### Challenge

I found the exposed backup configuration and used its Flask signing key to access the admin report.

### Solve

I checked `/robots.txt`, found `/static/backup/`, then requested the backup configuration directly because the directory listing returned 404:

```bash
curl http://<challenge-host>/static/backup/config.py.bak
```

I found the Flask `SECRET_KEY` in the file. I inspected the session cookie, changed its role, signed it with the leaked key, then refreshed `/dashboard` to open the report.
