### Challenge

I reversed the sequence of text transformations to recover the flag. [Challenge page](https://learn.cylabacademy.org/library/766)

### Solve

I decoded the Base64, reversed the text, restored underscores and braces, then applied ROT13:

```bash
base64 -d | rev | tr '-' '_' | tr '()' '{}' | tr 'a-zA-Z' 'n-za-mN-ZA-M'
```

### Flag

```text
academy{Revers1ng_t3xt_Tr4nsf0rm@t10ns_80c914b7}
```
