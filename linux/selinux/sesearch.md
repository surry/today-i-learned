
# Finding SELinux Rules with sesearch

`sesearch` can be used to find different types of SELinux rules in the current policy. For example:

```sesearch --allow -t http_port_t```

This searches the current policy for allow rules pertaining to the type `http_port_t`.
This can be handy when trying to determine whether a specific rule is currently in force.

See the man page [for more information](https://linux.die.net/man/1/sesearch).
