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
### 6. Timestamp in Terminal
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
### 8. 



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
-[ ] Host
-[ ] VirtualBox
-[ ] VM
2. start script to auto upload my notes and screenshoots to private github account
3. connect VPN
4. Login to website


## Not sure about:
### 1. Install OBS studio? use virtualbox screen capture? 1 fps for backup screen shots
### 2. git hub to save notes and screenshots 	
	Automate a script to upload the info every 5 min if github is pingable. 
	Automate screenshots every min (What is the max file size for uploading to github?). should save info to github notes for OSCP. 
### 3. 

