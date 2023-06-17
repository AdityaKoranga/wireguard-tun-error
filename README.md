# wireguard-tun-error

If you ever get this error:

![image](https://github.com/AdityaKoranga/wireguard-tun-error/assets/95766110/8e06767a-4bb3-4c79-8a08-e01cc48b210b)

`Failed to resolve interface "tun": No such device`

Then change the `conf file` like this:

Under the `[Interface]` section of the conf file:

Instead of `DNS = 8.8.8.8`, change it to `PostUp = resolvectl dns %i 8.8.8.8`

```bash
[Interface]
PrivateKey = 
Address = 
PostUp = resolvectl dns %i 8.8.8.8


[Peer]
PublicKey = 
PresharedKey = 
AllowedIPs = 
PersistentKeepalive = 
Endpoint = 
