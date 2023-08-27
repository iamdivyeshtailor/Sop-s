1. Create a sudo user:
```Shell
root@moros:~# adduser user_name
```

2. Change Password for new server:
```Shell
root@moros:~# passwd user_name
```

3. Add User to SUDO Group (Debian/Ubuntu):
```Shell
root@moros:~# usermod -aG sudo kd-admin
```

3. Add User to SUDO Group (Fedora/RHEL/CentOS):
```Shell
root@moros:~# usermod -aG wheel kd-admin
```

4. Add your key to Your User's authorized_key File:
```Shell
root@moros:~# usermod -aG wheel kd-admin
```

5. Edit Following Options in sshd_Config
```Shell
root@moros:~# sudo nano /etc/ssh/sshd_config
```
```
# Logging
SyslogFacility AUTH
LogLevel INFO

#PermitRootLogin yes
```

6. Restart SSH Server:
```Shell
root@moros:~# sudo systemctl restart sshd.service
```
