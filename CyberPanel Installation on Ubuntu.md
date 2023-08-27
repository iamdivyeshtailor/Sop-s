- CYBERPANEL is a free and open source website control panel and management system that acts as a management backend for your website. It is a very useful tool especially if you have deployed a website on a custom VPC / INSTANCE on common cloud platforms such as AMAZON WEB SERVICES,DIGITAL OCEAN, MICROSOFT AZURE or ORACLE CLOUD that allows you to have features and function that you normally would have on a CPANEL web hosting account. CyberPanel itself is free, you can install CyberPanel with OpenLiteSpeed and deploy unlimited super fast websites. As CyberPanel is Free and Open-source, you can install it a thousand times and there is no limits on number of installations nor number of websites in the Free Forever Plan. You can also monitor your CPU, Memory and Disk Usage right from your Dashboard restart system services and even install SSL Certificates by Let’s Encrypt with autorenewal of certificates enabled by default.

## REQUIREMENTS

1) A cloud hosted or on premise / on device linux ubuntu server 20.04 LTS virtual machine  
2) An AWS free tier account  
3) An SSH client such as PUTTY or the MacOS / Linux terminal  
4) The cyberpanel installation files for Linux Ubuntu  
5) A web browser such as Google Chrome , Firefox, Safari , Internet Explorer 

## OVERVIEW

1) CYBERPANEL system requirements  
2) Open AWS LIGHTSAIL and create a new LINUX UBUNTU instance (if you intend to deploy in the cloud)  
3) Connect to the instance via SSH then download and install UBUNTU updates  
4) Install CYBERPANEL  
5) Allow CYBERPANEL ports 443, 8090 and 7080 and log into the WEB dashboard.

## CYBERPANEL SYSTEM REQUIREMENTS

The following are the minimu system requiremtns that are needed to run CYBERPANEL successfully of a LINUX ubuntu virtual machine:  
1) LINUX UBUNTU 16.04 LTS or any newer version  
2) Python 3.x or newer and OPENLITESPEED  
3) 1GB of RAM though 4GB is recommended  
4) A dual core processor  
5) 10GB of disk space  
6) A FQDN domain name pointing to the CYBERPANEL server (in production deployments)

## STEP 1: OPEN AWS LIGHTSAIL AND CREATE A NEW LINUX UBUNTU INSTANCE (IF YOU INTEND TO DEPLOY IN THE CLOUD)

1) Click [HERE](https://aws.amazon.com/) to log into your AWS CONSOLE, we recommend that you log in using your IAM user credentials and not your root user account. If you do not have an AWS account, click [HERE](https://aws.amazon.com/free) to sign up for a free tier account. 

NB: You also need to have a working VISA or MASTERCARD to be able to sign up for a FREE TIER account.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-1-768x600.png)

2) Once you have logged into your AWS account, use the search bar at the top of the page to search for LIGHTSAIL. Click on the AWS LIGHTSAIL search result to open the LIGHTSAIL MANAGEMENT console. In the console, click on the CREATE INSTANCE button.

On the SELECT A PLATFORM section, choose LINUX / UNIX and on the SELECT A BLUEPRINT section select UBUNTU 20.04 LTS.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-1-1.png)

3) On the CHOOSE YOUR INSTANCE PLAN section, select $5USD plan or the $10USD plan ( first three (3) months free) and scroll down to the IDENTIFY YOUR INSTANCE section.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-2.png)

4) Give the INSTANCE a descriptive name on the IDENTIFY YOUR INSTANCE input box and click on CREATE INSTANCE.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-3.png)

## STEP 2: CONNECT TO THE INSTANCE VIA SSH THEN DOWNLOAD AND INSTALL UBUNTU UPDATES

5) To connect to the instance via SSH first you have to download the KEY PAIR FILE. Click on HOME and click on the name of the INSTANCE that you have just created. On the CONNECT tab scroll down to the USE YOUR OWN SSH CLIENT section and click on DOWNLOAD KEY PAIR.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-4.png)

6) Open your terminal application if using LINUX or MACOS and change your working directory to the downloads folder. Run the following command to set the permissions on the key pair file to read only:

sudo chmod 400 key-pair-file-name.pem

If you do not do this any connection attemp that you make to the UBUNTU INSTANCE will be denied.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-5.png)

7) Next connect to the instance by running the following command:

ssh -i ‘key-pair-file-name’ ubuntu@ip-address-of-instance

You will see a message notifying you that “the authenticity of the instance cannot be established. Are you sure you want to continue connecting?” Type in the letter Y and press ENTER.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-6.png)

8) Once you have succeded connecting, run the following command to download and install UBUNTU updates:

sudo apt-get update && apt-get upgrade

Once the system package update process is complete, run the following command to restart the UBUNTU instance:

sudo reboot now

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-7.png)

## STEP 3: INSTALL CYBERPANEL

9) When the INSTANCE restarts, reconnect to the instance via SSH and run the following command to download the CYBERPANEL installation script:

sudo su –

wget -O installer.sh https://cyberpanel.net/install.sh

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-8.png)

10) Next, make the installer.sh script file executable by running the command

chmod +x installer.sh

Then kick start the CYBERPANEL installation by running the command:

sh installer.sh

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-9.png)

11) The CYBERPANEL installer will ask if youd like to INSTALL CYBERPANEL or EXIT out of the installer, Press 1 and press ENTER. 

You also need to choose of you would like to install CYBERPANEL with OPENLITESPEED or LITESPEED ENTERPRISE. Press 1 (openlitespeed)  and press ENTER.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-10.png)

12) The installer, will now ask if you would like to perform a full installation, Enter the letter Y and press ENTER. You will also be prompted if you would like to setup REMOTE MYSQL, Enter the letter N and press ENTER. 

The installer will also prompt you to set a password, enter the letter S and press ENTER then set your custom default password. Alternatively you can just press D and press ENTER to use the default password of 1234567

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-11.png)

13) Next, you will be prompted to install MEMCACHED process and its PHP extension, type on the letter Y and press ENTER. The installer will also prompt for confirmation to install REDIS process and its PHP extension as well as WATCHDOG, Type in the letter Y on each prompt and press ENTER.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-12.png)

## STEP 4: ALLOW CYBERPANEL PORTS 443, 8090, 7080 AND LOG INTO THE WEB DASHBOARD.

14) Go to the AWS LIGHTSAIL dashboard, click on the name of the instance and click on the NETWORKING tab. Scroll down to the IPv4 firewall and click on add rule. For the first rule select HTTPS and click on CREATE. Create a second rule, set the application to CUSTOM, set the port range to 8090 and click on CREATE. Create a third rule, set the application to CUSTOM, set the port to 7080 and click on CREATE.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-13.png)

15) Next, open up a new web browser tab and type in the IP address of the CYBERPANEL server in the address bar. Ensure that you append the port number 8090 at the end and press enter. The format of the address should be:

https://ip-address-of-cyberpanel-server:8090

If you get an error message informing you that “YOUR CONNECTION IS NOT PRIVATE” click on ADVANCED and click on PROCEED. This happens because CYBERPANEL uses a self signed SSL certificate.

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-14.png)

16) On the LOG IN page, use the username admin and the password 1234567 (if you used the default system password) and click on SIGN IN

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-15.png)

17) Once you log in, the CYBERPANEL home page will be displayed and list out all the functions that are available

![](https://billysoftacademy.com/wp-content/uploads/2022/04/BILLYSOFTACADEMY-16.png)