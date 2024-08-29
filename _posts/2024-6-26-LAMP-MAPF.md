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
在IEEE ROBOTICS AND AUTOMATION LETTERS上发表的论文《Adaptive Lifelong Multi-Agent Path Finding With Multiple Priorities》中，我们展示了仿真研究的成果。该研究中，智能体根据优先级（蓝色最高，黄色次之，红色最低）进行路径规划。每个智能体都被赋予了一系列任务，这些任务由一系列终点组成，智能体需要依次到达这些终点。在到达每个终点后，智能体会随机停留一段预定时间，然后继续前往下一个终点。一旦当前任务完成，智能体会被分配新的使命，确保其持续参与到动态的任务分配和执行过程中。

<iframe  src="//player.bilibili.com/player.html?isOutside=true&aid=113042952028776&bvid=BV1kKs5eaEk2&cid=25631461032&p=1"  scrolling="no"  border="0"  frameborder="no"  framespacing="0" allowfullscreen="true" width="80%"  height="500px"> </iframe>
### 实验验证
* 终身路径规划实验
机器人根据颜色旗帜的优先级（蓝色最高，黄色次之，红色最低）来规划它们的路径。每当机器人成功到达一个终点，它们就会被赋予新的任务，确保了任务分配的连续性和动态性。
<iframe src="//player.bilibili.com/player.html?isOutside=true&aid=113042968872164&bvid=BV1F3s5eFEYL&cid=25631589722&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="640" height="480"> </iframe>

* 多优先级路径规划实验
优先级红色旗帜>黄色旗帜>蓝色旗帜。
<iframe src="//player.bilibili.com/player.html?isOutside=true&aid=113042985648816&bvid=BV1cus5ehEyu&cid=25631657301&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="640" height="480"> </iframe>
优先级蓝色旗帜>黄色旗帜>红色旗帜。
<iframe src="//player.bilibili.com/player.html?isOutside=true&aid=113042985648614&bvid=BV1cus5ehEBo&cid=25631721773&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="640" height="480"> </iframe>
## 论文发表
2024年6月发表于IEEE ROBOTICS AND AUTOMATION LETTERS（二区 IF5.5）。

