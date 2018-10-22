---
layout: post
title:  "并行计算学习笔记 Parallel Computing Study Notes"
author: Jiayun
---
{% include mathjax.html %}
## RAM and PRAM Model
**RAM (随机存取机)** stands for Random Access Machine, which is a simple model of computation. A program in a RAM runs according the program counter, and the operation (in the program) is translated to a constant number of instructions. It is called "random" because the time taken to access the memory is constant over all addresses.

在RAM中，一个程序中的每个语句都会被编译成不同的指令（instructions），但是指令的数量与算法本身的复杂度是没有关系的。也就是说，假设输入由$$n$$变成$$n^2$$，编译出来指令的数量不会变化。另外，在RAM中，访问内存中的任意位置所需要的时间是一致的，内存中任意位置存放的信息的大小也是一致的。
![figure1](/myblog/assets/ram.png)
[RAM slide](https://www5.in.tum.de/lehre/vorlesungen/fundalg/WS02/docs/ram.pdf)

**PRAM** stands for Parallel Random Access Machine. According to [Karp and Ramachandran](https://www.researchgate.net/publication/242456161_A_survey_of_parallel_algorithms_for_shared_memory_machines) (1988) which assumes that each processor has random access in unit time to any cell of a global memory. This ideal model permits separation of parallel computation and issues of interprocessor communication.
简单来说，PRAM是一个用于将处理器之间的数据传递和并行算法本身分隔开的理想化模型。
