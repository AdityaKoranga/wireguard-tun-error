# wireguard-tun-error

If you ever get this error:

![image](https://github.com/AdityaKoranga/wireguard-tun-error/assets/95766110/8e06767a-4bb3-4c79-8a08-e01cc48b210b)

`Failed to resolve interface "tun": No such device`

Then check the output of this command:
```bash
modprobe wireguard
```

If it says: `Module not found`, then download the `WireGuard kernel module`:

```bash
sudo apt-get install wireguard-dkms
```

And that should work and if you still face the issue , then follow the below step:

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
```

The PostUp line tells WireGuard to run the command resolvectl dns %i 8.8.8.8 after the interface has been successfully established. The %i variable is replaced by the name of the WireGuard interface. So, if your WireGuard interface is named "Adi", the command becomes resolvectl dns Adi 8.8.8.8.

* Error:
If you get this error:

![image](https://github.com/AdityaKoranga/wireguard-tun-error/assets/95766110/6a42b8de-e99c-4499-862d-54850b21c201)

Install the module.
