```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main () {
   char command[50];
   char command2[50];
   char command3[50];

   strcpy( command, "wmic process where name="program.exe" get commandline" );
   strcpy( command2, "wmic process where name="program.exe" get parentprocessid");
   strcpy( command3, "wmic process where processid=<id number from previous command> get commandline");
   system(command);
   system(command2);
   system(command3);

   return(0);
} 
```
```
echo %ERRORLEVEL%
```


```
#include <stdio.h>
#include <stdlib.h>


int main(int argc, char **argv)
{
        int status;
        if(( status = system("kill -9 13043")) != -1){
                fprintf(stdout, "kill command exit status: %d\n", WEXITSTATUS(status));
        }

        return 0;
}
```


```
when the EXE is run it should pop up a CMD and run:
whoami
# to see who the program is being run as
whoami /priv
# to tell me what priveldges the program is being run with
wmic process where name="program.exe" get commandline
# tell me what command was used to call program.exe
wmic process where name="program.exe" get parentprocessid
# to tell me the process id of the command that  called program.exe
wmic process where processid=<id number from previous command> get commandline
# tell me the location of the program that ran the command
```   
   



```
sudo apt-get install mingw-w64 gcc -y
gcc -c main.c     <== Linux
i686-w64-mingw32-gcc -static-libstdc++ -static-libgcc -o main32.exe main.c       <== Windows 32-bit
x86_64-w64-mingw32-gcc -static-libstdc++ -static-libgcc -o main64.exe main.c     <== Windows 64-bit
```
