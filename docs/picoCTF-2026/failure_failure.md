### Challenge

I investigated how a global rate limit interacts with HAProxy's primary/backup health checks and failover. [Challenge page](https://learn.cylabacademy.org/library/756)

### Solve

I wrote a script to trigger the HAProxy failover and check the backup response. The backup server returned the flag.
