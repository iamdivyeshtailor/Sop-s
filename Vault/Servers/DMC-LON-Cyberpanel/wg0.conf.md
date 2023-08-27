
```

[Interface]
PrivateKey = QFmbxE64Nv3cy9F5LSVo1CBAUyAgtXnqvWWU232EmW8=
Address = 198.18.7.3/24

PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

[Peer]
PublicKey = 3QFjDyfRF7ZweMsO0Dn2N8bYT4O8UPd67KVi7xQQyiA=
AllowedIPs = 198.18.7.1/24
Endpoint = 219.91.133.131:51820

```