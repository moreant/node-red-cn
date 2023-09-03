---
layout: about-single
title: 关于
permalink: about/
lang: zh-CN
---

Node-RED 是一种基于流程的编程工具，最初由 [IBM 的新兴技术服务](https://emerging-technology.co.uk)团队开发，现在属于 [OpenJS 基金会](https://openjsf.org/)的一部分。

### 基于流编程

[基于流编程 (flow-based programming)](https://en.wikipedia.org/wiki/Flow-based_programming) 是由 J.Paul Morrison 在 20 世纪 70 年代发明的，它是一种将应用程序的行为描述为一个黑盒网络的方法，或者在 Node-RED 中称为“节点”的方法。每个节点都有一个定义良好的用途; 给它一些数据，它对这些数据做一些事情，然后将这些数据传递给下一个节点。

它是一个非常适合于可视化表示的模型，并使其更容易被更广泛的用户访问。

如果有人能够将问题分解成离散的步骤，那么他们就可以查看流并了解它在做什么; 而不必理解每个节点中的代码行。

### 运行时/编辑器

Node-RED 由一个基于 Node.js 的运行时组成，您可以通过 Web 浏览器访问流编辑器。在浏览器中，通过将调色板(palette)中的节点拖动到工作区(workspace)中并开始将它们连接在一起来创建应用程序。

通过安装社区创建的新节点，可以轻松地扩展节点面板，并且您创建的流可以轻松地作为 JSON 文件共享。

### 历史

Node-RED 于2013年初开始运作，是 IBM 新兴技术服务集团的 Nick O’Leary 和 Dave Conway-Jones 的一个副项目。

它最初只是一个用于可视化和操作 MQTT 主题之间映射的概念验证，但很快就变成了一个更加通用的工具，可以轻松地向任何方向扩展。

它于2013年9月开放源代码，此后一直开放开发，最终于2016年10月成为 JS 基金会的创始项目之一。

2019年，Node.JS 基金会与 JS 基金会合并成为 [OpenJS Foundation](https://openjsf.org/)。

<div class="doc-callout">
<b>为什么叫 Node-RED？</b>这个名字是对听起来像“红色代码('Code Red')”的单词的一个轻松的玩笑。它卡住了，是一个很大的改进，无论它是在最初几天。“ Node”部分既反映了流/节点编程模型，也反映了底层 Node.JS 运行时。

我们从来没有就 “RED” 部分代表什么得出结论。“快速事件开发人员”('Rapid Event Developer')是一个建议，但我们从未感到有必要将任何事情正式化。

<br>
我们坚持使用 “Node-RED”。

</div>

了解更多的历史和亮点:

- 阅读我们的博客文章，宣布[移动到 JS 基金会](http://nodered.org/blog/2016/10/17/js-foundation)。
- 观看 Nick 在 [Monki Gras 2016大会上的演讲](https://www.youtube.com/watch?v=Bbg1017amZs)：

<div style="text-align: center">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/Bbg1017amZs" frameborder="0" allowfullscreen></iframe>
</div>

### 引用 Node-RED

如果你需要在论文中引用该项目，请使用以下信息:

-----|----
**Name** | `Node-RED`
**Author** | `OpenJS Foundation & Contributors`
**URL** | If you are citing the project in general, use the project website URL - `https://nodered.org`. <br/>If you are citing a particular version, use either the website, or find the [release page on GitHub](https://github.com/node-red/node-red/releases) for the version you are citing.
