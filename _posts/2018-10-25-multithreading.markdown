---
layout: "post"
title: "Multithreading"
date: "2018-10-25 16:00"
author: Jiayun
---

{% include mathjax.html %}

### What is a Thread?

![thread](/myblog/assets/thread.png){:height="30%" width="30%"}

Threads are "light-weighted" processes inside a process - a sequence of instructions. It allows concurrency and parallelism in a program. For example, in a Client-Server architecture, threads can be created to handle requests or to manage remote objects in the server. Below is a figure illustrates 4 different C-S architecture using multithreading (4 different processes in one server). From server1 to server4 are **Thread-per-connection**, **Worker-Pool (fixed number of threads)**, **Thread-per-request** and **Thread-per-object** respectively.

![thread](/myblog/assets/cs.png){:height="70%" width="70%"}

### User-level Threads and Kernel Threads

In order to reduce context switch expenses, [Thomas et al.](https://homes.cs.washington.edu/~bershad/Papers/p53-anderson.pdf) developed an approach to mediate between user-level scheduling and kernel scheduling of threads. I drew the figure below to show the basic idea of a Scheduler Activation (SA). Further readings can be found in [Coulouris'book](http://www.gecg.in/papers/ds5thedn.pdf), pp.302 (pdf page 320).

![thread](/myblog/assets/sa.png){:height="70%" width="70%"}

In addition to 4 different kind of events (Virtual processor allocated, SA Blocked, SA Unblocked and SA preempted) that the SA sends to the user-level, a user-level scheduler can inform the kernel that a virtual processor is no longer needed / a new (additional) virtual processor is needed.
