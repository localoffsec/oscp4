


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









