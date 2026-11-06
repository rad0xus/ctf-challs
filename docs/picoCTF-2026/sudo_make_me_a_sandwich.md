### Challenge

I used the privileged Emacs command to open a root shell and read the flag. [Challenge page](https://learn.cylabacademy.org/library/735)

### Solve

I checked my sudo permissions, launched Emacs with sudo, used `M-x shell`, and read `flag.txt`:

```bash
sudo -l
sudo emacs
```
