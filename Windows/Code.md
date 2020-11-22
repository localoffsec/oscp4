


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


echo %ERRORLEVEL%



