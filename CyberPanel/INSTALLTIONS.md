
# 01 - Installing CyberPanel

### Requirements

-   Server with a fresh install of Centos 7.x, Centos 8.x, Ubuntu 18.04, Ubuntu 20.04, AlmaLinux 8
-   Python 3.x
-   1024MB RAM, or higher
-   10GB Disk Space

### CyberPanel vs CyberPanel Ent
CyberPanel is 100% identical in both versions. The only difference is which web server is running in the back-end.

1.  **CyberPanel** comes with _OpenLiteSpeed_ and is completely free for an unlimited number of domains and worker processes.
2.  **CyberPanel Ent** comes with _LiteSpeed Web Server Enterprise_ and it is free for 1 domain. If you need more than 1 domain, you can view our pricing page. The CyberPanel license **includes** the price of your LiteSpeed Enterprise license.

To learn more about the differences between OpenLiteSpeed and LiteSpeed Web Server Enterprise, please see this.

---

### Installing CyberPanel

#### Step 1: Connect to your server via SSH

The installation of CyberPanel is quite simple. First, log into your server via SSH as the _**root**_ user (sudo will not work). You can get the login details from your web host.

#### Step 2: Update packages

For Ubuntu: `sudo apt update && sudo apt upgrade -y`  
For CentOS/Alma/Rocky:

```sql
sudo yum check-update
sudo yum update
```

#### [](https://community.cyberpanel.net/docs?category=9&tags=install%7Cupgrade&topic=82#step-2-run-the-installation-script-6)Step 2: Run the installation script

Run the following command. It will initiate the automated installation script, which will prompt you for a few decisions about which version of LiteSpeed and which add-ons you would like to install.

`sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)`

If, for some reason, you are not able to log in as `root`, you can use this command

`sudo su - -c "sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)"`

#### Step 3: Select the version of LiteSpeed that you would like to use

Select which version of LiteSpeed to install. If you select LiteSpeed Enterprise, please ensure that you have obtained a license key first. It is free for 1 domain, but you still need to obtain the key. Visit the pricing table to decide your desired plan.

```sql
CyberPanel Installer v2.1.2

RAM check : 184/981MB (18.76%)

Disk check : 7/30GB (27%) (Minimal 10GB free space)

1. Install CyberPanel with OpenLiteSpeed.

2. Install Cyberpanel with LiteSpeed Enterprise.

3. Exit.


  Please enter the number[1-3]:
```

If you selected LiteSpeed Enterprise, you will see the following prompt. Enter your serial number

`If you do not have any license, you can also use trial license (if server has not used trial license before), type TRIAL`

Please input your serial number for LiteSpeed WebServer Enterprise:

#### Step 4: Select options and add-ons

You will be presented with a series of prompts for different options and add-ons that are available.

**Full Service (default Y):**

-   PowerDNS- an open-source DNS server
-   Postfix - open-source mail transfer agent
-   Pure-FTPd - open-source FTP server

**Remote MySQL (default N):**

-   Allow for your Database to be installed on a remote server

**CyberPanel Version (default Latest Version):**

-   You can choose to install a previous version of CyberPanel, or press Enter to install the latest

**Password (default “1234567”):**

-   It is recommended that you use “s” to set your own strong password

**Memcached(default Y):**

-   Distributed memory object caching system

**Redis (default Y):**

-   In-memory data structure store, used as a database, cache, and message broke

**Watchdog (default Yes):**

-   Kernel watchdog is used to monitor if a system is running. It is supposed to automatically reboot hanged systems due to unrecoverable software errors

#### Step 5: Installation

The installation process will proceed automatically. It will take 5-10 minutes, depending on the speed of your server.

#### Step 6: Finalize Installation

At the end of the installation process, you will be presented with the following screen which contains important information about your configuation. Select and copy it to a safe location for future reference.

```yaml
###################################################################
                CyberPanel Successfully Installed

                Current Disk usage : 7/30GB (26%)

                Current RAM  usage : 313/981MB (31.91%)

                Installation time  : 0 hrs 11 min 0 sec

                Visit: https://<your server's IP address>:8090
                Panel username: admin
                Panel password: <the password you set during installation>
                Visit: <your server's IP address>:7080
                WebAdmin console username: admin
                WebAdmin console password: TSXMwny4zVeDg37K

                Visit: https://<your server's IP address>:8090/rainloop/?admin
                Rainloop Admin username: admin
                Rainloop Admin password: gQKFWm9O3nr7Xn

             Run cyberpanel help to get FAQ info
             Run cyberpanel upgrade to upgrade it to latest version.
             Run cyberpanel utility to access some handy tools .

              Website : https://www.cyberpanel.net
              Forums  : https://forums.cyberpanel.net
              Wikipage: https://docs.cyberpanel.net
              Docs    : https://cyberpanel.net/docs/

            Enjoy your accelerated Internet by
                CyberPanel & OpenLiteSpeed
###################################################################
If your provider has a network-level firewall
Please make sure you have opened following port for both in/out:
TCP: 8090 for CyberPanel
TCP: 80, TCP: 443 and UDP: 443 for webserver
TCP: 21 and TCP: 40110-40210 for FTP
TCP: 25, TCP: 587, TCP: 465, TCP: 110, TCP: 143 and TCP: 993 for mail service
TCP: 53 and UDP: 53 for DNS service
Your provider seems blocked port 25 , E-mail sending may not work properly.
```

#### Step 7: Restart Server

`Would you like to restart your server now? [y/N]:`

Enter “y” to restart. Or enter “reboot” later after you have performed other desired operations.

#### Step 8: Access CyberPanel

After the successful installation you can access CyberPanel using the details below (make sure to change):

```makefile
URL: https://<Your Server's IP Address>:8090 
Username: admin
Password: <the password you set during installation>
```

---

### Troubleshooting

#### 503 Error After Install

If you get a 503 error after installing CyberPanel, you can do one of the following things.

**1. Check LSCPD Status.**

`systemctl status lscpd`

If LSCPD is not running, start LSCPD using:

`systemctl start lscpd`

**2. Manually set up virtualevn**

```bash
source /usr/local/CyberCP/bin/activate
pip install --ignore-installed -r /usr/local/CyberCP/requirments.txt
deactivate
virtualenv --system-site-packages /usr/local/CyberCP
systemctl restart lscpd
```

**3.** **Install Logs**

If you are still having issues after these steps, you can try to find errors in the install logs, they are located at:

`/var/log/installLogs.txt`

**4. Submit Bug Report**

If all of the above failed, please submit a .