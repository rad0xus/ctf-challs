### Challenge

The service sends 20 ELF rounds, gives 10 seconds per round, and expects the secret as a decimal number. [Challenge page](https://learn.cylabacademy.org/library/754)

### Solve

I inspected a round's disassembly and found the 32-bit secret in a `mov` immediate. I read its four little-endian bytes after `c7 45 fc` and converted them to an unsigned decimal integer.

I used this local extraction for each supplied hex dump:

```python
import re

elf = bytes.fromhex(open("round.hex").read())
match = re.search(rb"\xc7\x45\xfc(.{4})", elf, re.DOTALL)
if match is None:
    raise ValueError("secret immediate not found")
print(int.from_bytes(match.group(1), "little"))
```

Submit the printed decimal value and repeat for each round.
