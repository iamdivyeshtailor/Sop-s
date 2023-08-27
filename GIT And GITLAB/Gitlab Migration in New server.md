Gitlab Migration in New server  

### 1. Update your current install
-   only backup & restore to from Gitlab running the same versions. To avoid having to find an older version for your new server, it makes this process smoother if your current version of Gitlab is up-to-date.
```bash
sudo apt update 
```
### 2. Setup a new Server
-   I was able to do this by replacing gitlab-ee in the documentation with gitlab-ce. For example, the Debian install requires a script which is then piped through bash - it can be updated to the following- 

```bash
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
```

-  Now We can install gitlab-ce in the next step

```bash
sudo EXTERNAL_URL="https://gitlab.example.com" apt-get install gitlab-ce
```
### 3. Create a backup
-   If you are up-to-date, you can use the following to make a backup. Run this on your exiting Gitlab server

```bash
sudo gitlab-backup create
```

-   You will see it loop through all of the projects on your Gitlab server and eventually create a tar file. This tar filename contains the date and the Gitlab version - so you can double check your versions are in sync.    
-   This file should be located in /var/opt/gitlab/backups/ (unless you have changed this yourself in the gitlab.rb file).

### 4. Transfer the files

-   The most straight-forward way of getting the backup to the new server is a direct scp or rsync. The backup file will be owned by root, so however you get this to the new server is down to you.
-   I added my personal SSH key from the original server to the target server, transferred the backup file to my home directory, chownd it to me and scpd it from there.    
-   Along with the tar, make sure you transfer the gitlab files in /etc/gitlab/ (e.g. /etc/gitlab/gitlab).

### 5. Move the files

-   Move the files you have just transferred to the places where you found them. The tar goes to /var/opt/gitlab/backups/ and the two gitlab files to /etc/gitlab/.
### 6. Restore the backup

-   The restoration is details in the [Gitlab documentation](https://docs.gitlab.com/ee/raketasks/backup_restore.html#restore-for-omnibus-gitlab-installations), however once you have stopped the services listed, you can run
```bash
sudo gitlab-backup restore
```    
-   This will restore the one and only backup that exists. If you do pass in the name of the file (if you, say, took a backup of the new server), you need to omit the _gitlab_backup.tar at the end of the name.

-   For example, if the file was 1612726810_2021_02_07_13.8.3_gitlab_backup.tar you would do:

```bash
sudo gitlab-backup restore BACKUP=1612726810_2021_02_07_13.8.3
```