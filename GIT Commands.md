Tired of memorizing `git` commands? Here is a **cheat sheet** with **40+ commands** to simplify your life.

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#1-initialize-a-local-repository)1. Initialize a local repository

```
git init <directory>
```

The `<directory>` is optional. If you don't specify it, the **current directory** will be used.

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#2-clone-a-remote-repository)2. Clone a remote repository

```
git clone <url>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#3-add-a-file-to-the-staging-area)3. Add a file to the staging area

```
git add <file>
```

To add all files in the **current directory**, use `.` in place of `<file>`.  

```
git add .
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#4-commit-changes)4. Commit changes

```
git commit -m "<message>"
```

If you want to add all changes made to **tracked files** & **commit**  

```
git commit -a -m "<message>"

# or

git commit -am "<message>"
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#5-remove-a-file-from-the-staging-area)5. Remove a file from the staging area

```
git reset <file>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#6-move-or-rename-a-file)6. Move or rename a file

```
git mv <current path> <new path>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#7-remove-a-file-from-the-repository)7. Remove a file from the repository

```
git rm <file>
```

You can also remove it from **staging area** only using `--cached` flag  

```
git rm --cached <file>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#basic-git-concepts)Basic Git Concepts

1.  Default **branch** name: `main`
2.  Default **remote** name: `origin`
3.  Current **branch** reference: `HEAD`
4.  Parent of `HEAD`: `HEAD^` or `HEAD~1`
5.  Grandparent of `HEAD`: `HEAD^^` or `HEAD~2`

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#13-display-branches)13. Display branches

```
git branch
```

Useful **flags**:

-   `-a`: Display all **branches** (local & remote)
-   `-r`: Display **remote branches**
-   `-v`: Display **branches** with last **commit**

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#14-create-a-branch)14. Create a branch

```
git branch <branch>
```

You can create a **branch** and switch to it using the `checkout` command.  

```
git checkout -b <branch>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#15-switch-to-a-branch)15. Switch to a branch

```
git checkout <branch>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#16-delete-a-branch)16. Delete a branch

```
git branch -d <branch>
```

You can also force delete a **branch** using the `-D` flag.  

```
git branch -D <branch>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#17-merge-a-branch)17. Merge a branch

```
git merge <branch to merge into HEAD>
```

Useful **flags**:

-   `--no-ff`: Create a **merge commit** even if the merge resolves as a **fast-forward**
-   `--squash`: Squash all **commits** from the specified **branch** into a single **commit**

### [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#fast-forward%C2%A0merge)Fast forward Merge

[![Fast-forward-merge](https://res.cloudinary.com/practicaldev/image/fetch/s--aJqyDJ6J--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/42ni8mpxvszgy8lv7ps3.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--aJqyDJ6J--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/42ni8mpxvszgy8lv7ps3.png)

### [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#nonfast-forward%C2%A0merge)Non-Fast forward Merge

[![No-fast-forward-merge](https://res.cloudinary.com/practicaldev/image/fetch/s--27hsl6SY--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/m0anmpky6p73loegkgac.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--27hsl6SY--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/m0anmpky6p73loegkgac.png)

It is suggested to not use the `--squash` **flag** as it will squash all **commits** into a single **commit**, leading to a **messy commit history**.

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#18-rebase-a-branch)18. Rebase a branch

**Rebasing** is the process of moving or combining a sequence of **commits** to a new base **commit**

[![Rebase](https://res.cloudinary.com/practicaldev/image/fetch/s--LaqH_xzc--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wmhc1lvw6pvjgisaodi3.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--LaqH_xzc--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wmhc1lvw6pvjgisaodi3.png)  

```
git rebase <branch to rebase from>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#19-checkout-a-previous-commit)19. Checkout a previous commit

```
git checkout <commit id>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#20-revert-a-commit)20. Revert a commit

```
git revert <commit id>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#21-reset-a-commit)21. Reset a commit

```
git reset <commit id>
```

You can also add the `--hard` flag to delete all changes, but use it with caution.  

```
git reset --hard <commit id>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#22-check-out-the-status-of-the-repository)22. Check out the status of the repository

```
git status
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#23-display-the-commit-history)23. Display the commit history

```
git log
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#24-display-the-changes-to-unstaged-files)24. Display the changes to unstaged files

```
git diff
```

You can also use the `--staged` flag to display the changes to **staged** files.  

```
git diff --staged
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#25-display-the-changes-between-two-commits)25. Display the changes between two commits

```
git diff <commit id 01> <commit id 02>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#26-stash-changes)26. Stash changes

The **stash** allows you to temporarily store changes without **committing** them.  

```
git stash
```

You can also add a message to the **stash**.  

```
git stash save "<message>"
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#27-list-stashes)27. List stashes

```
git stash list
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#28-apply-a-stash)28. Apply a stash

Applying the **stash** will **NOT** remove it from the **stash list**.  

```
git stash apply <stash id>
```

If you do not specify the `<stash id>`, the latest **stash** will be applied (Valid for all similar **stash** commands)

You can also use the format `stash@{<index>}` to apply a **stash** (Valid for all similar **stash** commands)  

```
git stash apply stash@{0}
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#29-remove-a-stash)29. Remove a stash

```
git stash drop <stash id>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#30-remove-all-stashes)30. Remove all stashes

```
git stash clear
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#31-apply-and-remove-a-stash)31. Apply and remove a stash

```
git stash pop <stash id>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#32-display-the-changes-in-a-stash)32. Display the changes in a stash

```
git stash show <stash id>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#33-add-a-remote-repository)33. Add a remote repository

```
git remote add <remote name> <url>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#34-display-remote-repositories)34. Display remote repositories

```
git remote
```

Add a `-v` flag to display the **URLs** of the remote **repositories**.  

```
git remote -v
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#35-remove-a-remote-repository)35. Remove a remote repository

```
git remote remove <remote name>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#36-rename-a-remote-repository)36 Rename a remote repository

```
git remote rename <old name> <new name>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#37-fetch-changes-from-a-remote-repository)37. Fetch changes from a remote repository

```
git fetch <remote name>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#38-fetch-changes-from-a-particular-branch)38. Fetch changes from a particular branch

```
git fetch <remote name> <branch>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#39-pull-changes-from-a-remote-repository)39. Pull changes from a remote repository

```
git pull <remote name> <branch>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#40-push-changes-to-a-remote-repository)40. Push changes to a remote repository

```
git push <remote name>
```

## [](https://dev.to/ruppysuppy/git-cheat-sheet-with-40-commands-concepts-1m26#41-push-changes-to-a-particular-branch)41. Push changes to a particular branch

```
git push <remote name> <branch>
```