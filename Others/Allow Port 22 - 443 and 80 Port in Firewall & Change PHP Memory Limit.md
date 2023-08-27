### Allow 80 & 443 and 22 Port in Firewall

- By Defaut Firewall is Disable in Linux
- Allow Port no 80 443 and 22. one by one
```bash
sudo ufw allow 22
sudo ufw allow 80
sudo ufw allow 443
```
- Output
```
root@DIVS-BLR1-DEV:~# sudo ufw allow 22
Rules updated
Rules updated (v6)
root@DIVS-BLR1-DEV:~# sudo ufw allow 80
Rules updated
Rules updated (v6)
root@DIVS-BLR1-DEV:~# sudo ufw allow 443
Rules updated
Rules updated (v6)
```
- Then enable firewall
```bash
sudo ufw enable
```
- and then we can see in status
```bash
sudo ufw status 
```
- Output
```
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere                  
80                         ALLOW       Anywhere                  
443                        ALLOW       Anywhere                  
22 (v6)                    ALLOW       Anywhere (v6)             
80 (v6)                    ALLOW       Anywhere (v6)             
443 (v6)                   ALLOW       Anywhere (v6)
```

### Change PHP Memory Limit

- First go into a php folder
```bash
cd /etc/php/7.4/
```
- Then you can the fpm folder
```bash
/etc/php/7.4# ls

apache2  cli  fpm  mods-available
```
- Then  go in fpm folder
```bash
cd fpm

root@DIVS-BLR1-DEV:/etc/php/7.4/fpm# ls

conf.d  php-fpm.conf  php.ini  pool.d
```
- Open php.int file
```bash
vim php.ini
```
- Type  / and search for memory limit
- once you find it type (i key to insert) and the then change  size from 128 or 256 to 512
```bash
memory_limit = 512M
```
