---
layout: post
title: "分布式系统简介 Introduction to Distributed System"
date: "2018-10-22"
author: Jiayun
---

##What is a Distributed System?
As defined in [Coulouris'book](http://www.gecg.in/papers/ds5thedn.pdf):
A distribued system is one in which hardware or software components located at networked computers communicate and coordinate their actions only by passing messages.

![Distributed System](/assets/ds_concept.png)

分布式系统的定义：硬件，软件之间通过网络连接，他们之间只通过信息传递来进行工作上的协作和交流。分布式系统是在网络（Network）的基础上搭建的，因此网络本身并不能称之为分布式系统。

![network](/assets/network.png)

Also, there is another definition by [Tanenbaum](http://barbie.uta.edu/~jli/Resources/MapReduce&Hadoop/Distributed%20Systems%20Principles%20and%20Paradigms.pdf): A distributed system is a collection of independent computers that
appears to its users as a single coherent system.

Tanenbaum 给出了另外一个角度的定义：虽然一个分布式系统是由很多独立的电脑组成的，但在用户视角，这就是“一台电脑”（换句话来说，用户并不知道这个系统是由多少台独立的电脑组成的）

![Distributed System](/assets/ds_concept_2.png)

Example of Distributed Systems:

Cluster - a collection of interconnected stand-alone computers cooperatively
working together as a single, integrated computing resource.

Cloud - a collection of
interconnected and virtualised computers that are dynamically
provisioned and presented as one or more unified computing
resources based on service-level agreements established through
negotiation between the service provider and consumers.

Cloud 和 Cluster 之间的区别是， cluster 内的组件一般是通过LAN (局域网)相连的，而Cloud则是可以做到不受地域限制（Geographically distributed）。Cluster更像是将很多个电脑堆在一起做成一个“大电脑”。

![Distributed System](/assets/cluster_cloud.png)

##5 **Reasons** for Distributed System (FIPRE)

1.  Functional separation (e.g. Client Server) <br><br>
分布式系统可以将不同的功能分隔开，降低系统的耦合程度，方便维护。<br>

2.  Inherent distribution <br><br>
维持固有的分布属性。分为Information和People两方面。在不同的网页中，不同的信息是由不同的人来维护的 （Information），而在一些协同工作中，不同的人（如医生，工程师等）可以通过DS来完成作业 （People）。

3.  Power imbalance and load variation

4.  Reliability<br><br>
系统的可靠性。数据可以在多个节点上备份。

5.  Economies<br><br>
通过共享来降低资源的拥有成本(reduce cost of ownership)，如可以多人共用一个打印机进行作业。

##4 **Consequences** of DS (CHNI)
Concurrency, Heterogenerity, No global clock, Independent failures.
