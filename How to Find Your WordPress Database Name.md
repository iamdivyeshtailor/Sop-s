
- Using hPanel’s File Manage
- Using an FTP Client
- Finding the WordPress Database Name
- Login to sever. where the site is hosted

### Using hPanel’s File Manager
- [![wp-config.php file on the File Manager](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2016/08/wp-config-file-manager.png)](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2016/08/wp-config-file-manager.png)

After opening the file manager in your panel, you will see several directories and files. The location of **wp-config.php** entirely depends on where you have installed WordPress. However, in the hPanel, the installation path is typically /**public_html/wp-config.php**.

### Using an FTP Client

- After configuring FileZilla, connect by accessing **File** -> **Site Manager.** After successfully logging into your FTP account, you will see your hosting’s primary directory on the right side of the screen. If you didn’t install WordPress in a subfolder, the **wp-config.php** file should be there.

[![The wp-config.php file on FileZilla](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2016/08/wp-config-ftp.png)](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2016/08/wp-config-ftp.png)

## Finding the WordPress Database Name

- To open and inspect your **wp-config.php** file, you need to right-click on it and select **edit** or **view**. This action works similarly on both the FTP client and File Manager.
- Once inside, navigate to the value called **DB_NAME**. The string of numbers or letters after it is the WordPress database name.
- [![The database name on the wp-config.php file](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2016/08/wp-config-file.png)](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2016/08/wp-config-file.png)
- If you can’t find the value or want to locate it faster, you may use the **Ctrl+F** combination on Windows or **CMD+F** on Mac. Similarly, you can check other database details there as well by looking up the

	- DB_HOST, 
	- DB_USER
	 , or 
	- DB_PASSWORD

- values since they all represent your WordPress database details.