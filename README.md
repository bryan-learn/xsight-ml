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

## Data Preparation

### 1) Data Selection

__Available Data:__

Several months worth of Web10G metrics stored per-flow from two data transfer 
nodes (DTNs). Most Web10G metrics will be used as features.

__Unavailable Data:__

A performance metric for every flow. We create synthetic data by calculating 
throughput per-flow.

__Excluded Data:__

Potentially some of the Web10G metrics.

### 2) Data Preprocessing

__Formatting:__

The Available Data is in a time-series database, InfluxDB. The data needs to be
queried and reformatted for ease of processing.

For the synthetic performance data (labels), a script is used to pull 
throughput metrics on a per-application basis. The statistics are summarized 
and a histogram is created using Scott's Rule to determine bucket width. These 
buckets are used as performance classes for the corresponding transfer 
Application. The flows and their corresponding performance class are stored in 
a flat file.

For the Web10G metrics (features), a script is used to process the flat file 
representing the synthetic performance data for a particular transfer 
Application. InfluxDB is queried to pull all the selected feastures for each 
flow in the flat file. A CSV file is produced that maps each flow's selected 
Web10G metrics to the performance class.

__Cleaning:__

There may be data instances that are incomplete or incorrect. Those instances should be mentioned here.

__Sampling:__

We are starting by sampling only the SSH Application data from the Available Data.

### 3) Data Transformation

__Scaling:__

The feature data will be scaled for better use in various algorithms. Numerical
attributes will be scaled to values between -5 and 5.

__Decomposition:__

There may be features that represent a complex concept that may be more useful 
to a machine learning method when split into the constituent parts.

__Aggregation:__

There may be features that can be aggregated into a single feature that would 
be more meaningful to the problem you are trying to solve.

## Evaluate Various Algorithms

__Test Harness:__

__Performance Measure:__

__Test and Train Datasets:__

__Cross Validation:__

__Testing Algorithms:__

## Improving Results

__Algorithm Tuning:__

__Ensembles:__

## Presenting Results

__Report:__

- Context
- Problem
- Solution
- Findings
- Limitations
- Conclusions

__Operationalize:__

- Algorithm Implementation (move from research to production)
- Model Tests (write automated tests for model and data preparation)
- Tracking (monitor model performance over time)

