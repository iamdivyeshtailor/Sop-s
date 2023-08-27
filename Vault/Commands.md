1. Sync Ultra.cc to Qnap NAS
```SHELL
[/share/Backups]$ rsync -aHAXxv --numeric-ids --progress --bwlimit=20000 usb244@arcturus.usbx.me:/home/usb244/Backups/ /share/Backups/ultra.cc
```

