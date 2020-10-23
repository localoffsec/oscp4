# SMB

# Enumeration & Attacking Network Services
### SAMB / SMB / Windows Domain Enumeration
### SMB Enumeration Tools
```
nmblookup -A target
smbclient //MOUNT/share -I target -N
smbclient -N -L \\\\10.10.10.27\\
rpcclient -U "" target
enum4linux target
```

## Fingerprint SMB Version
smbclient -L //192.168.1.100 

## Find open SMB Shares
nmap -T4 -v -oA shares --script smb-enum-shares --script-args smbuser=username,smbpass=password -p445 192.168.1.0/24   

## Enumerate SMB Users
nmap -sU -sS --script=smb-enum-users -p U:137,T:139 192.168.11.200-254 


