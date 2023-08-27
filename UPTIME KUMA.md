
# How To Run Kuma Uptime Robot Using PM2

[![](https://techviewleo.com/wp-content/uploads/2021/12/uptime-logo.png?ezimgfmt=rs:484x484/rscb7](https://techviewleo.com/wp-content/uploads/2021/12/uptime-logo.png)

In the [previous article](https://techviewleo.com/run-kuma-self-hosted-uptime-robot-in-docker-container/), we evaluated how to Install the Uptime Kuma monitoring tool using Docker and running a docker-compose YAML file. Please start with that article before proceeding to this one. Definitions & features and how to install Uptime Kuma on Ubuntu, Debian, and Fedora using Docker were covered with cool screenshots on dashboard configurations.

In this article, I will show you how to run Kuma Uptime Robot Using PM2. For those new to Node.JS world, PM2 is an advanced process manager for production Node.js applications. It is a complete daemon process manager designed to help you manage and keep your application online 24/7.

To carry out the steps below, ensure you have the following:

-   A Linux system
-   User with root privileges.
-   Use local volume as NFS is not supported.

The Non-Docker method of installation requires the following tools.

-   Node.js version 14 and above.
-   git
-   pm2

This method of installation is Not recommended for ARM CPU users. Let’s get started.

Update your packages cache index

```
## Debian based systems ##
sudo apt update -y 

## RHEL based systems ##
sudo yum -y makecache
```

## Step 1: Install Node.js and npm from a repository.

Once apt packages are updated install Node.js and npm in your system.

### 1.1 Install the **Node.js** environment

To install Node.js with all necessary dependencies:

```
## Debian based systems ##
cd
curl -sL https://deb.nodesource.com/setup_16.x | sudo bash -
sudo apt install node.js -y

## RHEL based systems ##
curl -sL https://rpm.nodesource.com/setup_16.x | sudo bash -
sudo yum install -y nodejs
```

Confirm installed version.

```
$ node -v
v16.13.1
```

### 1.2 Install Node.js using NVM

We will proceed to install and update the nvm. nvm is a version manager for Node.js

```
curl  -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

The script clones the nvm repository and sources it.

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Close and start your terminal to start using nvm.

List the available Node.js versions.

```
nvm list remote
```

Sample output :

```
 v16.10.0
       v16.11.0
       v16.11.1
       v16.12.0
       v16.13.0   (LTS: Gallium)
       v16.13.1   (Latest LTS: Gallium)
        v17.0.0
        v17.0.1
        v17.1.0
        v17.2.0
```

Let’s install v16.x.y using **nvm**. The article requires v14 and above.

```
nvm install v16
```

The output:

```
Downloading and installing node v16.13.1...
Downloading https://nodejs.org/dist/v16.13.1/node-v16.13.1-linux-x64.tar.xz...
######################################################################### 100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v16.13.1 (npm v8.1.4)
```

## Step 2: Git Install Version Control

Git is an open-source Distributed Version Control System.

```
## Debian based systems ##
sudo apt update
sudo apt install git

## RHEL based systems ##
sudo yum install -y git
```

### 2.1 : Clone Uptime Kuma

We will use the same image used in the previous article.

```
git clone https://github.com/louislam/uptime-kuma.git
```

Output:

```
Cloning into 'uptime-kuma'...
remote: Enumerating objects: 10799, done.
remote: Counting objects: 100% (10796/10796), done.
remote: Compressing objects: 100% (3148/3148), done.
remote: Total 10799 (delta 7836), reused 10342 (delta 7530), pack-reused 3
Receiving objects: 100% (10799/10799), 3.15 MiB | 6.23 MiB/s, done.
Resolving deltas: 100% (7836/7836), done.
```

Once you have cloned uptime-Kuma, cd to that directory.

```
cd uptime-kuma
```

### 2.2 Run setup

Run the uptime-Kuma setup with npm.

```
npm run setup
```

The output of the command:

```
> uptime-kuma@1.11.1 setup
> git checkout 1.11.1 && npm ci --production && npm run download-dist

Note: checking out '1.11.1'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 8bb8b0a update to 1.11.1
npm WARN deprecated core-js@2.6.12: core-js@<3.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Please, upgrade your dependencies to the actual version of core-js.

added 395 packages, and audited 396 packages in 9s

22 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

> uptime-kuma@1.11.1 download-dist
> node extra/download-dist.js

Downloading dist
https://github.com/louislam/uptime-kuma/releases/download/1.11.1/dist.tar.gz
https://objects.githubusercontent.com/github-production-release-asset-2e65be/382496361/d4c398e4-76af-42b1-8982-ccfc40cf616e?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20211209%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20211209T113445Z&X-Amz-Expires=300&X-Amz-Signature=dd0015972f6fed6d86ecf75434519b8ab18762ce625ca296eeb0ec5190ba7741&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=382496361&response-content-disposition=attachment%3B%20filename%3Ddist.tar.gz&response-content-type=application%2Foctet-stream
Extracting dist...
Done
npm notice 
npm notice New minor version of npm available! 8.1.4 -> 8.2.0
npm notice Changelog: https://github.com/npm/cli/releases/tag/v8.2.0
npm notice Run npm install -g npm@8.2.0 to update!  ## update to the latest version 
npm notice 
```

### 2.3 Test the success of installation

Test the success of uptime installation in your system by running the command:

```
node server/server.js
```

Sample output:

```
Welcome to Uptime Kuma
Node Env: production
Importing Node libraries
Importing 3rd-party libraries
Importing this project modules
Prepare Notification Providers
Version: 1.11.1
Creating express and socket.io instance
Server Type: HTTP
Data Dir: ./data/
Copying Database
Connecting to the Database
SQLite config:
[ { journal_mode: 'wal' } ]
[ { cache_size: -12000 } ]
SQLite Version: 3.36.0
Connected
Your database version: 0
Latest database version: 10
Database patch is needed
Backing up the database
```

## Step 3: Using PM2 to manage Kuma service

PM2 is a daemon process manager for managing and keeping your application online.

### 3.1 Install PM2

PM2 is installed in the system via NPM or Yarn.

To run the steps below, you must be inside your directory: i.e **Uptime-Kuma**

```
npm install pm2@latest -g
## OR ##
yarn global add pm2
```

This command installs the latest version of pm2.

### 3.2 Start Uptime Kuma Server

Run this command inside your directory.

```
pm2 start server/server.js --name uptime-kuma
```

The output:

```
[PM2] Starting /home/jil/uptime-kuma/server/server.js in fork_mode (1 instance)
[PM2] Done.
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ uptime-kuma        │ fork     │ 0    │ online    │ 0%       │ 31.8mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

### 3.3 Useful commands

Run these commands to start, stop and restart Uptime Kuma.

```
pm2 start uptime-kuma
pm2 stop uptime-kuma
pm2 restart uptime-kuma
```

To Start Uptime Kuma :

```
pm2 start uptime-kuma
```

The Output:

```
pm2 start uptime-kuma
[PM2] Applying action restartProcessId on app [uptime-kuma](ids: [ 0 ])
[PM2] [uptime-kuma](0) ✓
[PM2] Process successfully started
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ uptime-kuma        │ fork     │ 1    │ online    │ 0%       │ 18.0mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

To Stop Uptime Kuma

```
pm2 stop uptime-kuma
```

The output:

```
[PM2] Applying action stopProcessId on app [uptime-kuma](ids: [ 0 ])
[PM2] [uptime-kuma](0) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ uptime-kuma        │ fork     │ 1    │ stopped   │ 0%       │ 0b       │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

To Restart Uptime Kuma

```
pm2 restart uptime-kuma
```

The output:

```
Use --update-env to update environment variables
[PM2] Applying action restartProcessId on app [uptime-kuma](ids: [ 0 ])
[PM2] [uptime-kuma](0) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ uptime-kuma        │ fork     │ 1    │ online    │ 0%       │ 17.9mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

To update environment variables:

```
pm2 restart uptime-kuma --update-env
```

The output:

```
[PM2] Applying action restartProcessId on app [uptime-kuma](ids: [ 0 ])
[PM2] [uptime-kuma](0) ✓
┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
│ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
│ 0  │ uptime-kuma        │ fork     │ 2    │ online    │ 0%       │ 18.8mb   │
└────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

## Step 4: Testing on the web browser interface.

For this article, I used my Ubuntu 18.04 which runs on IP Address 192.168.201.8. To access the Uptime Kuma interface on the web browser, type this address on your URL: **http://<YOUR_IP_ADDRESS>:3001** i.e http://192.168.201.8:3001

This takes me to this page:

![](https://techviewleo.com/wp-content/uploads/2021/12/uptime-kuma-landing-page.png?ezimgfmt=rs:484x296/rscb7/ng:webp/ngcb7)

Uptime-Kuma-Login-Page

Congratulations, you have successfully set up Uptime Kuma using non-docker i.e PM2. We hope you have enjoyed the article. In our earlier article on using docker, we did a test using the techviewleo website. Kindly refer to the article.

Well, that’s about it. If you like what we are doing, make that comment at the bottom of the article. We would like to hear from you and how we can improve to make our articles more helpful. We are eternally grateful for your continued support. That coffee motivates us to keep going.