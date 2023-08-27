### Introduction

A “LAMP” stack is a group of open source software that is typically installed together in order to enable a server to host dynamic websites and web apps written in PHP. This term is an acronym which represents the **L**inux operating system with the **A**pache web server. The site data is stored in a **M**ySQL database, and dynamic content is processed by **P**HP.

## Step 1 — Installing Apache and Updating the Firewall
The Apache web server is among the most popular web servers in the world. It’s well documented, has an active community of users, and has been in wide use for much of the history of the web, which makes it a great choice for hosting a website.

Start by updating the package manager cache. If this is the first time you’re using `sudo` within this session, you’ll be prompted to provide your user’s password to confirm you have the right privileges to manage system packages with `apt`:

``` bash
sudo apt update
```
Then, install Apache with:

```
sudo apt install apache2
```

You’ll be prompted to confirm Apache’s installation. Confirm by pressing `Y`, then `ENTER`.

Once the installation is finished, you’ll need to adjust your firewall settings to allow HTTP traffic. Ubuntu’s default firewall configuration tool is called Uncomplicated Firewall (UFW). It has different application profiles that you can leverage. To list all currently available UFW application profiles, execute this command:
```bash
sudo ufw app list
```

```
Output
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
```
Here’s what each of these profiles mean:

-   **Apache**: This profile opens only port `80` (normal, unencrypted web traffic).
-   **Apache Full**: This profile opens both port `80` (normal, unencrypted web traffic) and port `443` (TLS/SSL encrypted traffic).
-   **Apache Secure**: This profile opens only port `443` (TLS/SSL encrypted traffic).
- For now, it’s best to allow only connections on port `80`, since this is a fresh Apache installation and you don’t yet have a TLS/SSL certificate configured to allow for HTTPS traffic on your server.

To only allow traffic on port `80`, use the `Apache` profile:

```
sudo ufw allow in "Apache"
```

Verify the change with:

```
sudo ufw status
```

```
OutputStatus: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                                
Apache                     ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)                    
Apache (v6)                ALLOW       Anywhere (v6)     

```

Traffic on port `80` is now allowed through the firewall.

You can do a spot check right away to verify that everything went as planned by visiting your server’s public IP address in your web browser (view the note under the next heading to find out what your public IP address is if you do not have this information already):

```
http://your_server_ip
```

The default Ubuntu 22.04 Apache web page is there for informational and testing purposes. Below is an example of the Apache default web page:

![Ubuntu 22.04 Apache default web page with an overview of your default configuration settings](https://assets.digitalocean.com/articles/LampStack-2204-apache-landing)

If you can view this page, your web server is correctly installed and accessible through your firewall.

### How To Find your Server’s Public IP Address

If you do not know what your server’s public IP address is, there are a number of ways to find it. Usually, this is the address you use to connect to your server through SSH.

There are a few different ways to do this from the command line. First, you could use the `iproute2` tools to get your IP address by typing this:

```
ip addr show ens3 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'
```

This will give you two or three lines back. They are all correct addresses, but your computer may only be able to use one of them, so feel free to try each one.

An alternative method is to use the `curl` utility to contact an outside party to tell you how it sees your server. This is done by asking a specific server what your IP address is:

```
curl http://icanhazip.com
```

Whichever method you choose, type in your IP address into your web browser to verify that your server is running.

## Step 2 — Installing MySQL

Now that you have a web server up and running, you need to install the database system to be able to store and manage data for your site. MySQL is a popular database management system used within PHP environments.

Again, use `apt` to acquire and install this software:

```
sudo apt install mysql-server
```

When prompted, confirm installation by typing `Y`, and then `ENTER`.

When the installation is finished, it’s recommended that you run a security script that comes pre-installed with MySQL. This script will remove some insecure default settings and lock down access to your database system. Start the interactive script by running:

```
sudo mysql_secure_installation
```

This will ask if you want to configure the `VALIDATE PASSWORD PLUGIN`.

Answer `Y` for yes, or anything else to continue without enabling.
