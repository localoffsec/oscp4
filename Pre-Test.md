1. Install Kali Linux https://www.kali.org/downloads/
2. Update Kali: 
```
sudo apt update && sudo apt upgrade -y && sudo apt install -y curl wget
```
3. Install pip for Python2: 
```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
```
4. Install Feroxbuster https://github.com/epi052/feroxbuster
5. Setup History w/ timestamp and autosave across all reminals
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
6. clone this repo 
```
git clone https://github.com/ciwen3/OSCP.git
```
7. 



## Not sure about:
1. Install OBS studio? use virtualbox screen capture? 1 fps for backup screen shots
2. script to automatically save my hacking info to private github repo (not this one). 
3. 

