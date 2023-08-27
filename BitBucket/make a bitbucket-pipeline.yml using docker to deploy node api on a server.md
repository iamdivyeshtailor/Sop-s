Sure! I can help you create a Bitbucket Pipeline configuration file (`bitbucket-pipelines.yml`) to deploy a Node.js API using Docker. Here's an example configuration:

```bash
# bitbucket-pipelines.yml

pipelines:
  default:
    - step:
        name: Build and Deploy
        image: node:14
        caches:
          - node
        script:
          # Install dependencies
          - npm ci

          # Build the project
          - npm run build

          # Build Docker image
          - docker build -t my-api-image .

          # Log in to Docker registry (if necessary)
          - docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD

          # Push Docker image to registry
          - docker push my-api-image

          # SSH into the server and deploy the Docker image
          - ssh $SSH_USER@$SSH_HOST 'docker stop my-api-container || true'
          - ssh $SSH_USER@$SSH_HOST 'docker rm my-api-container || true'
          - ssh $SSH_USER@$SSH_HOST 'docker pull my-api-image'
          - ssh $SSH_USER@$SSH_HOST 'docker run -d --name my-api-container -p 3000:3000 my-api-image'
```

In this example, we assume that you have already set up SSH access to the server where you want to deploy your Node.js API. Make sure to replace the placeholders with your actual values:

- `$DOCKER_USERNAME` and `$DOCKER_PASSWORD`: Your Docker registry credentials, if applicable.
- `$SSH_USER` and `$SSH_HOST`: SSH username and hostname of your server.

Here's a breakdown of the steps performed in the pipeline:

1. The pipeline uses the official Node.js 14 Docker image.
2. The `npm ci` command installs the project dependencies based on the `package-lock.json` file.
3. The `npm run build` command builds your Node.js API (replace with your actual build script if necessary).
4. The `docker build` command builds a Docker image for your API using the current directory (`.`) as the build context.
5. If you need to authenticate with a Docker registry, the `docker login` command allows you to log in with your credentials.
6. The `docker push` command pushes the Docker image to the registry.
7. The subsequent SSH commands stop any existing container, remove it, pull the new Docker image, and run a new container with the updated image.

Remember to adjust the Dockerfile, build script, and deployment steps as per your project's requirements.
