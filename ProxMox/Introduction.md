### What is qemu guest agent

The qemu-guest-agent is a helper daemon, which is installed in the guest. It is used to exchange information between the host and guest, and to execute command in the guest.

In Proxmox VE, the qemu-guest-agent is used for mainly two things:

1.  To properly shutdown the guest, instead of relying on ACPI commands or windows policies
2.  To freeze the guest file system when making a backup (on windows, use the volume shadow copy service VSS).

## Installation

### Host

You have to install guest-agent in each VM and then enable it, you can do that in the Proxmox VE Webinterface (GUI)

[![QEMU Guest Agent Option](https://pve.proxmox.com/mediawiki/images/6/6d/Proxmox_VE_-_QEMU_Guest_Agent_Option.png)](https://pve.proxmox.com/wiki/File:Proxmox_VE_-_QEMU_Guest_Agent_Option.png "QEMU Guest Agent Option")

or via CLI: 

```cmd
qm set VMID --agent 1
```


```
### Guest

#### Linux

On Linux you have to simply install the qemu-guest-agent, please refer to the documentation of your system.

We show here the commands for Debian/Ubuntu and Redhat based systems:

on Debian/Ubuntu based systems (with apt-get) run:

```shell
apt-get install qemu-guest-agent
```

and on Redhat based systems (with yum):

```shell
yum install qemu-guest-agent
```

Depending on the distribution, the guest agent might not start automatically after the installation.

Start it either directly with

```shell
systemctl start qemu-guest-agent
```

(should work for most distributions) or reboot the guest.

#### Windows

[![Screen-vioserial-device-manager.png](https://pve.proxmox.com/mediawiki/images/thumb/3/3f/Screen-vioserial-device-manager.png/300px-Screen-vioserial-device-manager.png)](https://pve.proxmox.com/wiki/File:Screen-vioserial-device-manager.png)

[](https://pve.proxmox.com/wiki/File:Screen-vioserial-device-manager.png "Enlarge")

[![Screen-vioserial-driver.png](https://pve.proxmox.com/mediawiki/images/thumb/f/f3/Screen-vioserial-driver.png/300px-Screen-vioserial-driver.png)](https://pve.proxmox.com/wiki/File:Screen-vioserial-driver.png)

[](https://pve.proxmox.com/wiki/File:Screen-vioserial-driver.png "Enlarge")

First you have to download the virtio-win driver iso (see [Windows VirtIO Drivers](https://pve.proxmox.com/wiki/Windows_VirtIO_Drivers "Windows VirtIO Drivers")).

Then install the virtio-serial driver:

1.  Attach the ISO to your windows VM (virtio-*.iso)
2.  Go to the windows Device Manager
3.  Look for "PCI Simple Communications Controller"
4.  Right Click -> Update Driver and select on the mounted iso in DRIVE:\vioserial\<OSVERSION>\ where <OSVERSION> is your Windows Version (e.g. 2k12R2 for Windows 2012 R2)

After that, you have to install the qemu-guest-agent:

1.  Go to the mounted ISO in explorer
2.  The guest agent installer is in the directory **guest-agent**
3.  Execute the installer with double click (either **qemu-ga-x86_64.msi** (64-bit) or **qemu-ga-i386.msi** (32-bit)

After that the qemu-guest-agent should be up and running. You can validate this in the list of Window Services, or in a PowerShell with:

PS C:\Users\Administrator> Get-Service QEMU-GA

Status   Name               DisplayName
------   ----               -----------
Running  QEMU-GA            QEMU Guest Agent

If it is not running, you can use the **Services** control panel to start it and make sure that it will start automatically on the next boot.

### Testing that the communication with the guest agent is working

The communication with the guest agent takes place over a unix socket located in /var/run/qemu-server/<my_vmid>.qga You can test the communication qm agent:

`qm agent <vmid> ping`

if the qemu-guest-agent is correctly runnning in the VM, it will return without an error message.
