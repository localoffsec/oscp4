# SMB

# Enumeration & Attacking Network Services
### SAMB / SMB / Windows Domain Enumeration
### SMB Enumeration Tools
```
nmblookup -A target
smbclient //MOUNT/share -I target -N
smbclient -N -L \\\\10.10.10.27\\
smbclient -L <IP>
smbclient -U <domain>\\<user> -L <IP>
rpcclient -U "" target
enum4linux target
```

## Fingerprint SMB Version
smbclient -L //192.168.1.100 

## Find open SMB Shares
nmap -T4 -v -oA shares --script smb-enum-shares --script-args smbuser=username,smbpass=password -p445 192.168.1.0/24   

## Enumerate SMB Users
nmap -sU -sS --script=smb-enum-users -p U:137,T:139 192.168.11.200-254 

## Enumerate users from SMB
```
python /usr/share/doc/python-impacket-doc/examples/samrdump.py 192.168.XXX.XXX
```
## RID cycle SMB / enumerate users from SMB
``
ridenum.py 192.168.XXX.XXX 500 50000 dict.txt
```
## Enmerate users from SNMP
```				
snmpwalk public -v1 192.168.X.XXX 1 |grep 77.1.2.25 |cut -d” “ -f4
```
## Enmerate users from SNMP
```
python /usr/share/doc/python-impacket-doc/examples/samrdump.py SNMP 192.168.X.XXX
```
## Search for SNMP servers with nmap, grepable output
```
nmap -sT -p 161 192.168.X.XXX/254 -oG snmp_results.txt 					
```

## Nmap script to scan for vulnerable SMB servers - WARNING: unsafe=1 may cause knockover
```
nmap -v -p 445 --script=smb-check-vulns --script-args=unsafe=1 192.168.1.X	
```
## Nmap script to scan for vulnerable SMB servers – WARNING: unsafe=1 may cause knockover
```
nmap –script smb-check-vulns.nse –script-args=unsafe=1 -p445 [host]         
```


## Find open SMB Shares
```
nmap -T4 -v -oA shares --script smb-enum-shares --script-args smbuser=username,smbpass=password -p445 192.168.1.0/24   
```

## Enumerate SMB Users
```
nmap -sU -sS --script=smb-enum-users -p U:137,T:139 192.168.11.200-254 
```


