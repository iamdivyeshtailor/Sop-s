- ### How to add SWAP RAM (MEMORY) Swap Space on Ubuntu

	- Swap is a space on a disk that is used when the amount of physical RAM memory is full. When a Linux system runs out of RAM, inactive pages are moved from the RAM to the swap space.
	- Swap space can take the form of either a dedicated swap partition or a swap file. Generally when running Ubuntu on a virtual machine, a swap partition is not present, and the only option is to create a swap file.

- ### How to Check We have alredy Add Swap Or Not  
	- Before Adding SWAP check if your Linux System has  already add swap or not by Typing
	```bash
	sudo swapon --show
	```
	 - If the output is empty, it means that your system does not have swap space enabled.
	- Otherwise, if you get something like below, you already have swap enabled on your machine.
	```bash
	sudo swapon --show

	NAME      TYPE SIZE USED PRIO
	/swapfile file   4G   0B   -2
	```
	- as you can see the size is 4G means Swap memory  is 4GB. 
	- and if you alredy have the SWAP memory. First you have to check the available space in your HARDDISK.
	- And if you dont have more memory  then you have to remove the already Addes SWAP memory then you can used it.

- ### How to Creating a Swap File 
	- Start by creating a file which will be used for swap:  
	```bash
	sudo fallocate -l 1G /swapfile
	```
	- If fallocate is not installed or you get an error message saying fallocate failed: Operation not supported then use the following command to create the swap file:
```bash
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```

- then only Only the root user should be able to write and read the swap file. Set the correct by typing:
```bash
sudo chmod 600 /swapfile
```
- Use the mkswap utility to set up a Linux swap area on the file:
- this will create a swap bu typing mkswap
```bash
sudo mkswap /swapfile
```
- Now we need to Activate the Swap. whick we had created
- Activate the swap file using the following command:
```bash
sudo swapon /swapfile
```

- To make the change permanent open the `/etc/fstab` file:
```bash
sudo nano /etc/fstab
```
and paste the following line 
```bash
/swapfile swap swap defaults 0 0
```
- Verify that the swap is active by using either the swapon or the free command, as shown below:
```bash
sudo swapon --show
```

```bash
NAME      TYPE SIZE USED PRIO
/swapfile file   4G 512K   -2
```
- we can also use this command 

```bash
sudo free -h
```

```bash
              total        used        free      shared  buff/cache   available

Mem:          976Mi       761Mi        70Mi        30Mi       144Mi        53Mi

Swap:         4.0Gi       3.0Mi       4.0Gi
```


and you can also see by typing htop in terminal.
![[Screen Shot 2022-10-04 at 10.40.02 PM.png]]

- ### Adjusting the Swappiness Value

	- Swappiness is a Linux kernel property that defines how often the system will use the swap space. Swappiness can have a value between 0 and 100. A low value will make the kernel to try to avoid swapping whenever possible, while a higher value will make the kernel to use the swap space more aggressively.
	- The default swappiness value is 60. You can check the current swappiness value by typing the following command:
```bash
cat /proc/sys/vm/swappiness
```

```bash
output
60
```
- While the swappiness value of 60 is OK for most Linux systems, for production servers, you may need to set a lower value.
- For example, to set the swappiness value to 10, run:
 ```bash
 sudo sysctl vm.swappiness=10
```
- To make this parameter persistent across reboots, append the following line to the /etc/sysctl.conf file:
```bash
vm.swappiness=10
```
- The optimal swappiness value depends on your system workload and how the memory is being used. You should adjust this parameter in small increments to find an optimal value.

- # Removing a Swap File

	- To deactivate and remove the swap file, follow these steps:
	- Start by deactivating the swap space by typing:
```bash
sudo swapoff -v /swapfile
```

- Next, remove the swap file entry /swapfile swap swap defaults 0 0 from the /etc/fstab file.
- Finally, remove the actual swapfile file using the command:
```bash
sudo rm /swapfile
```

From Where Did I Learn it. 
LINK "https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-18-04/