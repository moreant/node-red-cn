---
layout: docs-creating-nodes
toc: toc-creating-nodes.zh-CN.html
title: 创建你的第一个节点
slug: first node
permalink: docs/creating-nodes/first-node
lang: zh-CN
---

部署流时会创建节点，它们可以在流运行时发送和接收一些消息，并在部署下一个流时被删除。

它们由一对文件组成：

- 定义节点功能的 JavaScript 文件，
- 定义节点属性、编辑对话框和帮助文本的 html 文件。

package.json 文件用于将其全部打包为 npm 模块。

- [创建一个简单的节点](#创建一个简单的节点)
  - [package.json](#package-json)
  - [lower-case.js](#lower-casejs)
  - [lower-case.html](#lower-casehtml)
- [在 node red 中测试你的节点](#在-node-red-中测试你的节点)


### 创建一个简单的节点

此示例将展示如何创建一个将消息有效负载转换为所有小写字符的节点。
all lower-case characters.

确保您的系统上安装了 Node.js 的最新 LTS 版本。在撰写本文时，这是 10.x。

创建一个目录，您将在其中开发代码。在该目录中，创建以下文件：

- `package.json`
- `lower-case.js`
- `lower-case.html`

<h4 id="package-json"><i class="fa fa-file-o"></i> package.json</h4>

这是 Node.js 模块用来描述其内容的标准文件。

要生成标准 `package.json` 文件，您可以使用命令 `npm init`。
这将询问一系列问题，以帮助创建文件的初始内容，并尽可能使用合理的默认值。出现提示时，
将其命名为 `node-red-contrib-example-lower-case`。

生成后，您必须添加 `node-red` 部分：

```json
{
    "name" : "node-red-contrib-example-lower-case",
    ...
    "node-red" : {
        "nodes": {
            "lower-case": "lower-case.js"
        }
    }
}
```

这告诉运行时模块包含哪些节点文件。

有关如何打包节点的更多信息，包括命名要求和发布节点之前应设置的其他属性，请参阅[打包指南](packaging)。

**注意**：请**不要**将此示例节点发布到 npm！

<h4 id="lower-casejs"><i class="fa fa-file-o"></i> lower-case.js</h4>

```javascript
module.exports = function (RED) {
  function LowerCaseNode(config) {
    RED.nodes.createNode(this, config)
    var node = this
    node.on('input', function (msg) {
      msg.payload = msg.payload.toLowerCase()
      node.send(msg)
    })
  }
  RED.nodes.registerType('lower-case', LowerCaseNode)
}
```

该节点被包装为 Node.js 模块。该模块导出一个函数，当运行时在启动时加载节点时会调用该函数。使用单个参数 `RED` 调用该函数，该参数提供对 
Node-RED 运行时 API 的模块访问。

节点本身由函数 `LowerCaseNode` 定义，每当创建节点的新实例时都会调用该函数。它传递一个对象，其中包含在流编辑器中设置的特定于节点的属性。

该函数调用 `RED.nodes.createNode` 函数来初始化所有节点共享的特征。之后，特定于节点的代码就生效了。

在本例中，节点向 `input` 事件注册一个侦听器，每当消息到达节点时就会调用该事件。在此侦听器中，它将有效负载更改为小写，然后调用 `send` 函数在
流中传递消息。

最后，使用节点名称 `lower-case` 向运行时注册 `LowerCaseNode` 函数。

如果节点具有任何外部模块依赖项，则它们必须包含在其 `package.json` 文件的 `dependencies` 部分中。

有关节点运行时部分的更多信息，请参阅[此处](node-js)。

<h4 id="lower-casehtml"><i class="fa fa-file-o"></i> lower-case.html</h4>

```html
<script type="text/javascript">
  RED.nodes.registerType('lower-case', {
    category: 'function',
    color: '#a6bbcf',
    defaults: {
      name: { value: '' }
    },
    inputs: 1,
    outputs: 1,
    icon: 'file.png',
    label: function () {
      return this.name || 'lower-case'
    }
  })
</script>

<script type="text/html" data-template-name="lower-case">
  <div class="form-row">
    <label for="node-input-name"><i class="fa fa-tag"></i> Name</label>
    <input type="text" id="node-input-name" placeholder="Name" />
  </div>
</script>

<script type="text/html" data-help-name="lower-case">
  <p>
    A simple node that converts the message payloads into all lower-case
    characters
  </p>
</script>
```

节点的 HTML 文件提供以下内容：

- 在编辑器中注册的主节点定义
- 编辑模板
- 帮助文本

在此示例中，节点具有单个可编辑属性 `name` 。虽然不是必需的，但此属性有一个广泛使用的约定，以帮助区分单个流中节点的多个实例。

有关节点编辑器部分的更多信息，请参阅[此处](node-html)。


### 在 Node-RED 中测试您的节点

如上所述创建基本节点模块后，您可以将其安装到 Node-RED 运行时中。

To test a node module locally the [`npm install <folder>`]()
command can be used. This allows you to develop the node in a local directory and
have it linked into a local node-red install during development.

要在本地测试节点模块，可以使用 [`npm install <folder>`](https://docs.npmjs.com/cli/install) 命令。
这允许您在本地目录中开发节点，并在开发过程中将其链接到本地​​ node-red 安装。

In your node-red user directory, typically `~/.node-red`, run:
在您的节点红色用户目录（通常是 `~/.node-red` ）中，运行：

    npm install <location of node module>

例如，在 Mac OS 或 Linux 上，如果您的节点位于 `~/dev/node-red-contrib-example-lower-case` ，您将执行以下操作：

    cd ~/.node-red
    npm install ~/dev/node-red-contrib-example-lower-case

在 Windows 上你会这样做：

    cd C:\Users\my_name\.node_red
    npm install C:\Users\my_name\Documents\GitHub\node-red-contrib-example-lower-case

这将创建一个指向 `~/.node-red/node_modules` 中的节点模块项目目录的符号链接，以便 Node-RED 在启动时能够发现该节点。只需重新启动 
Node-RED 即可拾取对节点文件的任何更改。在 Windows 上，再次使用 npm 5.x 或更高版本：

<div class="doc-callout">
<em>Note</em> :  <code>npm</code> will automatically add an entry for your module in the
<code>package.json</code> file located in your user directory.  If you don't want
it to do this, use the <code>--no-save</code> option to the <code>npm install</code>
command.
</div>

<div class="doc-callout">
<em>注意</em>：  <code>npm</code> 将自动在位于用户目录的
<code>package.json</code> 文件中为您的模块添加一个条目。 如果您不希望它执行此操作，请使用
<code>npm install</code>命令的<code>--no-save</code> 选项。</div>

### 单元测试

为了支持单元测试，可以使用名为 [`node-red-node-test-helper`](https://www.npmjs.com/package/node-red-node-test-helper) 的 npm
模块。 test-helper 是一个基于 Node-RED 运行时构建的框架，可以更轻松地测试节点。

使用此框架，您可以创建测试流，然后断言您的节点属性和输出按预期工作。例如，要将单元测试添加到小写节点，
您可以将 `test` 文件夹添加到节点模块包中，其中包含名为 `_spec.js` 的文件

<h4 id="lower-casespecjs"><i class="fa fa-file-o"></i> test/lower-case_spec.js</h4>

```javascript
var helper = require('node-red-node-test-helper')
var lowerNode = require('../lower-case.js')

describe('lower-case Node', function () {
  afterEach(function () {
    helper.unload()
  })

  it('should be loaded', function (done) {
    var flow = [{ id: 'n1', type: 'lower-case', name: 'test name' }]
    helper.load(lowerNode, flow, function () {
      var n1 = helper.getNode('n1')
      n1.should.have.property('name', 'test name')
      done()
    })
  })

  it('should make payload lower case', function (done) {
    var flow = [
      { id: 'n1', type: 'lower-case', name: 'test name', wires: [['n2']] },
      { id: 'n2', type: 'helper' }
    ]
    helper.load(lowerNode, flow, function () {
      var n2 = helper.getNode('n2')
      var n1 = helper.getNode('n1')
      n2.on('input', function (msg) {
        msg.should.have.property('payload', 'uppercase')
        done()
      })
      n1.receive({ payload: 'UpperCase' })
    })
  })
})
```

这些测试检查节点是否正确加载到运行时，以及它是否按预期正确地将有效负载更改为小写。

两个测试都使用 `helper.load` 提供被测节点和测试流程，将节点加载到运行时。第一个测试检查运行时中的节点是否具有正确的 name 属性。第二个测试
使用辅助节点来检查该节点的输出实际上是否为小写。

帮助程序模块包含从 Node-RED 核心节点获取的其他测试示例。有关帮助程序模块的更多信息，请参阅相关的自述文件。
