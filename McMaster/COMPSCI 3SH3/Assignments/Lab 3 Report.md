COMPSCI 3SH3 Fall, 2022
By: Nathan Agbomedarho
Student ID: 400081762
Date: November 6 2022

<h1 align="center"> Lab 3 Report </h1>

**Q1: stats.c
``` C
#include  <pthread.h>

#include  <stdio.h>

#include  <stdlib.h>

  

#define  NUMBER_OF_THREADS 3

  

void *averageFinder(void *params);      /*  thread  that  calculates  average  */

void *minimumFinder(void *params);      /*  thread  that  calculates  minimum  */

void *maximumFinder(void *params);      /*  thread  that  calculates  maximum  */

  

int argCount, avg, min, max;

  

int main(int argc, char * argv[]) {

  

    argCount = argc - 1;

    int arguments[argCount];

  

    for (int i = 0; i < argCount; i++) {

        arguments[i] = atoi(argv[i + 1]);

    }

  

    pthread_t workers[NUMBER_OF_THREADS];

  

    pthread_create(&workers[0], 0, averageFinder, (void *) &arguments);

    pthread_create(&workers[1], 0, minimumFinder, (void *) &arguments);

    pthread_create(&workers[2], 0, maximumFinder, (void *) &arguments);

  

    for (int i = 0; i < NUMBER_OF_THREADS; i++) {

        pthread_join(workers[i], NULL);

    }

  

    printf("The average value is %d \n", avg);

    printf("The minimum value is %d \n", min);

    printf("The maximum value is %d \n", max);

}

  

void *averageFinder(void *params) {

    int *l = (int *) params;

    int sum = 0;

    for (int i = 0; i < argCount; i++) {

        sum += l[i];

    }

    avg = sum/argCount;

    pthread_exit(0);

}

  

void *minimumFinder(void *params) {

    int *l = (int *) params;

    min = l[0];

    for (int i = 1; i < argCount; i++) {

        if (l[i] < min) {

            min = l[i];

        }

    }

    pthread_exit(0);

}

  

void *maximumFinder(void *params) {

    int *l = (int *) params;

    max = l[0];

    for (int i = 1; i < argCount; i++) {

        if (l[i] > max) {

            max = l[i];

        }

    }

    pthread_exit(0);

}
```

The code above initializes three threads, three separate functions for the average, maximum and minimum operations and also 3 global variables for each. We begin by accepting input arguments with a loop, and then we send these parameters to each of the functions. The functions calculate the values and once each thread has finished executing, they are joined and the results are printed out.

**Q2: prime.c
```C
#include  <pthread.h>

#include  <stdio.h>

#include  <stdlib.h>

  

#define  NUMBER_OF_THREADS 1

  

void *primeFinder(void *params);      /*  thread  that  calculates  prime  */

int primeCheck(int num);             /*  helper  function  that  checks  prime*/

  

int input;

  

int main(int argc, char * argv[]) {

  

    input = atoi(argv[1]);

  

    pthread_t workers[NUMBER_OF_THREADS];

  

    pthread_create(&workers[0], 0, primeFinder, (void *) &input);

  

    pthread_join(workers[0], NULL);

}

  

void *primeFinder(void *params) {

    int *val = (int *) params;

    int n = *val;

  

    for (int i = 2; i <= n; i++) {

        if (primeCheck(i)) {

            printf("%d ", i);

        }

    }

    printf("\n");

    pthread_exit(0);

}

  

int primeCheck(int num) {

    int res = 1;

    for (int i = 2; i < num; i++) {

        if (num % i == 0) {

            res = 0;

        }

    }

    return res;

}
```

My code initializes a single thread and function to find prime numbers preceding and including the input argument. This argument is passed to primeFinder and then, primeCheck, verifies that the number is a prime. The calculated values are then returned and printed out.
