# Xsight-ML

Machine Learning apporach to classifying TCP flow performance.

## Problem Definition

### 1) What is the problem?

#### Informal Description

Many data transfers have poor performance but the users and/or the system 
admins are unaware that the performance problem exists. 

#### Formal Description

> A computer program is said to learn from experience E with respect to some 
class of tasks T and performance measure P, if its performance at tasks in T, 
as measured by P, improves with experience E.
~ Tom Mitchell

* __Task__ (T): Classify a TCP flow as one of N performance classes.
* __Experience__ (E): A dataset of per-flow RFC 4894 statistics labeled with a 
performance class.
* __Performance__ (P): Classification accuracy, the number of flows predicted 
correctly out of all flows considered as a percentage.



### 2) Why does the problem need solved?

- Identifying performance problems provides admins/engineers more accurate 
insight into infrastructure ultilization and enables them to resolve the 
problems if possible.
- Improving data transfer performance would increase scientific productivity.
- A solution to this problem could be used to develop a dashboard for 
admins/engineers that helps them identify and resolve flow problems faster.
- A solution to this problem could also be used to drive automated fixes to 
discovered problems.

### 3) How could the problem be solved manually (without AI)?

- E.q. Previous XSight project solutions
