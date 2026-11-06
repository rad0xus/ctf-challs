### Challenge

I extracted RSA private-key material from the image metadata and decrypted the provided ciphertext. [Challenge page](https://learn.cylabacademy.org/library/719)

### Solve

I ran `exiftool` and found hex-encoded key material in the comment:

```bash
exiftool image.jpeg
```

The repeated `2d` bytes decode to PEM hyphens. I saved the comment's hex as `key.hex`, reconstructed the key, then decrypted the file:

```bash
xxd -r -p key.hex > rsa_private_key.pem
openssl pkeyutl -decrypt -inkey rsa_private_key.pem -in flag.enc -out decrypt_file.txt
```
