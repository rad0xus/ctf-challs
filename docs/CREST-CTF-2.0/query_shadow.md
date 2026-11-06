### Challenge

I changed my saved display name, then triggered its use in `/colleagues`; that exposed a second-order SQL injection.

### Solve

I tested the query with `ORDER BY` and learned it returned two columns. An error confirmed that the application used SQLite.

I used SQLite's `json_extract()` errors to reveal the table names, the `secrets` columns (`id`, `name`, `value`), and the secret value.

### Flag

```text
crest{sec0nd_0rder_1nj3ct10n_sh4d0w}
```
