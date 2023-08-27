- ### GIT
	- Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
	- Git is easy to learn and has a tiny footprint with lightning fast performance.  It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching convenient staging areas, and multiple workflows.
	- Git is free and open source nad thats the main reson we everyone is use GIT instead of GITHUB.

- #### GITHUB

	- GitHub is a cloud-based hosting service that lets you manage Git repositories. If you have open-source projects that use Git, then GitHub is designed to help you better manage them.
	- We can also use GITHUB to push and pull our Repositor.  But that repository is public in GITHUB and anyone can use our code. so that is why GITHUB is a paid service if we want to use as a private server we cant use.

- #### How GIT Works
 
 ![[Screen Shot 2022-10-03 at 9.51.57 AM.png]]

GIT is working on this model. as we can see in this diagram

- ### How to Downloads git in Linux 

```bash
sudo apt-get install git
```

- After downloading Git into our system. 
- First Step is to add a Folder in Git repositary. we can chech is our repository is git repositary or not
```bash
Dvs:~ dvs$ git status
fatal: not a git repository (or any of the parent directories): .git
```

- we can also check which version of GIT is this. By using this command
```bash
git --version
git version 2.17.2 (Apple Git-113)
```
- and we can see this repository is fatel not a GIT repository.
- so now can add this repository in GIT as a GIT repository by adding this command.(git init)

```bash
git init
Reinitialized existing Git repository in /Users/dvs/divyesh-sops/.git/
```
- now our repository is GIT repository
```bash
Dvs:divyesh-sops dvs$ git status

On branch master
Your branch is up to date with 'origin/master'.
nothing to commit, working tree clean
```
- Now we add files into our GIT repository after adding files into repository
```bash
Dvs:divyesh-sops dvs$ ls

2022-10-01.md
Allow Port (22 & 443 and 80) Port in Firewall & Change PHP Memory Limit.pdf
Allow Port 22 - 443 and 80 Port in Firewall & Change PHP Memory Limit.md
DNS (DomainNaming System) and its Records.md
Deploy WordPress Server On Ubuntu Server.pdf
```
- after adding files into our repository. we will use git add stage our repository. like we are put our code in staging before add this into final step.
- and we can use this by adding this command- 
````bash
Dvs:Obsidians dvs$ git add .
````
- and after our repository into staging area. we can save this by adding "commit" and name that it so we can use this future if we want 
```bah
Dvs:divyesh-sops dvs$ git commit -m "Add Screen_Shot"

On branch master
Your branch is up to date with 'origin/master'.
nothing to commit, working tree clean
```

- and now we can see this is master branch and and git has commit those changes and and save as a name call "Add Screen_Shot"
- we can add our name in to our Repositoy 
```bash
git config   global user.name "Divyesh Tailor"
```
and can also add our email into our repository
```bash
git config   global user.email "divyeshtailor012@gmail.com"
```
- and we have add global into our user name. so GIt create a repository and name it as "Divyesh Tailor".
- and after our code is ready into our repository. we can push our code to git server by using this command called "git push" 

```bash
git push
```
- this means. we have push our code from staging area to Final stage. means our new version has been applyed to server. and old version is removed

