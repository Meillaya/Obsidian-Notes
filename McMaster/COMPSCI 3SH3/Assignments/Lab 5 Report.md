COMPSCI 3SH3 Fall, 2022\
By: Nathan Agbomedarho\
Student ID: 400081762\
Date: December 4 2022\

# Lab 5 Report

The SJF algorithm compares the burst size of jobs and schedules the shortest first. 
add(), inserts a new task into the list of task, schedule() process the schedule and pickNextTask() returns the next selected task to run by linearly traversing the list to find the shortest burst time.


The Round Robin with priority algorithm functions by using a time quantum(time slice) to process each task. add() inserts a new task into the list of tasks. schedule() process and runs the list of tasks and if there are more than 1 task with the same priority(duplicate) Round Robin occurs, else it runs normally. If the burst value is greater than the quantum value then the task is inserted at the end. pickNextTask() selects the next task to run, depending on the highest priority.
