#!/bin/bash
#### Kamaldhari Infotech Nov 2021
#### CCPro Updater Script

```bash
export NODE_OPTIONS=--max-old-space-size=4086
```
code explanation  (By Default the side of the node is 2048. So by increase the size to 4086 ) 
- #### Pulling New Code
```bash
cd /root/ccpro/react/ccpro-v3-git/goodgrid-chat-web
git fetch
git stash
git clean -fd
```
- #### Check if any Commit hash is passed and use if Exists
```bash
if (( "$#" != 1 ))
then
    git checkout dev
    echo "No Argument Passed! Using Dev Branch"
else
    git checkout $1
    echo "Checking Commit $1 and building"
fi
git pull --rebase
echo "Waiting 5 Second before Building. Press CTRL + C to End Script."
sleep 5
```
- #### Build New
```bash
yarn install
```
- #### npx browserslist@latest --update-db
```bash
yarn build
```
- #### move to build to server
```bash
zip -r /root/ccpro-old-builds/ccpro-$(date +'%m-%d-%Y').zip /var/www/ccpro
```

``` syntax
zip(command) -r(option) /root/ccpro-old-builds/ccpro-$(date +'%m-%d-%Y').zip (destination) /var/www/ccpro(source)
```

```bash
rm -rf /var/www/ccpro
cp -r /root/ccpro/react/ccpro-v3-git/goodgrid-chat-web/dist /var/www/ccpro
```
- #### cleanup & restart
```bash
rm -rf /root/ccpro/react/ccpro-v3-git/goodgrid-chat-web/dist/
systemctl restart nginx
```
- #### Exiting
echo "Script ran Successfully! Exiting/......"
```bash
exit 0
```
