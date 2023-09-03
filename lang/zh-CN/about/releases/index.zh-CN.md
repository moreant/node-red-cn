---
layout: about-single
title: 版本计划
slug: releases
permalink: about/releases/
lang: zh-CN
---

_更新时间: 2022-08-04_

该计划是项目计划如何安排即将发布的版本的指南，同时考虑到底层 Node.js 运行时的发布时间表。

![](release-plan.png)


活动的 Node-RED 流 (3.x) 将每三个月发布一个新的次要版本（例如 3.1 -> 3.2）。维护版本（例如 3.1.0 -> 3.1.1）将在需要时继续发布。

在2023年4月底，当 Node 14.x 到达生命周期的终点时，我们将发布 Node-RED 4.x，它将放弃对 Node 14的支持。

然后3.x 流将进入维护模式。它将只接收错误修复和安全更新。如果有一个非常好的理由，以及人们可以做的工作，新的特性可以从4.x 返回移植。

4.x 流程将继续积极开发，每三个月左右发布一个小版本，持续一年左右，直到下一个主要版本发布。

这项建议意味着:

 - 我们有一个定期的发布周期——把新功能交到用户手中。
 - 我们有一个时间表来帮助我们确定优先级和计划积压的项目。
 - 我们可以提供更长期的稳定释放与众所周知的生命结束。
 - 我们有一个计划，使我们能够作出潜在的突破性变化，每年一次。


版本     | 首次发布         | 维护开始              | 生命结束
--------|-----------------|----------------------|-----------------
1.x     | 2019-09-30      | 2021-04-30           | 2022-06-30
2.x     | 2021-07-22      | 2022-07-14           | 2023-06-30
3.x     | 2022-07-14      | *2023-04-30* *       | 2024-06-30
4.x     | *2023-04-30* *  | *2024-04-30* *       | 2025-06-30

_* 日期可能会更改_

参考文献:
 - [Blog post: Going beyond Node-RED 1.x 博客文章：超越 Node-RED 1.x](https://nodered.org/blog/2020/07/01/release-plans)
 - [Node-RED Release Plan source Node-RED 发布计划来源](https://docs.google.com/spreadsheets/d/1swMH5DXVposBIdnm6Q3BvIplMjAZSZVnU_cRS0jAPjY/edit)
 - [Node.js Releases Node.js 版本](https://nodejs.org/en/about/releases/)
