### Challenge

I pushed a commit with the required author metadata and a `flag.txt` file. [Challenge page](https://learn.cylabacademy.org/library/764)

### Solve

I set the commit identity, created `flag.txt`, and pushed the commit:

```bash
git config user.name 'root'
git config user.email 'root@picoctf'
touch flag.txt
git add .
git commit -m 'changes'
git push origin master
```

The server checked the commit author and returned the flag from its push hook.
