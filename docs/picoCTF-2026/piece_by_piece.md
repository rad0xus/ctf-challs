### Challenge

I concatenated the five archive fragments, entered the password, and read the flag. [Challenge page](https://learn.cylabacademy.org/library/740)

### Solve

I concatenated the parts in order, ran `unzip`, entered `supersecret`, and read `flag.txt`:

```bash
cat part_aa > part.zip
cat part_ab >> part.zip
cat part_ac >> part.zip
cat part_ad >> part.zip
cat part_ae >> part.zip
unzip part.zip
cat flag.txt
```
