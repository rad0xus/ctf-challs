### Challenge

I reversed the local password database binary and inspected the value its hash routine returned. [Challenge page](https://learn.cylabacademy.org/library/767)

### Solve

The program XORs the hidden input bytes with `0xaa`, then applies a 64-bit DJB2-style hash. I set a breakpoint on `hash`, ran the program, and inspected its return value:

```text
(gdb) break hash
(gdb) run
(gdb) finish
(gdb) info registers rax
```

GDB returned the signed value `-3209081493549540382`.
