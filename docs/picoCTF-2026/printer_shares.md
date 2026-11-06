### Challenge

I connected to the public SMB service on its nonstandard port and retrieved `flag.txt`. [Challenge page](https://learn.cylabacademy.org/library/759)

### Solve

I listed the shares anonymously, connected to `shares`, and downloaded the flag:

```bash
smbclient -L //<challenge-host> -p <challenge-port> -N
smbclient //<challenge-host>/shares -p <challenge-port> -N
smb: \> get flag.txt
```
