### NAME: Kamaldhari Infotech
### Project: Doccine
### Front End: Doccine

stages:
  - Test
  - Build
  - Package
  - Deploy


### Branch = Develop ###
 
dev-api_deploy:
  stage: Deploy
  environment:
    name: Development
    url: http://dev.doccine.webcase.me/
  before_script:
    - echo "$Dev_Deploy_Known_Host" > ~/.ssh/known_hosts
    - chmod 644 ~/.ssh/known_hosts
  script:
    - ssh doccine-dev@localhost "bash update-frontend.sh"
  tags:
    - shell
    - dev-deploy
  only:
    - Develop


### Branch = Staging ###

## Build
build-staging:
  image: jainil00/reactbuilder:testing
  tags:
    - react
  environment:
    name: staging
  variables:
    CI: 'false'
  stage: Build
  artifacts:
    untracked: false
    expire_in: 2 days
    paths:
    - build
  before_script:
    - npm install -g yarn  
    - yarn install 2> >(grep -v warning 1>&2)
  script:
    - echo $CI_PROJECT_TITLE
    - npx browserslist@latest --update-db
    - export NODE_OPTIONS=--max_old_space_size=4096
    - echo REACT_APP_SERVICE_URL=$DEV_REACT_APP_SERVICE_URL >> .env
    - echo REACT_APP_URL=$DEV_REACT_APP_URL >> .env
    - echo REACT_APP_DATABASE_TYPE=$DEV_REACT_APP_DATABASE_TYPE >> .env
    - echo REACT_APP_S3_BUCKET = $DEV_REACT_APP_S3_BUCKET >> .env
    - echo REACT_APP_S3_URL = $DEV_REACT_APP_S3_URL >> .env
    - echo PORT=$DEV_PORT=$DEV_PORT >> .env
    - echo REACT_APP_FB_APP_ID=$REACT_APP_FB_APP_ID >> .env
    - echo REACT_APP_FB_PAGE_ID=$REACT_APP_FB_PAGE_ID >> .env
    - echo REACT_APP_MODE=STAGING >> .env
    - echo REACT_APP_UPLOAD_REPORT_SIZE=$REACT_APP_UPLOAD_REPORT_SIZE >> .env
    - yarn build
  only:
    - Staging

### Explain= `Build Job` 

``` shell
npm install -g yarn  
```
- The command `npm install -g yarn` installs the package manager `yarn` globally on your system using the package manager `npm`. The `-g` flag stands for global and it is used to install the package globally, so it can be run from anywhere on your system. This means that you can run yarn commands from any directory, rather than just within a specific project folder.
``` shell
yarn install 2> >(grep -v warning 1>&2)
```
- This command installs packages specified in a `yarn.lock` or `package.json` file using the `yarn` package manager. The `2> >(grep -v warning 1>&2)` part of the command is redirecting the stderr stream (`2`) to a process created by `grep -v warning`. The `grep -v` tells `grep` to invert the match, so it shows all lines that do not match the string "warning". The `1>&2` at the end tells the shell to redirect the stdout stream to the same place as stderr, so the output from `grep` is sent to the same place as the original stderr output. The overall effect of this command is to install packages using `yarn`, and hide any warnings that are normally displayed during the installation process.



## Package
package-staging:
  tags:
   - shell
  stage: Package
  environment:
    name: staging
  dependencies:
    - build-staging
  before_script:
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER $CI_REGISTRY --password-stdin
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_ENVIRONMENT_NAME -t $CI_REGISTRY_IMAGE:$CI_COMMIT_BRANCH -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA .
    - docker push $CI_REGISTRY_IMAGE --all-tags
  only:
    - Staging

