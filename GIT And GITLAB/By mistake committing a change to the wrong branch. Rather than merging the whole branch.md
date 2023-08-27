
### By mistake committing a change to the wrong branch. Rather than merging the whole branch

## Git Cherrypick

`Git cherry-pick` is designed to pick a commit from a branch and apply it to another branch. This could happen when a user makes a mistake by committing a change to the wrong branch. Rather than **merging** the whole branch, you can cherry-pick. This command is also useful for team collaboration. Different teams may need a commit. `Git Cherry-pick` helps with that.
-   First, ensure that you are in the branch you want to be in.
``` 
git checkout <branch_name>
```
-   Cherry-pick the commit using the commit hash
```
git cherry-pick <commit_id>
```
- The **commit ID** is the _commit hash key_. It can be gotten when you run `git log`.
```
git cherry-pick df2a446bd3742c530f2bc6eac2b6b38c99a697d8
```

```
git cherry-pick --edit <Hash>
```

- This command lets you edit a commit message before committing.
```
git cherry-pick --no-commit <Hash>
```

Rather than creating a new commit, it carries over the commit message from your branch to your working directory.

## Git Clean

`Git Clean` operates on or cleans the working repository by removing **untracked files**. For clarity, _untracked files_ are files in your repository working directory that haven’t been staged or added to the version control using the popular command `git add`. Just running `git clean` will most likely throw an error because the command needs to be passed along with an option.
```
git clean -n
```
This command tells you what file would be removed without actually removing them. This is most definitely a good practice. It makes you quite sure about what files are going to be removed.
```
git clean -f or --force
```
This command deletes an untracked file from the working directory. This doesn’t remove untracked folders or **.gitignore** files. A file path can also be passed along `git clean -f`.
```
git clean -dn
git clean -df
```
By passing the -d option, it removes untracked directories. By default, `git clean` does not remove untracked directories, just untracked files.
```
git clean -xn
git clean -x
```
This command forces the removal of ignored files. It is best practice to check what files would be removed by doing a dry run first.
![2-xn clean.png](https://blog.openreplay.com/images/top-dozen-advanced-git-commands-to-know/images/image02.png)

For more on Git clean, click [here](https://www.git-scm.com/docs/git-clean)

## Git Commit

`Git commit` takes and records staged changes(changes that have been added) made to a project. This change becomes the most recent commit in the local repository. Changes are staged using the `git add .` command. Also, note that using `git commit` does not automatically save to the remote server. It only saves in the local Git repository.
```
git commit
```
This command launches an editor prompting for a commit message. After saving and exiting, it creates a commit message.
```
git commit -a
```
This command includes all changes to tracked files. It does not include untracked, those that haven’t been added using `Git add .` files.
```
git commit -m "commit message"
```

![3 commit_message](https://blog.openreplay.com/images/top-dozen-advanced-git-commands-to-know/images/image03.jpg)

This command creates a commit along with a commit message passed. Accurate commit messages help to clarify the changes made to a repository. So teammates can understand what changes were pushed because of the right name given. This command sets the commit message here rather than launching the editor.
```
git commit -am "commit message"
```
This command combines the `-a` and the `-m` options to commit changes. This creates a commit for all staged changes and adds a commit message. This omits the `git add .` step.
```
git commit --amend
```
This command modifies the previous commit. Rather than creating a new commit, current staged changes will be added to the previous commit. This command opens up the editor and prompts you to change the previous commit that is already there.

## Git Config

This command allows you to change and set Git configuration values and settings globally or locally(in a specific git repository), depending on which you prefer. `Git config` may seem like a beginner command, but there is no end to what you can do with it.

Globally, Git configuration is stored in the _.gitconfig_ file.
```
el@el-HP-EliteBook:~$ cat .gitconfig
[user]
              email = <your_email>
              name = <your_name>
```
This file shows the configuration already in place globally. It can be more, not just email and name.
```
git config user.name
```
This shows the user’s name.
Locally, the config file is stored in your repository’s _.git_ folder.

![4 config_file](https://blog.openreplay.com/images/top-dozen-advanced-git-commands-to-know/images/image04.png)

The configuration file includes some information, like the URL of the repo and the branch.

N.B Global level uses `--global` flag, local(specific git repository) level uses `--local` flag
```
git config --global user.name <your_name>
```
This command writes the value `<your_name>` to the configuration `user.name`. Since it’s using the `--global` flag, it sets the value for the current operating system user. This username will be the commit author that will show up in your commits.
```
git config --global user.email <your_email>
```

### Git Config Editor

As an engineer, when any command sends me to an editor I don’t fully understand, I get confused, and it takes time to adjust. This command allows us to choose an editor of our choice.

```
git config --global core.editor <editor>
```

```
git config --global core.editor "emacs"
```
The particular editor of your choice will always be opened when the git command is run. There are other editors from you to choose from.
```
git config -l or --list
```
This is a way to see if the changed or added settings are applied. The results would vary depending on whether you are in your local repo or you are global.

## Aliases

These are custom and temporary shortcuts that help increase efficiency. Again, this can be set globally or in your local repo.
```
git config --global alias.<what_you_want_to_set_the_command_to> <command>
```

```
git config --global alias.a add
```

So when next you want to add a file to the staging area, rather than using `git add .`, you can do `git a .`
```
git config --global alias.cm commit
git config --global alias.stat status
```
The `-unset` flag can be used to get rid of a setting.
```
git config --global --unset user.name
```
This removes the user name from the global config file.

—unset-all : removes multiple settings in the file

—remove-section: removes a particular section from the file

```
git config --global --remove-section "section"
```

![5 remove_section](https://blog.openreplay.com/images/top-dozen-advanced-git-commands-to-know/images/image05.png)

This command removes the user section from the configuration file.

END

### From Where I get this
URL: https://blog.openreplay.com/top-dozen-advanced-git-commands-to-know/