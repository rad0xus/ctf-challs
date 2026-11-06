### Challenge

I inspected the provided source and ELF to answer the 13-question binary-analysis quiz.

### Solve

I ran these local inspection commands:

```bash
file vuln
strings vuln
checksec --file=vuln
```

I checked the `win` symbol in GDB:

```text
(gdb) print win
```

I used the source and binary details to answer the quiz, and the service returned the flag.
