# Definitions
## Feasible
A schedule \sigma is said to be feasible if all tasks are able to complete within a set of constraints.

## Schedulable
Task set \Gamma is said to be schedulable if there exists a feasible schedule for it.

## Optimality
* Algorithm finds a feasible schedule if there exists one
And tries for example to optimize for:
* Minimize the maximum lateness
* Minimize the number of deadline misses
* Maximize the total reward value of completed tasks

## Lateness
L_i = f_i - d_i
L < 0 : slack
L > 0 : deadline miss

# Classical Scheduling Policies
## FCFS (First Come First Serve)
- very unpredictable
    (3 tasks (S,M,L) arriving right after each other. The response time depends strongly on the order of arrival)
- not optimal
* Non Preemptive
* Dynamic
* Online

## SJF (Shortest Job First)
+ Minimize average response time

* Non preemtive or preemptive
* Static
* Online or Offline

## Priority Scheduling
* fixed priorities for each task.
* Same priorities are served FCFS

* Preemptive
* Static or Dynamic
* Online

Problem: Starvation (which can be sovled with aging)

Note:
* p_i relative to 1/C_i => SJF
* p_i relative to 1/r_i => FCFS

## Round Robin

# Real-Time Aglorithms
* relative deadlines D_i (static)
* absolute deadlines d_i (dynamic)

## EDD (Earliest Due Date)
Earliest RELATIVE Deadlines (D_i)
Minimizes the maximum lateness (L_max)

* All tasks arrive simultaneously
* Fixed priority (D_i is known in advance)
* Preemption (is not an issue)

off line guarantee test:
for all i, check if the sum of all C_k is less or eq. than D_i (where k are all the tasks which should finish before (and incl.) task i).

## EDF (Earliest Deadline First)
Earliest absolute deadline (d_i)
Minimizes the maximum lateness

* arrive at any time
* Dynamic priority (d_i depends on r_i)
* Full preemtive 

on line guarantee test:
for all i should hold that, the sum of all 'to do' computations is less than the deadline d_i - the current time t.

## LDF (Latest Deadline First)
Constructed bottom->up!
Handles precedences.
nodes with no successors (so the bottom ones) are scheduled according to the lateste deadline. (note: sometimes this can be tricky)

## EDF*
transforms precedence constraints into modified arrival times and dealines to make EDF work.

A -> B

postpone arrival time of successor r^_B = r_A + C_A
advance the deadline of a predecessor: d^_A = d_b - C_B
