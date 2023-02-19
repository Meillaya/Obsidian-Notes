COMPSCI 3SH3 Fall, 2022
By: Nathan Agbomedarho
Student ID: 400081762
Date: October 23 2022

<h1 align="center"> Lab 2 Report </h1>

**Q1: time-shm.c**
``` C
#include <sys/types.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <fcntl.h>
#include <sys/shm.h>
#include <sys/stat.h>
#include <sys/mman.h>
#include <sys/time.h>

#define READ_END 0
#define WRITE_END 1

int main(int argc, char **argv) {
    // Create pipe
    int fd[2];
    if (pipe(fd) == -1) {
        fprintf(stderr,"Pipe failed\n");
        return 1;
    }
    // Storing time
    struct timeval before, after, rewrite;
    // For child process
    pid_t pid;
    pid = fork();
    // Error creating child
    if (pid < 0) {
        fprintf(stderr, "Fork Failed\n");
        return 1;
    }

    // Parent process

    if (pid > 0) {
        // Wait for completion of child
        wait(NULL);
        // Close write end and get end time
        close(fd[WRITE_END]);
        gettimeofday(&after, NULL);
        // Get start time from pipe and subtract from start time to show total time
        read(fd[READ_END], &rewrite, sizeof(rewrite));
        float time = (after.tv_usec + after.tv_sec*1000000) - (rewrite.tv_usec + rewrite.tv_sec*1000000);
        printf("Elapsed time: %.5f\n", time/1000000);
        // Close read end
        close(fd[READ_END]);
    }

    // Child process

    else {
        // Close read end and write start time to pipe
        close(fd[READ_END]);
        gettimeofday(&before, NULL);
        write(fd[WRITE_END], &before, sizeof(before));
        // Close write end and execute argument
        close(fd[WRITE_END]);        
        execvp(argv[1], &argv[1]);
    }
    return 0;
}
```

A shared memory object is initially created, then the child process take the current time, and writes to the shared memory. Once the child process has completed its task, the parent process then gets the start time and current time from the shared memory and calculates the difference between both. This method is faster than using pipes, uses less resources and gives you greater control over resource allocation, however the downside is that multiple processes can access shared memory simultaneously unless mutexes or semaphores are used.



**Q2: time-pipe.c**
```C
#include <sys/types.h>
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <sys/shm.h>
#include <sys/stat.h>
#include <sys/mman.h>
#include <sys/wait.h>
#include <sys/time.h>


int main(int argc, char **argv) {

    // For shared memory

    const int SIZE = 4096;

    const char *name = "OS";

    int fd;

    char *ptr;

    fd = shm_open(name, O_CREAT | O_RDWR, 0666);

    ftruncate(fd, SIZE);

    ptr = (char *)

    mmap(0, SIZE, PROT_READ | PROT_WRITE, MAP_SHARED, fd, 0);

    // For child process

    pid_t pid;

    pid = fork();
    // Storing time

    struct timeval before, after;

    // Error creating child

    if (pid < 0) {
        fprintf(stderr, "Unable to create child processes \n");
        return 1;
    }

    // Child process
    else if (pid == 0) {
        // Get start time and add to shared memory
        gettimeofday(&before, NULL);
        char convert[20];
        sprintf(convert, "%ld", before.tv_usec + before.tv_sec*1000000);
        sprintf(ptr, "%s", convert);
        ptr += strlen(convert);
        // Execute argument
        execvp(argv[1], &argv[1]);
    }

    // Parent process
    else {
        // Wait for completion of child
        wait(NULL);
        // Take end time and subtract from start time to show total time
        gettimeofday(&after, NULL);
        float time = after.tv_usec + after.tv_sec*1000000 - atof((char *)ptr);
        printf("Elapsed time: %.5f\n", time/1000000);
        // Remove shared memory
        shm_unlink(name);
        return 0;
    }

}
```

With this method, a pipe is created initially, a child process then takes the current time and writes to the pipe. The parent process waits until the child process completes, then it gets the start and current time and takes the difference. One the pipe closes, it switches to either the parent or the child.
This method is easy to setup and you dont have to worry about buffering and managing resources, as the OS does that for you. However, the downside is that there is a data capacity restriction compared to shared memory.

Pipes have synchronization inherently, reading/writing will suspend it. With shared memory you have to implement such a feature for read/writes using semaphores to ensure that only one process can access the shared memory at a time. In summary, pipes are simpler and excell at one-to-one communicating, shared memory is more flexible, but more expertise is required for its implementation to avoid potential erros (i.e segmentation faults).