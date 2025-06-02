---
title: fail2ban
description: Ban suspicious IPs based on logged activity. 
---

Ban suspicious IPs based on logged activity. 

## Instalation

```
apt install fail2ban
```

## Configuration

To use fail2ban, you need to set up *jails* that use *filters* to trigger *actions*. 

All of those can be found in `/etc/fail2ban`. 

In order to modify something, do **not** change `.conf` file but create a `.local` file instead. 

You can start by experimenting with default filters. Write all your jail configuration to jail.local as follows. Create the file if it doesn't exist. 

```title="/etc/fail2ban/jail.local"
[<FILTER NAME>]
enabled = true
banaction = nftables-allports     # See all options with `ls actions.d` You can use `dummy` to get the logs without actually doing anything
maxretry = 4                      # The IP address will be banned after <maxretry> logged failures
findtime = 1h                     # Time span the failures need to happen in
bantime = 2h                      # How long you want the IP to be banned for
logpath = /var/log/exim4/mainlog  # Path of the log.
#backend = systemd                # Use this instead of the previous line if your service writes to systemd instead of a file
```

You can create your own filter by creating the file `filters.d/<your filter>.conf`

All it needs is to have inside is:

```
[Definition]

failregex = ... <HOST> ...
```

Use "normal" regex. <HOST> will match an IP adress or hostname, it is mandatory because this is what f2b uses to ban IPs.   

For example, you can match the log `[123.45.6.789] failed authentication` with the following filter:

```
[Definition]

failregex = ^\[<HOST>\] failed authentication$
```

Reload f2b for changes to take effect.

!!! warning "Missing `fail2ban-regex`"
