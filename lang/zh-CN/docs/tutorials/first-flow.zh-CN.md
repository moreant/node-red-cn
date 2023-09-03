---
layout: docs-tutorial
toc: toc-user-guide.html
title: 创建你的第一个流程
slug: first flow
redirect_from:
  - /docs/getting-started/first-flow
permalink: docs/tutorials/first-flow/
lang: zh-CN
---

### 概述

本教程介绍了 Node-RED 编辑器，并创建了一个演示注入、调试和函数节点的流程。


### 1. 访问编辑器

[运行](/docs/getting-started) Node-RED 后，在 Web 浏览器中打开编辑器。

如果你在同一台运行 Node-RED 的计算机上使用浏览器，你可以通过 url 访问它: <http://localhost:1880>。

如果在另一台计算机上使用浏览器，则需要使用运行的计算机的 ip 地址 Node-RED: `http://<ip-address>:1880`。

### 2. 添加一个注入(Inject)节点

通过单击节点上的按钮或设置注入之间的时间间隔，可以将消息注入到流中。

将其中一个从[调色板(palette)](/docs/user-guide/editor/palette/)拖到[工作区(workspace)](/docs/user-guide/editor/workspace/)上。

选择新添加的 注入(Inject) 节点，可以在[信息侧边栏(Information sidebar)](/docs/user-guide/editor/sidebar/info)窗格中查看有关其属性的信息以及关于它的操作的说明。

### 3. 添加调试(Debug)节点

“调试(debug)”节点可以做到在[调试窗口侧边栏](/docs/user-guide/editor/sidebar/debug)中显示任何消息。默认情况下，它只显示消息的有效负载，但也可以显示整个消息对象。


### 4. 将两者连接起来

通过在一个节点的输出端口与另一个节点的输入端口之间拖动，将 Inject 节点和 Debug 节点[连接在一起](/docs/user-guide/editor/workspace/wires)。

### 5. 部署

此时，节点只存在于编辑器中，必须部署到服务器。

单击 Deploy 按钮。

### 6. 注入

选中调试窗口侧边栏选项卡后，单击注入按钮(Inject节点旁边的小正方形按钮)。您应该会看到数字出现在侧边栏中。默认情况下，Inject 节点使用自 1970 年 1 月 1 日以来的毫秒数作为其有效负载。

### 7. 添加一个函数(Function)节点

函数节点允许您通过 JavaScript 函数传递每条消息。

删除现有的连接(选择它并在键盘上按删除键)。

在 Inject 和 Debug 节点之间连接 Function 节点。

双击 Function 节点，打开编辑对话框。将下面的代码复制到“函数”字段中:

{% highlight javascript %}
// 从负载中创建日期对象
var date = new Date(msg.payload);
// 将负载更改为格式化的日期字符串
msg.payload = date.toString();
// 返回消息以便可以继续发送
return msg;
{% endhighlight %}

单击“完成(Done)”关闭编辑对话框，然后单击“部署(deploy)”按钮。

现在，当您单击注入按钮时，侧边栏中的消息将被格式化为可读的时间戳。

***

### 总结

此流程演示了创建流程的基本概念。它显示了如何使用 Inject 节点手动触发流，以及 Debug 节点如何在侧栏中显示消息。

它还展示了如何使用函数节点来编写针对消息运行的自定义 JavaScript。


### 源码

本教程中创建的流程由以下 json 表示。要将其导入到编辑器中，请将其复制到剪贴板，然后将其粘贴到 导入(Import) 对话框中。


```json
[{"id":"58ffae9d.a7005","type":"debug","name":"","active":true,"complete":false,"x":640,"y":200,"wires":[]},{"id":"17626462.e89d9c","type":"inject","name":"","topic":"","payload":"","repeat":"","once":false,"x":240,"y":200,"wires":[["2921667d.d6de9a"]]},{"id":"2921667d.d6de9a","type":"function","name":"Format timestamp","func":"// Create a Date object from the payload\nvar date = new Date(msg.payload);\n// Change the payload to be a formatted Date string\nmsg.payload = date.toString();\n// Return the message so it can be sent on\nreturn msg;","outputs":1,"x":440,"y":200,"wires":[["58ffae9d.a7005"]]}]
```

### 下一步

 - [创建你的第二个流程](second-flow)

### 相关阅读

 - [使用编辑器](/docs/user-guide/editor/)
 - [核心节点](/docs/user-guide/nodes)
 - [使用消息 (message)](/docs/user-guide/messages)
 - [使用函数(Function)节点](/docs/user-guide/writing-functions)
