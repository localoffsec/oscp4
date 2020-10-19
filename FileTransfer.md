
# start a webserver:
====================
# -m is for module
pyhton -m SimpleHTTPServer 8080
python3 -m http.server 8000
# Whatever folder you start this in will be the folder listed and available online. 
# so if you run this from the home folder, then you'd open a browser and go to the IP/PORT and see everything in the home folder.


How to spin up an FTP server with python:
=========================================
# create anonymous ftp with write access to your filesystem. More features are available under the hood for better security so just go look:
python -m pyftpdlib
python -m pyftpdlib --help
python3 -m pyftpdlib.ftpserver

sudo pip3 install pyftpdlib
python3 -m pyftpdlib -w  


#Alternatively 'my_server.py':
==============================
#!/usr/bin/env python
from pyftpdlib import servers
from pyftpdlib.handlers import FTPHandler
address = ("0.0.0.0", 21)  # listen on every IP on my machine on port 21
server = servers.FTPServer(address, FTPHandler)
server.serve_forever()


NetCat File Transfer:
=====================
# nc is basically a built-in tool from any UNIX-like systems (even embedded systems), so it's perfect for "quick and temporary way to transfer files".
# Step 1, on the receiver side, run:
nc -l 12345 | tar -xf -
# this will listen on port 12345, waiting for data.

# Step 2, on the sender side:
tar -cf - ALL_FILES_YOU_WANT_TO_SEND ... | nc $RECEIVER_IP 12345

# You can also put pv in the middle to monitor the progress of transferring:
tar -cf - ALL_FILES_YOU_WANT_TO_SEND ...| pv | nc $RECEIVER_IP 12345

# After the transferring is finished, both sides of nc will quit automatically, and job done.







using "systemctl enable" instead if "service * start" means the service will automatically start after reboot. 
Examples:
systemctl enable postgresql
systemctl enable ssh 
systemctl disable ssh
 
