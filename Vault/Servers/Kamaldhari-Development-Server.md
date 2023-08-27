
```

[Interface]
PrivateKey = 6C71Vj2GErdQmEtG/yVLe3KYyoZ73d0PLo9Wujym30c=
Address = 198.18.7.2/32

PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

[Peer]
PublicKey = 3QFjDyfRF7ZweMsO0Dn2N8bYT4O8UPd67KVi7xQQyiA=
AllowedIPs = 192.18.7.1/32
Endpoint = 219.91.133.131:51820

```