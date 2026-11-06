### Challenge

I analyzed a 64-bit program whose oversized input can redirect execution to `win`. [Challenge page](https://learn.cylabacademy.org/library/755)

### Solve

I checked the local binary and its protections:

```bash
file vuln
checksec --file=vuln
```

The source reads up to 128 bytes into a 32-byte buffer, and `checksec` showed NX enabled with PIE disabled. I used cyclic input in the debugger to find the return offset, then redirected execution to `win` and got the flag.
