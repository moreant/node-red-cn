---
layout: docs-tutorial
toc: toc-user-guide.html
title: 创建你的第一个流程
slug: first flow
redirect_from:
  - /docs/getting-started/first-flow
---

### 概述

本教程介绍了 Node-RED 编辑器，并创建了一个演示注入、调试和函数节点的流程。

### 1. 访问编辑器
[运行](/docs/getting-started) Node-RED 后，在 Web 浏览器中打开编辑器。

如果你在同一台运行 Node-RED 的计算机上使用浏览器，你可以通过 <http://localhost:1880> 访问它。

如果在另一台计算机上使用浏览器，则需要使用运行 Node-RED: `http://<ip-address>:1880` 的计算机的 ip 地址。


### 2. 添加一个注入(Inject)节点

通过单击节点上的按钮或设置注入之间的时间间隔，可以将消息注入到流中。

将其中一个从[调色板(palette)](/docs/user-guide/editor/palette/) 拖到[工作区(workspace)](/docs/user-guide/editor/workspace/) 上。

选择新添加的 Inject 节点，可以在 [信息侧栏(Information sidebar pane)](/docs/user-guide/editor/sidebar/info) 中查看有关其属性的信息以及关于它的操作的说明。

### 3. 添加一个调试(Debug)节点

The Debug node causes any message to be displayed in the
[Debug sidebar](/docs/user-guide/editor/sidebar/debug). By
default, it just displays the payload of the message, but it is possible to
display the entire message object.

调试节点能够在[调试侧栏(Debug sidebar)](/docs/user-guide/editor/sidebar/debug) 中显示任何消息。默认情况下，它只显示消息(msg)负载(payload)，但是可以显示整个消息对象。

### 4. 将两者连接起来

通过在一个节点的输出端口与另一个节点的输入端口之间拖动，将注入节点和调试节点[连接在一起 (dragging between)](/docs/user-guide/editor/workspace/wires) 。

### 5. Deploy

At this point, the nodes only exist in the editor and must be deployed to the
server.

Click the Deploy button.

### 6. Inject 

With the Debug sidebar tab selected, click the Inject button (the small square button next to your inject node). You should see
numbers appear in the sidebar. By default, the Inject node uses the number of
milliseconds since January 1st, 1970 as its payload.

### 7. Add a Function node

The Function node allows you to pass each message though a JavaScript function.

Delete the existing wire (select it and press delete on the keyboard).

Wire a Function node in between the Inject and Debug nodes.

Double-click on the Function node to bring up the edit dialog. Copy the following
code into the function field:

{% highlight javascript %}
// Create a Date object from the payload
var date = new Date(msg.payload);
// Change the payload to be a formatted Date string
msg.payload = date.toString();
// Return the message so it can be sent on
return msg;
{% endhighlight %}

Click Done to close the edit dialog and then click the deploy button.

Now when you click the Inject button, the messages in the sidebar will now be
formatted is readable timestamps.

***

### Summary

This flow demonstrates the basic concept of creating a flow. It shows how the
Inject node can be used to manually trigger a flow, and how the Debug node displays
messages in the sidebar. It also shows how the Function node can be used to
write custom JavaScript to run against messages.

### Source

The flow created in this tutorial is represented by the following json. To import
it into the editor, copy it to your clipboard and then paste it into the Import dialog.


```json
[{"id":"58ffae9d.a7005","type":"debug","name":"","active":true,"complete":false,"x":640,"y":200,"wires":[]},{"id":"17626462.e89d9c","type":"inject","name":"","topic":"","payload":"","repeat":"","once":false,"x":240,"y":200,"wires":[["2921667d.d6de9a"]]},{"id":"2921667d.d6de9a","type":"function","name":"Format timestamp","func":"// Create a Date object from the payload\nvar date = new Date(msg.payload);\n// Change the payload to be a formatted Date string\nmsg.payload = date.toString();\n// Return the message so it can be sent on\nreturn msg;","outputs":1,"x":440,"y":200,"wires":[["58ffae9d.a7005"]]}]
```

### Next Steps

 - [Create your second flow](second-flow)

### Related reading

 - [Using the editor](/docs/user-guide/editor/)
 - [The Core nodes](/docs/user-guide/nodes)
 - [Working with messages](/docs/user-guide/messages)
 - [Using the Function node](/docs/user-guide/writing-functions)
