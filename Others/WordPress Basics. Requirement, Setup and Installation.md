### WordPress Basics. Requirement, Setup and Installation
- WordPress is one of the most popular content management systems (CMS) on the planet, with more than 42% of all websites on the internet powered by the platform
- DigitalOcean supports WordPress hosting on our virtual machine called  Droplets —and we’ve made installing WordPress on a Droplet extremely easy, so you get your website up and running confidently and quickly.
- Wordpress uses technologies like 
	- Linux 
	- Nginx  
	- PHP 
	- MySql 

### Basic requirements to install WordPress

 - Step 1:- Create a Virtual Machine
	- First you need a server to install and Host Wordpress site. so for that you need virtual machine or called Droplets 
	- so visit to the DigitalOcean Marketplace, and click **Create WordPress Droplet**. You’ll be taken to the “Create Droplets” page of your DigitalOcean account, where you can then:
	- Choose an image: “WordPress 5.8 on Ubuntu 20.04” should be automatically selected.
	- Choose a plan: Select the option that works best for you, but keep in mind that WordPress needs at least 1GB of RAM to run.
	-  Add SSD based Storage to expand storage capacity.
	- Choose the data center closest to your user base.
	- Select additional options like Monitoring—you can do so now or anytime in the future.   
	- Name your WordPress Droplet.

- Step 2: Access the Droplet via SSH to Enable Configuration
	- we just need a IP Address & Username and password to acces ther VM

```bash
ssh root@droplet.ip.address
```

### Where to Download WordPress

- Visit the WordPress.org official website. 
- Make sure to download the latest version and extract it from the ZIP file. 
- extract it to server directory


### Installation of WordPress

1. WordPress will first ask you to **select the language** for your site. Do so and press **Continue.**

[![The WordPress installation page featuring the language options.](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2021/11/wordpress-choose-language-1.png)]


2.  Fill in your website and administrator information:

-   Create a new Site Title for your WordPress site.
-   Set the WordPress Username, Password, and Your Email which will later be used to login to the WordPress Admin Dashboard.
-   We suggest only checking the box next to Search engine visibility if you don’t want the website to be visible on search engines.

Click the Install WordPress button to finalize the process.

[![The WordPress installation form](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2017/02/wordpress-website-installation-form.png)]

Then, fill in your login information and press the **Login** button to access WordPress Admin.

[![The WordPress login screen](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2017/02/wordpress-login-screen.png)]

Sometimes, WordPress might also ask to collect your MySQL details after selecting the language. Since you already have them, press Log in

- Enter your MySQL database credentials. Leave the Database Host and the Table Prefix fields as they are. Only change them if you wish to run multiple installations with one database. After filling in all the necessary information, click Submit.
- WordPress will check whether it’s possible to connect to the MySQL database you have created. If there are no errors, select Run the installation.

