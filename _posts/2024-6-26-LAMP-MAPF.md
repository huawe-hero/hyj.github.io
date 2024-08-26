---
layout: post
title: Adaptive Lifelong Multi-Agent Path Finding With Multiple Priorities（自适应终身多优先级多智能体路径规划）
description: >
  这篇文章介绍了一种名为LEB-LNS（Lifelong Evaluation Based Large Neighborhood Search）的算法，旨在解决终身自适应多智能体路径规划问题（LAMP-MAPF）。LAMP-MAPF问题要求智能体在变化的环境中动态接收和完成不同优先级的任务，并在有限的计算时间内找到路径以避免碰撞。
tags: [MAPF]
---
# Adaptive Lifelong Multi-Agent Path Finding With Multiple Priorities（自适应终身多优先级多智能体路径规划）
## 针对问题
这篇文章针对的是自适应终身多智能体路径规划问题（LAMP-MAPF），它在智能体路径规划领域中具有挑战性，因为它涉及到以下几个关键方面：

* 终身（Lifelong）：

    与通常的单次路径规划问题不同，终身路径规划问题要求智能体在达到目标点后，能够接收新的任务并重新规划路径。这要求算法能够适应连续变化的环境和任务需求。智能体在完成任务后，需要能够处理新分配的任务，而不是停留在原地。

* 自适应（Adaptive）：

    在实际应用中，路径规划算法需要在有限的计算时间内找到可行解，以避免计算超时。在保证计算效率的同时，算法还需要尽可能提供高质量的路径规划解决方案，避免路径冲突和不必要的延迟。


* 动态任务分配（Dynamic Task Allocation）：

    算法需要能够根据智能体的位置和任务的优先级动态地分配任务，确保任务能够高效地完成。
    
* 优先级考虑 （Priority Consideration）：

    在任务分配过程中，高优先级的任务会被优先考虑，并分配给距离最近或最合适的智能体。

## 解决方案
这篇文章提出的LEB-LNS（Lifelong Evaluation Based Large Neighborhood Search）算法针对终身自适应多智能体路径规划问题（LAMP-MAPF）设计的，它是在MAPF-LNS（Multi-Agent Path Finding with Large Neighborhood Search）算法的基础上发展而来的。MAPF-LNS主要用于解决标准的多智能体路径规划问题，即在给定的时间内找到所有智能体从起点到终点的无冲突路径。LEB-LNS针对的是终身自适应多智能体路径规划问题，这个问题不仅要求找到无冲突路径，还要处理智能体完成任务后的再任务分配，以及不同优先级任务的处理。LEB-LNS使用了以下方法：

* 继承MAPF-LNS基本框架。LEB-LNS算法继承了MAPF-LNS的基本框架和思想，都使用大邻域搜索来解决多智能体路径规划问题。

* 引入评估函数。LEB-LNS引入了一个基于γ的评估函数，这个评估函数不仅考虑路径成本，还考虑了不同优先级智能体的延迟和重要性，允许算法在搜索过程中给予高优先级任务更多的关注。

* 任务分配机制。LEB-LNS算法增加了任务分配的机制，当智能体完成当前任务后，会根据优先级和距离动态分配新任务。


## 仿真与实验
这篇文章通过一系列的仿真和实验验证了LEB-LNS算法在解决终身自适应多智能体路径规划问题（LAMP-MAPF）方面的有效性。

### 仿真验证
仿真在两种不同的地图上进行，一种是填充仓库（fulfillment warehouse）地图，另一种是分拣中心（sorting center）地图。在仓库履行地图上模拟了600个智能体，在分拣中心地图上模拟了400个智能体。
![fulfillment warehouse](/pictures/kiva.jpg "fulfillment warehouse")
![sorting center](/pictures/sorting.jpg "sorting center")
    
### 实验验证

* 实验场景：使用3个机器人在一个5米×8米的室内环境中进行实验，机器人由控制中心的PC进行管理。

* 硬件配置：PC配备了Intel i5-8265 U处理器和16 GB RAM，每个机器人由Jetson Nano控制。

* 软件环境：实验使用了Ubuntu操作系统和机器人操作系统（ROS）。

* 地图创建：使用Gmapping算法创建了实验环境的地图。

* 实验内容：
      优先级实验：验证算法在处理不同优先级智能体时的能力，观察高优先级智能体对低优先级智能体路径规划的影响。
      终身实验：模拟智能体完成任务后接收新任务的情况，验证算法在连续任务分配和路径规划中的性能。
      
## 论文发表
2024年6月发表于IEEE ROBOTICS AND AUTOMATION LETTERS（二区 IF5.5）。

