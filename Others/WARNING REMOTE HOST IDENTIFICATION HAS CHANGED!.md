# This can also be used if we have not done KEY BASH AUTHENCATION.

----------------------------------------------------------------------------
## WARNING REMOTE HOST IDENTIFICATION HAS CHANGED! 

Shows this mesage.


```bash
###Dvs:~ dvs$ ssh ubuntu@192.168.1.8

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!

Someone could be eavesdropping on you right now (man-in-the-middle attack)!

It is also possible that a host key has just been changed.

The fingerprint for the ECDSA key sent by the remote host is

SHA256:nDfJF8pK2PAx6F/LMqbuUw8bge6Q6q8hQVHZPg/MQyM.

Please contact your system administrator.

Add correct host key in /Users/dvs/.ssh/known_hosts to get rid of this message.

Offending ECDSA key in /Users/dvs/.ssh/known_hosts:1

ECDSA host key for 192.168.1.8 has changed and you have requested strict checking.

Host key verification failed.
```

----------------------------------------------------------------------------

### 1. Windows
It’s important to note that Windows machines might not have a **known_hosts** file. However, if you use the Open SSH client there _is_ a file. To find it, open the Windows search bar, and navigate to your user folder with the **%USERPROFILE%** command.

This will open the directory within the **File Explorer**. There will also be a **.ssh** folder within:

![The Windows File Explorer.](https://kinsta.com/wp-content/uploads/2021/08/file-explorer.png)

The file we want in this folder is **known_hosts**. You can open this with Notepad (or your [favorite text editor](https://kinsta.com/blog/best-text-editors/)). Inside will be a list of keys:

![The Windows known_hosts file.](https://kinsta.com/wp-content/uploads/2021/08/windows-known-hosts.png)

Here, you can delete the key that’s causing the problem, then resave the file.

Some users may prefer the Putty Client . The keys sit in the Registry, although they perform the same purpose as OpenSSH.

You’ll want to open the Windows Registry Editor (otherwise known as “regedit”). You can do this in whatever way you’re comfortable, but the quickest way is to type the app’s name into Window’s search bar:

![The Registry Editor link in the Windows Start menu.](https://kinsta.com/wp-content/uploads/2021/08/regedit.png)

The Registry Editor link in the Windows Start menu.

Here, look for the following destination within **regedit**:

```bash
HKEY_CURRENT_USER/Software/SimonTatham/PuTTY/SshHostKeys/
```

You’ll see a list of entries here relating to the saved connections on your computer. Your job is to delete whichever one is causing an issue:

![Deleting a Registry key in regedit.](https://kinsta.com/wp-content/uploads/2021/08/regedit-host-keys-putty.png)

Deleting a Registry key in regedit.

Once you click on the **Delete** button, you’ll also need to confirm that you want to remove the key:

![The Confirm Value Delete dialog.](https://kinsta.com/wp-content/uploads/2021/08/putty-confirm.png)

The Confirm Value Delete dialog.

Clicking **Yes** here means the key will be gone for good, and you shouldn’t get the “Warning: Remote host identification has changed” error any longer.


### 2. Mac

The Mac has a couple of ways to fix the “Warning: Remote host identification has changed” error — either through a premium app such as SSH Config Editor or the Terminal. The results will be the same, so we advise you to choose whichever option is more comfortable (and budget-friendly).

Our preferred approach is to access the file within a Terminal window (or iTerm2) if you use that app), and also open it with a dedicated Nano or Vim editor. This is because it’s accessible to everyone and straightforward to use regardless of your experience level.

Here, we’re going to use Nano. First, open your Terminal using whatever process is most comfortable:

![Opening the Terminal from Spotlight.](https://kinsta.com/wp-content/uploads/2021/08/spotlight-terminal.png)

Opening the Terminal from Spotlight.

From here, run the  command in your window. This will open a new Nano instance and display the keys within your **known_hosts** file:

```bash
nano ~/.ssh/known_hosts
```


![The Nano editor with the known_hosts file open.](https://kinsta.com/wp-content/uploads/2021/08/nano-known-hosts.png)

The Nano editor with the known_hosts file open.

You should delete the key causing the “Warning: Remote host identification has changed” error, then save your changes.

You might also want to delete the entire **known_hosts** file, especially if you only use SSH for one or two sites. To do this, you can run `rm .ssh/known_hosts` in a Terminal window.

There’s one more method to alter the **known_hosts** file on Mac: using the **ssh-keygen** utility from the command line. This is great if you don’t want to dig into the file itself, or if you want to work with only one site or key.

To achieve this, open a Terminal window and run `ssh-keygen`, followed by your server hostname. For example:

```bash
ssh-keygen -R server.example.com
```

This won’t ask you if you want to delete the specified lines, so make sure you’re removing the right ones before proceeding:

![Using ssh-keygen to delete from the known_hosts file.](https://kinsta.com/wp-content/uploads/2021/08/ssh-keygen-delete.png)

Using ssh-keygen to delete from the known_hosts file.

Once this is done, you shouldn’t get the “Warning: Remote host identification has changed” error from there on out.

----------------------------------------------------------------------------

# IF YOU HAVE DONE KEY BASH AUTHENCATION THEN FOLLOW STEPS.

2. MAC

Open Finder and and on top  you See Go option in menu bar. click and scroll down and  click on go to folder and type this path.

```BASH
~/.ssh/known_hosts/
```
![[Screen Shot 2022-09-26 at 10.54.43 PM.png]]

and this Folder will open. You can see the knows_hosts files opon that knows_hosts file and you will the key specified with IP Address. 

![[Screen Shot 2022-09-26 at 10.54.25 PM.png]]

Just change IP with you want to SSH and now you can do this. Error has just been solved.
-----------------------------------------------------------------------------------------