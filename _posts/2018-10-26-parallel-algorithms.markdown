---
layout: "post"
title: "Parallel Algorithms"
date: "2018-10-26 14:09"
author: Jiayun
---
{% include mathjax.html %}
- [Parallel Add](#parallel-add)
	- [Sub-Optimal](#sub-optimal)
	- [Optimal](#optimal)
- [Parallel Sort](#parallel-sort)
	- [Naive Version](#naive-version)


## Parallel Add

### Sub-Optimal

| metric | value |
|:-----:|:-----:|
|**Problem Size**|$$n$$|
|**Number of Processors p(n)** |$$\frac{n}{2}$$, which is $$O(n)$$|
|**Number of Parallel Steps t(n)**| $$O(log(n))$$|
|**Number of Operation per step** | $$O(1)$$|
|**w(n)** |$$O(nlog(n))$$|

![subadd](/myblog/assets/sub_add.png){:width="50%" align="center"}

### Optimal (with 2 stages)

| metric | value |
|:-----:|:-----:|
|**Problem Size**|$$n$$|
|**p(n)** | $$O(\frac{n}{log(n)})$$|
|**t(n)**| 1st stage: $$O(log(n))$$, 2nd stage: $$O(log(\frac{n}{log(n)}))$$|
|**Number of Operation per step** |$$O(1)$$ for both stages|
|**w(n)** |$$O(log(n))$$|

![subadd](/myblog/assets/opt_add.png)

In second stage, a sub-optimal add algorithm is applied to an array of size $$\frac{n}{log(n)}$$ (which is p(n)), and there are $$\lceil{log(\frac{n}{log(n)})}\rceil$$ parallel steps.

for stage 2, $$t_{s2}(n)$$:
$$\theta(\lceil{log(\frac{n}{log(n)})}\rceil)$$ = $$\theta(log(n)\ -\ loglog(n))$$ = $$\theta(log(n))$$

Total work:

$$w(n)$$ = $$p(n)$$ * $$t(n)$$ = $$\theta(\frac{n}{log(n)})$$ * $$\theta(log(n)\ +\ log(n))$$ = $$\theta(log(n))$$

## Parallel Broadcast
To simulate CRCW in an EREW, with a penalty of $$O(logn)$$ steps.
![subadd](/myblog/assets/bcast.png)

## Parallel Maximum

### Max1

| metric | value |
|:-----:|:-----:|
|**Problem Size**|$$n$$|
|**p(n)** | $$\theta(n^2)$$|
|**t(n)**| $$O(1)$$|
|**w(n)** |$$\theta(n^2)$$|

![subadd](/myblog/assets/max1.png)

### Max2

| metric | value |
|:-----:|:-----:|
|**Problem Size**|$$n^2$$|
|**p(n)** | $$\theta(n^2)$$|
|**t(n)**| $$\theta(loglog(n))$$|
|**w(n)** |$$\theta(n^2loglog(n))$$|

![subadd](/myblog/assets/max2.png)

To analyze the complexity, since in every recursive step the problem size is cut to the square root of the original, as shown in the example below:

![subadd](/myblog/assets/max2_2.png)

Assume there are $$j$$ recursive steps in total:

$$n^{\frac{2}{2^j}}$$ = $$2^2$$

$$n^{\frac{1}{2^j}}$$ = $$2$$

$$\frac{1}{2^j}$$ = $$log_n2$$ = $$\frac{log2}{logn}$$

$$2^j$$ = $$\frac{logn}{log2}$$

$$j$$ = $$log\frac{logn}{log2}$$ = $$loglogn\ -\ loglog2$$ = $$\theta(loglogn)$$



## Parallel Sort

### Naive

| metric | value |
|:-----:|:-----:|
|**total number of operations**| 1st stage: $$O(\frac{n}{p(n)}log(\frac{n}{p(n)}))$$, 2nd stage: $$O(n)$$|

![subadd](/myblog/assets/naive_merge.png)
