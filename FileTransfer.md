
# Start a Webserver with Python:
Whatever folder you start this in will be the folder listed and available online. 
so if you run this from the home folder, then you'd open a browser and go to the IP/PORT and see everything in the home folder.
-m is for module
## Python 2
``` 
pyhton -m SimpleHTTPServer 8080
```
## Python 3
```
python3 -m http.server 8000
```

# Start an FTP Server with Python:
Install:
```
sudo pip3 install pyftpdlib
python3 -m pyftpdlib -w  
```

create anonymous ftp with write access to your filesystem.
```
python -m pyftpdlib
python -m pyftpdlib --help
python3 -m pyftpdlib.ftpserver
```

# 'my_server.py':

```
#!/usr/bin/env python
from pyftpdlib import servers
from pyftpdlib.handlers import FTPHandler
address = ("0.0.0.0", 21)  # listen on every IP on my machine on port 21
server = servers.FTPServer(address, FTPHandler)
server.serve_forever()
```

# NetCat File Transfer:
nc is basically a built-in tool from any UNIX-like systems (even embedded systems), so it's perfect for "quick and temporary way to transfer files".
open a listen on port 12345, waiting for data.
### Step 1, on the receiver side, run:
```
nc -l 12345 | tar -xf -
```

### Step 2, on the sender side:
```
tar -cf - ALL_FILES_YOU_WANT_TO_SEND ... | nc $RECEIVER_IP 12345
```
### Alternate Step 2
### You can also put pv in the middle to monitor the progress of transferring:
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
