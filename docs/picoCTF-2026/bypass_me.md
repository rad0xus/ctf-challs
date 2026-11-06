### Challenge

I inspected the local binary's password check to recover the value it compares against. [Challenge page](https://learn.cylabacademy.org/library/761)

### Solve

I used LLDB to inspect the decoded password buffer. The program XORs the stored bytes with `0xaa`; the buffer contained `SuperSecure` at the comparison:

```text
(lldb) expr (char*)($rbp - 0x110)
```

I entered this password:

```text
SuperSecure
```
