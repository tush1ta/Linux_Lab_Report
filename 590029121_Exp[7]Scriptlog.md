EXPERIMENT 7 - Shell Programming
================================

Aim
---



**To understand and practically apply process management commands, viewing and monitoring processes, terminating, process priortization and scheduling**

* * *

Tools & Software Used
---------------------



* **Terminal Emulator:** GNOME Terminal
* **Shell:** Bash (_Bourne-Again Shell_)

* * *

Basic Process Commands
======================



#### 1.  `ps`  - shows currently running processes





![2aa725c1-c78c-4dc7-85b3-dd1e4aaadfae](.img/p33.png)



#### 2.  `top`  - shows running processes dynamically with their CPU and memory usage

![ffcdeacf-7b19-4213-9988-64dd54a95cd3](.img/p34.png)



#### 3.  `pstree`  - shows process hierarchy

![526cd856-2856-451b-b613-0fdf384a2b99](.img/p35.png)







#### 4.  `kill<PID>`  - stops the proccess

![5104442d-4f8e-410f-b4c1-78b0a4e46b3e](.img/p36.png)
Process Priotization
====================

#### 1.  `nice -n <value> command`  - starts a process with a specific priority

![d176016e-4d2d-4efe-85c7-97e58cdf1207](.img/p37.png)



#### 2.  `renice <value> - p <PID>`  - change priority of a runnung process

Process Scheduling
==================

#### 1.  `at <TIME>`  - schedules one time tasks (_works only with mins, hours & days_)



#### 2.  `cron`  - runs specific tasks at given time / dates

* * * * * command
          │  │  │  │  │
          │  │  │  │  └── Day of week (0–6, Sunday=0)
          │  │  │  └──── Month (1–12)
          │  │  └─────── Day of month (1–31)
          │  └────────── Hour (0–23)
          └───────────── Minute (0–59)
          
          

LAB Exericeses
==============

TASK 1: File existence Check
============================

#### Script:

![103fc4cc-f9b9-41b8-96d3-02ad1a4305eb](.img/p39.png)



#### 

#### Output:

![c7dd8166-9e7f-4d73-a465-5c8b01f919d5](.img/p40.png)

TASK 2: Print no.'s from 1 to 10
================================

#### Output:

    ![b00327b2-76bf-4ca8-bfb2-274f4cd792c8](.img/p41.png)

TASK 3: Count lines, words and characters in a file
===================================================

#### Script:

![cfafbc83-9688-4aaa-b7df-7c382af9efa5](.img/p42.png)



#### Output:

![1b71b064-9cb3-482e-a9a2-75dabb980914](.img/p43.png)

TASK 4: Factorial of a number using funtion
===========================================

#### Script:

![58f8cf31-c68d-4fd7-9f16-6ba2797882b5](.img/p44.png)





#### Output:

![325eae8b-b8d8-47af-9766-cc3cc83edf81](.img/p45.png)

OBSERVATIONS
============

* Successfully viewed running processes using ps, top, and pstree.

* Able to terminate processes using kill and control their priority with nice and renice.

* Scheduled tasks using at for one-time execution and cron for recurring jobs.
  
  

CONCLUSION
==========

The experiment enhanced understanding of Linux process management and scheduling.
