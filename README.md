## 学习 `workers-mcp` 笔记

今天开始学习 [workers-mcp](https://mcpbro.com/cn/mcp/cloudflare-worker-mcp) ，目标是让 Claude Desktop 可以和 Cloudflare Worker 交互。感觉挺有意思的，这样就可以用 Claude 来控制 Cloudflare 的一些服务了。

**第一步：生成一个新的 Worker 项目**

按照文档，首先要用 `create-cloudflare` 创建一个 Worker 项目。

```shell
npx create-cloudflare@latest my-new-worker
```

创建的时候，我选择了 `Hello World` 模板，先跑通最简单的流程。

**第二步：安装 `workers-mcp`**

进入到 Worker 的目录，然后安装 `workers-mcp`：

```shell
cd my-new-worker
npm install workers-mcp
```

**第三步：运行 `setup` 命令**

安装完之后，运行 `setup` 命令：

```shell
npx workers-mcp setup
```

跑完这个命令，我发现它好像做了一些配置，但是具体做了什么，我还不太清楚，之后要深入研究一下。

**第四步：迭代开发**

文档说，如果我们修改了 Worker 的代码，只需要运行 `npm run deploy` 就可以更新 Claude 里的函数信息和 Worker 实例。但是如果修改了函数名或者参数，需要重启 Claude 才能生效。

**遇到的问题：**

*   **命令找不到：** 在运行 `npx workers-mcp setup` 的时候，我一开始报错说 `workers-mcp` 命令找不到。后来发现，我忘记 `cd` 到 `my-new-worker` 目录里了。
*   **不确定 `setup` 做了什么：**  `npx workers-mcp setup` 命令执行后，我不太清楚它具体修改了哪些文件。下一步应该好好看看这个命令的源码，或者相关的文档。

**总结：**

目前为止，我只是完成了 `workers-mcp` 的基本安装和配置。下一步，我要尝试修改 Worker 的代码，然后看看 Claude 是否能够正确调用。另外，还需要研究一下 `setup` 命令具体做了什么，以及如何使用 `workers-mcp` 连接其他的 MCP 客户端。
