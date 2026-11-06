### Challenge

The secret-creation endpoint interpolates user content directly into an SQL statement.

### Solve

I traced `/secrets/create` and found that it inserted `content` directly into the query. I used that injection to copy the admin's secret into my own account, then read the flag from my secrets list.
