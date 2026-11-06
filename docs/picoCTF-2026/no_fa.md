### Challenge

I traced the application's second-factor login flow and found the OTP in its session data. [Challenge page](https://learn.cylabacademy.org/library/765)

### Solve

I found the admin's SHA-256 password hash in `users.db`, recovered the password offline with the supplied wordlist, and logged in. I decoded the Flask session and read the OTP there; I didn't need to brute-force it.
