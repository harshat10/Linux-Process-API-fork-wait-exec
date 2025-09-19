### NAME: HARSHAT.G
### REG_NO. : 212224040106
# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```
## OUTPUT
<img width="839" height="127" alt="image-1" src="https://github.com/user-attachments/assets/6b668d66-b8c6-478d-9957-2f21f9e88d78" />
## C Program to create new process using Linux API system calls fork() and exit()
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}
```
## OUTPUT
<img width="840" height="147" alt="image" src="https://github.com/user-attachments/assets/2a65de8e-050d-4b77-a0cb-9ca07c4c69d7" />
## C Program to execute Linux system commands using Linux API system calls exec() family
```

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}
```
# Output
<img width="1920" height="1080" alt="Screenshot from 2024-03-11 18-21-12" src="https://github.com/user-attachments/assets/14a26236-ebde-47b5-99e1-8aaaba898baf" />
<img width="1920" height="1080" alt="Screenshot from 2024-03-11 18-21-18" src="https://github.com/user-attachments/assets/999f2a04-b9c8-4aad-a57b-6185178c9053" />
<img width="1920" height="1080" alt="Screenshot from 2024-03-11 18-21-24" src="https://github.com/user-attachments/assets/e37ad564-24f2-40e3-b035-a2aad307c1cc" />
# RESULT:
The programs are executed successfully.
