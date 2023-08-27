LEMP Stack (Linux Nginx Mysql Php)

- ## Requirements 
	- WordPress will need a web server, a database, and PHP in order to correctly function. Setting up a LEMP stack (Linux, Nginx, MySQL, and PHP) fulfills all of these requirements.

### Step 1 --> SSH to Linux Machine and Update the Sytem

- First SSH into your Linux machine 
-  Before we begin, let’s update and upgrade the system. Login as the root user to your system and update the system to update the repositories.
```bash
ssh root@159.89.160.233

apt-get update && apt-get upgrade -y 

```

### Step 2 --> Creating a MySQL Database and User for WordPress.

- FIrst Log in to Root User Because we can Create Database only by Root Permissions
-  Dont Forgot to put colon `;` at the end of mySQL 

```bash
sudo su 
```
- Then Install My SQL
```bash
sudo apt-get install mysql-server mysql-client
```
- then start SQL
```bash
sudo mysql
```

- If you have changed the authentication method to use a password for the MySQL root account, use the following command instead:
```bash
mysql -u root -p
```
- You will be prompted for the password you set for the MySQL root account.
- Once logged in, create a separate database that WordPress can control. You can call this whatever you would like, but we will be using wordpress in this guide to keep it simple. You can create a database for WordPress by entering:

- Create DATABASE: 
```bash
CREATE DATABASE 'Database_name';
```
- Now Create user
```bash
CREATE USER 'user_name';
```
- Grant all Permission to User
```bash
GRANT ALL ON wordpress.* TO 'wordpressuser_name'@'localhost';
```
- And Now Exit

### Step 3 —> Installing Additional PHP Extensions

- First Install PHP 
```bash
sudo apt install php7.4-fpm
```
- Insert MySql Extension in Php
```bash
sudo apt install php7.4-mysql
```
- restart php 
```bash
sudo systemctl restart php7.4-fpm
```

### Step 4 —> Install And Configuring Nginx

- Install Nginx 

```bash
sudo apt-get install nginx
```

- Now create file to configure nginx in /etc/nginx/sites-available/

```bash
/etc/nginx/sites-available/
```

- and then configuration create file in this folder /etc/nginx/sites-available/

```bash
sudo nano webcase.me.conf
```

- Add  this in config script
```conf
server {
        listen 80;
        server_name webcase.me;
        root /var/www/wordpress;
        index index.php index.html index.htm;

        location / {
                try_files $uri $uri/ /index.php$is_args$args;
        }

  
        location ~ \.php$ {
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
            fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
            fastcgi_index index.php;
            include fastcgi.conf;
        }

         access_log /var/log/nginx/dvis_wp-access.log;
         error_log /var/log/nginx/dvis_wp-error.log;
}
```

- Now we need to enable the newly created nginx configuration. For that we need to create a symbolic in /etc/nginx/sites-enabled/ using this command

```BASH
root@divs-:$ ln -s /etc/nginx/sites-available/webcase.me.conf /etc/nginx/sites-enabled/webcase.me.conf
```
- Once Linked we need to check the nginx Configuration if its valid or not using folowing command.
```BASH
root@divs-:$ sudo nginx -t
```
- Now Restart the website
```BASH
root@divs-:$ sudo systemctl restart nginx.service
```

### Step 5 —> Downloading WordPress

-  Download wordpress 
```bash
wget https://wordpress.org/latest.tar.gz
```
- Now Uncompress
```
tar -xvf latest.tar.gz
```
- change ownership of ‘wordpress’ directory.
```
chown -R www-data:www-data wordpress/
```
- now check the permision
```bash
ls -lah
```

- Open your browser and go to the server’s URL. In my case it’s
```
https://server-ip/wordpress

```

### Step 6 —> Completing the Installation Through the Web Interface.

- Now we will get wordpress interface on browser
![[database-connection-details.png]]

![[alright-sparky-run-the-installation.png]]
- If all the details are correct, you will be given the green light to proceed. Run the installation.

![[welcome-more-information-needed.png]]
- Fill out the additional details required such as site title, Username, and Password and save them somewhere safe lest you forget. Ensure to use a strong password.
- ![[welcome-more-information-needed 1.png]]
- Scroll down and Hit ‘Install WordPress’. If all went well, then you will get a ‘Success’ notification as shown.
- ![[Sucess.png]]

- ![[log-in-to-Wordpress.png]]


### Step 7--> After Create Site in worpress  Assign SSL Certificate Using Certbot.
- after create sit in worpress --> assign ssl certificate using certbot.
- we need to install 2 packages

--> certbot

```bash
sudo apt-get install certbot python3-certbot-nginx
```
- then
```bash
sudo certbot --nginx -d divs-wp.webcase.me
```
- then enter you email id
```bash
sudo certbot --nginx -d divs-wp.webcase.me

Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator nginx, Installer nginx
Enter email address (used for urgent renewal and security notices) (Enter 'c' to
cancel): divyesh.kamaldhari@gmail.com
```

