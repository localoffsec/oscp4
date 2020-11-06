# Setup

### 1. Install Kali Linux https://www.kali.org/downloads/
### 2. Update Kali: 
```
sudo apt update && sudo apt upgrade -y && sudo apt install -y curl wget ssh openvpn
```
### 3. Install pip for Python2: 
```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
```
### 4. Install Feroxbuster https://github.com/epi052/feroxbuster
### 5. Autosave all commands to History forever
```
http://jesrui.sdf-eu.org/remember-all-your-bash-history-forever.html
Append the following lines to /etc/bash.bashrc:

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
```
Add Timestamp to Bash:
======================
# taken from https://www.contextis.com/en/blog/logging-like-a-lumberjack
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



## Not sure about:
### 1. Install OBS studio? use virtualbox screen capture? 1 fps for backup screen shots
### 2. script to automatically save my hacking info to private github repo (not this one). 
### 3. 

