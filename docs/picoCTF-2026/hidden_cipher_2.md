### Challenge

The binary multiplies each flag character by the answer to its arithmetic question, then prints the products. [Challenge page](https://learn.cylabacademy.org/library/751)

### Solve

I inspected the encoding loop in Ghidra. The challenge answer was `36`, so I divided each printed value by 36 to recover its character:

```python
values = [
    3492, 3564, 3492, 3600, 3636, 3924, 4356, 4428, 3924, 1872,
    4176, 3744, 3420, 3528, 1836, 3744, 1764, 3960, 3600, 3420,
    3564, 1764, 4032, 3744, 1836, 4104, 3420, 3636, 1800, 3492,
    3564, 3564, 3636, 3528, 3564, 4500,
]
print("".join(chr(value // 36) for value in values))
```

### Flag

```text
academy{m4th_b3h1nd_c1ph3r_e2accebc}
```
