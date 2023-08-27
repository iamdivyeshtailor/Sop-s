Go to git site and download for your device

![[Pasted image 20221207171703.png]]
then login with this command
so you connect with your repo
![[Pasted image 20221207171802.png]]
```
git config --global user.name "username"
```

```
git config --global user.email "username@email.com"
```

after that verify this using this command
```
git config --list
```

- then go to the folder where your source code or your code is 
- and open with git (as shown in below image)
![[Pasted image 20221207172137.png]]

- Basic Commands
```
git verison
git init
git status
git add .
git commit -m "commit-message"
git push
```
- to check which branch is this
```
git branch
```
output
![[Pasted image 20221207172612.png]]
- If you want to check your previous commit. use this command 
```
git log
```

![[Pasted image 20221207172836.png]]
to check the different betwen old code and new code
```
git diff
```
### If your code is not not running and want to go back to your previous code
![[Pasted image 20221207175305.png]]
```
git checkout `filename`
```
- so now the file have go back to the previous version and the diffected code is remove from the new file 
![[Pasted image 20221207174845.png]]

### To create a new Branch. use this comamnd
```
git branch `branch-name`
```

then switch to that branch
```
git checkout `branch`
```

### If by mistake you add your file to staging area. 
```
git restore --staged filename
```
![[Pasted image 20221207174339.png]]
- and then check again using `git status`
