
### FTP Commands

## What is FTP?

FTP is a network protocol used for exchanging files over the network. It uses port 21. FTP enables you to access a remote system for exchanging files using the ftp command.

- ### FTP Syntax
	- FTP syntax is as below:

```bash
ftp host or Ip address
```
- Here, host can either be the hostname or IP address of the remote host.
- FTP commands are similar to Linux commands. We'll discuss some of these.

- COMMAND and its USAGE

	- open --> Opens a remote connection with another computer.
	- get --> Copies a file from the remote system to the local system.
	- put --> Copies a file from the local system to a directory on the remote system.
	- mget --> Transfers multiple files from the remote system to the local system’s current directory.
	- mput --> Transfers multiple files from the local system to a directory on the remote system.
	- bye/quit --> Prepares to exit the FTP environment.
	- close --> Terminates the FTP connection.
	- ascii --> Enables file transfer mode to ASCII
	- binary --> Enables file transfer mode to binary.