## Deploy
Depoly-Staging:
  stage: Deploy
  environment:
    name: staging
  dependencies:
    - package-staging  
  tags:
   - shell
  before_script:
   - 'command -v ssh-agent >/dev/null || ( apt-get update -y && apt-get install openssh-client -y )'
   - eval $(ssh-agent -s)
   - echo "$PRIVKEYAWS" | tr -d '\r' | ssh-add -
   - mkdir -p ~/.ssh
   - chmod 700 ~/.ssh
   - echo "$DEV_SSH_KNOWN_HOSTS" > ~/.ssh/known_hosts
   - chmod 644 ~/.ssh/known_hosts
  script:
    - ssh $DEV_SERVER_USER@$DEV_SERVER_IP "bash docker-update.sh $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA $CI_PROJECT_TITLE-$CI_ENVIRONMENT_NAME $DEV_SERVER_PORT 3301"
  when: on_success
  only:
    - Staging

### Branch = Production_beta ###

## Build
build-production-beta:
  image: jainil00/reactbuilder:testing
  tags:
    - react
  environment:
    name: Production
  variables:
    CI: 'false'
  stage: Build
  artifacts:
    untracked: false
    expire_in: 14 days
    paths:
    - build
  before_script:
    - npm install -g yarn  
    - yarn install 2> >(grep -v warning 1>&2)
  script:
    - npx browserslist@latest --update-db
    - export NODE_OPTIONS=--max_old_space_size=4096
    - echo REACT_APP_SERVICE_URL=$PROD_REACT_APP_SERVICE_URL >> .env
    - echo REACT_APP_URL=$PROD_REACT_APP_URL >> .env
    - echo REACT_APP_DATABASE_TYPE=$PROD_REACT_APP_DATABASE_TYPE >> .env
    - echo REACT_APP_S3_BUCKET = $PROD_REACT_APP_S3_BUCKET >> .env
    - echo REACT_APP_S3_URL = $PROD_REACT_APP_S3_URL >> .env
    - echo PORT=$PROD_PORT >> .env
    - echo REACT_APP_FB_APP_ID=$REACT_APP_FB_APP_ID >> .env
    - echo REACT_APP_FB_PAGE_ID=$REACT_APP_FB_PAGE_ID >> .env
    - echo REACT_APP_MODE=$PROD_REACT_APP_MODE >> .env
    - echo REACT_APP_UPLOAD_REPORT_SIZE=$REACT_APP_UPLOAD_REPORT_SIZE >> .env
    - yarn build
  only:
    - Production-Beta

## Package and upload to Local Registry
package-production-beta-gitlab-registry:
  tags:
   - shell
  stage: Package
  environment:
    name: Production
  dependencies:
    - build-production-beta
  before_script:
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER $CI_REGISTRY --password-stdin
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_ENVIRONMENT_NAME -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    - docker push $CI_REGISTRY_IMAGE --all-tags
  only:
    - Production-Beta

## Package and upload to Docker Hub
package-production-beta-docker-hub:
  tags:
   - shell
  stage: Package
  variables: 
    CI_REGISTRY_USER: $Docker_Hub_User_Name
    CI_REGISTRY_PASSWORD: $Docker_Hub_PAT_Token
    CI_REGISTRY: docker.io
    CI_REGISTRY_IMAGE: index.docker.io/doccine/frontend 
  environment:
    name: Production
  dependencies:
    - build-production-beta
  before_script:
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER $CI_REGISTRY --password-stdin
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_ENVIRONMENT_NAME -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    - docker push $CI_REGISTRY_IMAGE --all-tags
  only:
    - Production-Beta


## Deploy
deploy-production-beta:
  stage: Deploy
  environment:
    name: Production
  tags:
   - shell
  before_script:
   - 'command -v ssh-agent >/dev/null || ( apt-get update -y && apt-get install openssh-client -y )'
   - eval $(ssh-agent -s)
   - echo "$PROD_SERVER_PRIV_KEY" | tr -d '\r' | ssh-add -
   - mkdir -p ~/.ssh
   - chmod 700 ~/.ssh
   - echo "$PROD_SSH_KNOWN_HOSTS" > ~/.ssh/known_hosts
   - chmod 644 ~/.ssh/known_hosts
  script:
   - ssh $PROD_SERVER_USER@$PROD_SERVER_IP "bash Deploy-Docker-Images.sh $CI_COMMIT_SHA $CI_PROJECT_TITLE-$CI_ENVIRONMENT_NAME-Beta $PROD_BETA_SERVER_DEPLOYMENT_PORT 3301 frontend"
  when: on_success
  only:
   - Production-Beta



