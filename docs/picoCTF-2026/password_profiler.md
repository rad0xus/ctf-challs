### Challenge

I used CUPP to generate a wordlist from the supplied personal details, then ran it through the provided password checker. [Challenge page](https://learn.cylabacademy.org/library/712)

### Solve

I cloned CUPP and ran its interactive profile mode:

```bash
git clone https://github.com/Mebus/cupp.git
cd cupp
python3 cupp.py -i
```

I put the generated list in the challenge directory and ran the checker:

```bash
python3 check_password.py
```

The checker found the password, and I used it to get the flag.
