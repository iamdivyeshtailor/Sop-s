### How to Backup & Restore Of GITLAB SERVER

 So first SSH to Gitlab server 
```bash
ssh root@192.168.1.11
```

then go to /etc/gitlab
- Before restoring the backup copy, first make sure backup copy is in the _/var/opt/gitlab/backups_ directory.
- and take a backup of this gitlab file because all file are in this folder.
- You can check the backup copy by using the _ls -l_ command which is described in the Create Backup.
- Now first , stop the processes which are related to the database by using the below commands
```bash
sudo gitlab-ctl stop unicorn

sudo gitlab-ctl stop sidekiq
```
- The above commands can also be used to free up some memory temporarily by shutting down them.
- You can verify status of the GitLab services by using the below command 
```bash
sudo gitlab-ctl status
```
 - Now, restore the backup by using the timestamp of the backup copy 
 ```bash
 sudo gitlab-rake gitlab:backup:restore BACKUP = 1521884424_2018_03_24_10.5.3
```
 - Restart the GitLab components by using the below command 
```bash
sudo gitlab-ctl restart
```
 - Now check the GitLab by sanitizing the database as shown below
```bash
sudo gitlab-rake gitlab:check SANITIZE = true
```

- The _SANITIZE = true_ flag removes all email addresses because they are confidential, removes the CI variables and access tokens as they can be used in the production instance.