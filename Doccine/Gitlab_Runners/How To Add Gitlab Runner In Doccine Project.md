- First Register a runner using this command
```bash
sudo gitlab-runner register
```
- then add usermod
```bash
sudo usermod -aG docker gitlab-runner
```
- then change user
```bash
sudo su gitlab-runner
```

- now you can add Register a Runner
```bash
sudo gitlab-runner register
```

``` Output
Runtime platform                                    
arch=amd64 os=linux pid=27520 
revision=0d4137b8 version=15.5.0
Running in system-mode.`
```
- Then Enter your Gitlab Runner URL
```
Enter the GitLab instance URL (for example, https://gitlab.com/):
```
- Type URL
```bash
https://gitlab.webcase.me
```
- Then Enter the registration token:
```bash
Enter the registration token:
```
- Type Token
```bash
3-WatNGyHzkBiDoKdhbk
```
- Now Add a Description for that 
```
Enter a description for the runner:
```
- Description Like
```bash
Dvs_Shello
```
- and then add a tags for your Runners
```bash
Enter tags for the runner (comma-separated):
```
- add tags
```
shell,deploy,deployer
```

- #### Where you can find this Registration Token
	- Login
	- Then go to Admin Panel
	- and then go to runner section from left side of side bar
	- Go to https://gitlab.webcase.me
	- and one the right side you can see "Register an instances runner" Expand it and you will get the token.
	- ![[Pasted image 20221102174250.png]]

- #### Where you can find this tags
	-  Login
	- Then go to Admin Panel
	- and then go to runner section from left side of side bar
	- Go to https://gitlab.webcase.me
	- ![[Pasted image 20221102173620.png]]
	- Login
	- Then go to Admin Panel
	- and then go to runner section from left side of side bar
	- ![[Pasted image 20221102173809.png]]
	- and from here you can get the tags. 
	- Done

Now just Refresh the webpage and you can see the runners has been added