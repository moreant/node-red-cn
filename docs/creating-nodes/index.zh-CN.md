---
layout: docs-creating-nodes
toc: toc-creating-nodes.zh-CN.html
title: 创建节点
permalink: docs/creating-nodes/
lang: zh-CN
---

Node-RED 扩展的主要方式是将新节点添加到其调色板中。

节点可以作为 npm 模块发布到 [公共 npm 存储库](https://www.npmjs.com/) 并添加到 [Node-RED  流程库](https://flows.nodered.org) 
以使它们可供社区使用。

- [创建你的第一个节点](first-node)
- [JavaScript 文件](node-js)
- [HTML  文件](node-html)
- [打包](packaging)
- [节点属性](properties)
- [节点凭证](credentials)
- [节点外观](appearance)
- [节点编辑对话框](edit-dialog)
- [存储上下文](context)
- [节点状态](status)
- [配置节点](config-nodes)
- [帮助风格指南](help-style-guide)
- [添加示例](examples)
- [国际化](i18n)

_自 Node-RED 1.3 起_

- [在编辑器中加载额外资源](resources)
- [将子流打包为模块](subflow-modules)

### 一般指导

创建新节点时需要遵循一些一般原则。 这些反映核心节点采取的方法和帮助提供了一致的用户体验。

节点应该：

- **明确其目的。**

    暴露 API 的所有可能选项的节点可能不如一组各自服务于单一用途的节点有用。

- **无论底层功能如何，都易于使用。**

    隐藏复杂性并避免使用行话或特定领域的知识。

- **对它接受的消息属性类型保持宽容。**

    消息属性可以是字符串、数字、布尔值、缓冲区、对象、数组或空值。当遇到这些情况时，节点应该做正确的事情。

- **他们发送的内容保持一致。**

    节点应该记录它们添加到消息中的属性，并且它们的行为应该一致且可预测。

- **坐(sit)在流程的开始、中间或结束位置 - 不要同时出现在所有位置。**

- **捕获错误。**

    如果节点抛出未捕获的错误，Node-RED 将停止整个流程，因为系统状态不再可知。

    只要有可能，节点必须捕获错误或为它们进行的任何异步调用注册错误处理程序。
