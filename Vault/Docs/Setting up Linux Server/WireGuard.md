1. Create Wireguard Folder
```Shell
kd-admin@moros:~$ mkdir /etc/wireguard
kd-admin@moros:~$ umask 077
```

2. Create Private and Public key
```Shell
kd-admin@moros:~$ cd /etc/wireguard
kd-admin@moros:~$ wg genkey | tee privatekey | wg pubkey > publickey
```

3. Create a Wireguard Config
```Shell
kd-admin@moros:~$ sudo nano /etc/wireguard/wg0.conf
```
```Wireguard Config
[Interface]
PrivateKey = <client's Private Key>
Address = <client's VPN IP>
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o enp2s0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o enp2s0 -j MASQUERADE

[Peer]
PublicKey = < Servers's Public Key >
AllowedIPs = < Routes to Advertise >
Endpoint = < Server Ip Address >
```

4. Enable Wireguard Config:
```Shell
kd-admin@moros:~$ sudo systemctl enable wg-quick@wg0.service
kd-admin@moros:~$ sudo systemctl daemon-reload
```

5. start Wireguard Config:
```Shell
kd-admin@moros:~$ sudo systemctl start wg-quick@wg0
```
