# Setup Kali

### 1. Install Kali Linux https://www.kali.org/downloads/

### 2. Update Kali: 
```
sudo apt update && sudo apt upgrade -y && sudo apt install -y curl wget ssh openvpn git
```

### 3. Install pip for Python2: 
```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
```

### 4. Install Feroxbuster https://github.com/epi052/feroxbuster

### 5. Autosave all commands to History forever with a timestamp
taken from: http://jesrui.sdf-eu.org/remember-all-your-bash-history-forever.html
```
# Append the following lines to /etc/bash.bashrc:

HISTTIMEFORMAT='%F %T '
HISTFILESIZE=-1
HISTSIZE=-1
HISTCONTROL=ignoredups
HISTIGNORE=?:??

# append to history, don't overwrite it
shopt -s histappend                 
# attempt to save all lines of a multiple-line command in the same history entry
shopt -s cmdhist
# save multi-line commands to the history with embedded newlines
shopt -s lithist
```

### 6. Timestamp in Terminal (for screenshots)
taken from: https://www.contextis.com/en/blog/logging-like-a-lumberjack
```
cp ~/.bashrc ~/.bashrc.back
nano ~./bashrc
# find the line(s) with PS1= and 
# add the following inside the ' '
[`date +"%d-%b-%Y %T"`] > 
# [21-Feb-2020 10:57:20] > 
```

### 7. clone this repo 
```
git clone https://github.com/ciwen3/OSCP.git
```

# Setup Windows 10 
## Settings:
1. Antivirus turned off
2. firewall turned off

## Software:
1. Immunity Debugger
2. moana.py
3. gitbash
4. firefox
5. Foxy Proxy
6. Burp Community edition
7. Java 
8. OWASP ZAP

## Attack Checklist:
1. https://book.hacktricks.xyz/windows/checklist-windows-privilege-escalation

# OSCP Start Checklist:
1. start Automatic Screenshots (saving to github folder)
	- [ ] Host: WinKey + G, snipping tool
	- [ ] VirtualBox: VM settings > Display > Recording > Enable Recording, Frame Size: 1024x768 (4:3), Frame Rate: 1 fps, Video Quality: high
	- [ ] Windows VM: snipping tool
	- [ ] Kali VM: 
	```
	PrtSc – Save a screenshot of the entire screen to the “Pictures” directory.
	Shift + PrtSc – Save a screenshot of a specific region to Pictures.
	Alt + PrtSc  – Save a screenshot of the current window to Pictures.
	Ctrl + PrtSc – Copy the screenshot of the entire screen to the clipboard.
	Shift + Ctrl + PrtSc – Copy the screenshot of a specific region to the clipboard.
	Ctrl + Alt + PrtSc – Copy the screenshot of the current window to the clipboard.
	```
2. start script to auto upload my notes and screenshoots to private github account

	https://github.com/ciwen3/OSCP/blob/master/PreTest/Auto-Upload.md
3. connect OSCP VPN
4. Login to OSCP website

# TODO:
1. 

## Not sure about:
### 1. Install OBS studio?? gnome-screenshot?? imagemagick??
### 2. cherrytree
### 3. 
