### Challenge

The challenge provides ASCII `0` and `1` characters; I packed each group of eight bits into a byte to recover the image. [Challenge page](https://learn.cylabacademy.org/library/698)

### Solve

I inspected the input, packed the bits into bytes, then opened the JPEG:

```bash
xxd digits.bin | head -n 10
```

```python
from pathlib import Path

bits = Path("digits.bin").read_text().split()
bits = "".join(bits)
image = bytes(int(bits[i:i + 8], 2) for i in range(0, len(bits) - 7, 8))
Path("output.jpg").write_bytes(image)
```

The output starts with a JPEG/JFIF signature. I opened `output.jpg` and read the flag.