### Branch = Production ###

## Build
build-production:
  image: jainil00/reactbuilder:testing
  tags:
    - react
  environment:
    name: Production
  variables:
    CI: 'false'
  stage: Build
  artifacts:
    untracked: false
    expire_in: 14 days
    paths:
    - build
  before_script:
    - npm install -g yarn  
    - yarn install 2> >(grep -v warning 1>&2)
  script:
    - npx browserslist@latest --update-db
    - export NODE_OPTIONS=--max_old_space_size=4096
    - echo REACT_APP_SERVICE_URL=$PROD_REACT_APP_SERVICE_URL >> .env
    - echo REACT_APP_URL=$PROD_REACT_APP_URL >> .env
    - echo REACT_APP_DATABASE_TYPE=$PROD_REACT_APP_DATABASE_TYPE >> .env
    - echo REACT_APP_S3_BUCKET = $PROD_REACT_APP_S3_BUCKET >> .env
    - echo REACT_APP_S3_URL = $PROD_REACT_APP_S3_URL >> .env
    - echo PORT=$PROD_PORT >> .env
    - echo REACT_APP_FB_APP_ID=$REACT_APP_FB_APP_ID >> .env
    - echo REACT_APP_FB_PAGE_ID=$REACT_APP_FB_PAGE_ID >> .env
    - echo REACT_APP_MODE=$PROD_REACT_APP_MODE >> .env
    - echo REACT_APP_UPLOAD_REPORT_SIZE=$REACT_APP_UPLOAD_REPORT_SIZE >> .env
    - yarn build
  only:
    - Production

## Package and upload to Local Registry
package-production-gitlab-registry:
  tags:
   - shell
  stage: Package
  environment:
    name: Production
  dependencies:
    - build-production
  before_script:
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER $CI_REGISTRY --password-stdin
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_ENVIRONMENT_NAME -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    - docker push $CI_REGISTRY_IMAGE --all-tags
  only:
    - Production

## Package and upload to Docker Hub
package-production-docker-hub:
  tags:
   - shell
  stage: Package
  variables: 
    CI_REGISTRY_USER: $Docker_Hub_User_Name
    CI_REGISTRY_PASSWORD: $Docker_Hub_PAT_Token
    CI_REGISTRY: docker.io
    CI_REGISTRY_IMAGE: index.docker.io/doccine/frontend 
  environment:
    name: Production
  dependencies:
    - build-production
  before_script:
    - echo $CI_REGISTRY_PASSWORD | docker login -u $CI_REGISTRY_USER $CI_REGISTRY --password-stdin
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_ENVIRONMENT_NAME -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    - docker push $CI_REGISTRY_IMAGE --all-tags
  only:
    - Production

## Deploy
deploy-production:
  stage: Deploy
  environment:
    name: Production
  tags:
   - shell
  before_script:
   - 'command -v ssh-agent >/dev/null || ( apt-get update -y && apt-get install openssh-client -y )'
   - eval $(ssh-agent -s)
   - echo "$PROD_SERVER_PRIV_KEY" | tr -d '\r' | ssh-add -
   - mkdir -p ~/.ssh
   - chmod 700 ~/.ssh
   - echo "$PROD_SSH_KNOWN_HOSTS" > ~/.ssh/known_hosts
   - chmod 644 ~/.ssh/known_hosts
  script:
   - ssh $PROD_SERVER_USER@$PROD_SERVER_IP "bash Deploy-Docker-Images.sh $CI_COMMIT_SHA $CI_PROJECT_TITLE-$CI_ENVIRONMENT_NAME $PROD_SERVER_DEPLOYMENT_PORT 3301 frontend"
  when: on_success
  only:
   - Production
