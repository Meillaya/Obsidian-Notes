COMPSCI 3SH3 Fall, 2022\
By: Nathan Agbomedarho\
Student ID: 400081762\
Date: November 13th 2022\

# Assignment 3

### CPU Scheduling

1a) 

Time quantum of 1 millisecond:

Calculating CPU utilization: $1ms \times 11 = 11ms$

Every task must use the time quantum value. As such, I/O operation from I/O bound tasks return when its their turn. Non-utilizations must also be considered, namely the context switches of $11 \times 0.1 ms = 1.1 ms$.

CPU utilization: 
Total time is $1.1ms + 11ms = 12.1ms$ total time. $\frac{11ms}{12.1ms} = 0.91$ %.

b)

Time quantum of 10 milliseconds

I/O bound task takes $10 + 0.1 = 10.1$ ms.  Adding to the time cycle through all processes in round robin:  $10.1 ms + 11 ms = 21.1 ms$

CPU utilization: $\frac{20}{21.1} \times 100 = 94.786$ %


### Virtual Memory

| **Number of frames** | **LRU** | **FIFO** | **Optimal** |
|---------------------|---------|----------|-------------|
| 1                   | 20      | 20       | 20          |
| 2                   | 18      | 18       | 15          |
| 3                   | 15      | 16       | 11          |
| 4                   | 10      | 14       | 8           |
| 5                   | 8       | 10       | 7           |
| 6                   | 7       | 10       | 7           |
| 7                   | 7       | 7        | 7           |


### Massive Storage

a. 750,000 drive-hours per failure divided by 1000 drives gives 750 hours per Failure about 31 days or once per month. 

b. The human-hours per failure is 8760 (hours in a year) divided by 0.001 failure, giving a value of 8,760,000 “hours” for the MTBF. 8760,000 hours equals 1000 years. This tells us nothing about the expected lifetime of a person of age 20.

### File Management

Direct: $9 \times 512 = 4608$

Double Indirect: $\frac{512}{4} \times \frac{512}{4} \times 512 = 8388608$ 

Max Size:  $8388608 + 4608 = 8393216$
