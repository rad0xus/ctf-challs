### Challenge

I decoded the message's Base64, hex, URL-escaped braces, and ROT13 layers. [Challenge page](https://learn.cylabacademy.org/library/710)

### Solve

I reversed the transformations in order:

```bash
base64 -d message_multicode.txt > stage1.hex
xxd -r -p stage1.hex > stage2.txt
cat stage2.txt
```

The hex-decoded text was `npnqrzl%7Barfgrq_rap0qvat_74ns0p65%7D`. I replaced the escaped braces and applied ROT13:

```bash
sed 's/%7B/{/g; s/%7D/}/g' stage2.txt | rot13
```

### Flag

```text
academy{nested_enc0ding_74af0c65}
```
