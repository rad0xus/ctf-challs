### Challenge

I computed the shared value from the supplied Diffie–Hellman parameters and used it to decode the ciphertext. [Challenge page](https://learn.cylabacademy.org/library/715)

### Solve

The challenge leaked the private exponent `b`. I plugged its `A`, `b`, `p`, and hex ciphertext into this code:

```python
shared = pow(A, b, p)
key_byte = shared & 0xff
ciphertext = bytes.fromhex(enc)
plaintext = bytes(byte ^ key_byte for byte in ciphertext)
print(plaintext)
```
