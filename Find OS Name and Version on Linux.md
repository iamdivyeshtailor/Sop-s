
#### Linux/Unix

The procedure to find os name and version on Linux:

1.  Open the terminal application (bash shell)
2.  For remote server login using the ssh: **ssh user@server-name**
3.  Type any one of the following command to find os name and version in Linux:  
```
cat /etc/os-release
```

```
lsb_release -a
```

```
hostnamectl
```

4.  Type the following command to find Linux kernel version:  
```
uname -r
```
 
 Output: 
```
NAME="Ubuntu"
VERSION="17.10 (Artful Aardvark)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 17.10"
VERSION_ID="17.10"
HOME_URL="[https://www.ubuntu.com/](https://www.ubuntu.com/)"
SUPPORT_URL="[https://help.ubuntu.com/](https://help.ubuntu.com/)"
BUG_REPORT_URL="[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)"
PRIVACY_POLICY_URL="[https://www.ubuntu.com/legal/terms-and-policies/privacy-policy](https://www.ubuntu.com/legal/terms-and-policies/privacy-policy)"
VERSION_CODENAME=artful
UBUNTU_CODENAME=artful
```