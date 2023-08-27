#### Migrate Development Site: simiandtemi.webcase.me to new cyberpanel server

### Requirements
Wp-admin page Credentials
cyber panel Credentials with both old and new server

- Easy Step
	- -->Take Back up of old wordpress site
	- -->Create a New Site using Cyber panel 
	- --> then add Ip and DNS in your local Computer (Throught which you can access new site)
	- --> open 

- #### First visit to admin pags of wordpress : 

	- Enter username  and password 
	- Eg: (https://simiandtemi.webcase.me/wp-admin/users.php)
	- ![[Screen Shot 2022-09-30 at 10.20.29 AM.png]]
	- and on left side. we see a menu bar with all the option we want in worpress. now find plugins options and move your curser into plugings option.
	- ![[Screen Shot 2022-09-30 at 11.00.59 AM.png]]
	- open plugins option. you will see all the plugin. available fot wordpress
	- now search for all in one worpress migration and install it
	- ![[Screen Shot 2022-09-30 at 11.02.51 AM.png]]
	- now on left side of menu bar we see a new option name (all in one wp migration). like this we can download plugin
	- click all in one wp migration and you see export import and backup option over here to back up your site
	- click on export 
	- ![[Screen Shot 2022-09-30 at 11.05.28 AM.png]]
	
	- ![[Screen Shot 2022-09-30 at 11.05.36 AM.png]]
	- ![[Screen Shot 2022-09-30 at 11.05.39 AM.png]]
	and you can download back up.
	- some time .so it may fail because of large size. so simply that means the back is already present. in backup section just next to export section.

- ### Now create a new Site where you want to migrate
	- So create a new site website secition in menu bar of cyber panel. --> and click create new webite
	- Fill all the details and tick mark on open basedir protection
	- ![[Screen Shot 2022-09-30 at 11.54.24 AM.png]]
	- now new site has been created and 
	- ![[Screen Shot 2022-09-30 at 11.54.40 AM.png]]
	- so now add this IP and DNS in your computer host file in /etc/hosts file
	- and then open this dns in any browser
	- you will see a cyberpanel is installed page
		now come back to cyber panel and visit to the webite section -> and open list webiste 
	- ![[Screen Shot 2022-09-30 at 1.02.40 PM.png]]
	- ![[Screen Shot 2022-09-30 at 1.00.29 PM.png]]
	- ![[Screen Shot 2022-09-30 at 1.00.31 PM.png]]
	- now on the right side. you will a manage open. click on it
	- and scroll down to the botton we will see a wordpess option just install it.
	- ![[Screen Shot 2022-09-30 at 1.03.58 PM.png]]
-  now open new tab and typer the dns and last type /wp-admin

- so the wordpress page will open 
	- so first thing to do is to install all in one wordpress plugin by 
	visiting to plugin page.
	- now create FTP  to upload a worpress file 
		- so visit to cyber panel and create a FTP account 
		- upload it by using filezilla just add all the credentials whick we have add  at a time of creating FTP  
		- select that file and upload in a wp-cli--> public_html--> wp-content--> ai1wm-backups 
		- and upload that file here.
		- ![[Screen Shot 2022-09-30 at 1.25.26 PM.png]]
		- ones the upload is we can see the name of that file 
		- 	![[Screen Shot 2022-09-30 at 1.23.52 PM.png]]


- go to the wp admin page. simiandtemi.webcase.me/wp-admin
- and go to all in one wp migration --> and then in Back up --> and restore 

- Now go to Cyber panel and install SSL
 - Go SSL section and click on manage SSL

- ![[Screen Shot 2022-09-30 at 2.34.48 PM.png]]
 - Select the Site to which you want to assign SSL
 - ![[Screen Shot 2022-09-30 at 2.33.54 PM.png]]
- and click on Issue SSL
- ![[Screen Shot 2022-09-30 at 2.36.41 PM.png]]
- SSL has been Done
- now go to wp-admin page and setting -> general -> site-url= https:.//simiandtimi.webcase.me
- and do same for home url
- done

Now log out to admin page

### END







