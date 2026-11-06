### Challenge

The portal hides each profile ID behind an MD5 hash. I used the predictable IDs to reach the admin profile. [Challenge page](https://learn.cylabacademy.org/library/750)

### Solve

I found the guest login in the page source and signed in. The profile showed ID `3000`, and its URL matched the MD5 hash of that number. I used the same pattern to locate the admin profile and read its flag.
