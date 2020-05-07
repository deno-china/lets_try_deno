# Deno 模块系统

Deno 和 Node.js 其中一个最大的区别就是，Deno 采用分布式的模块依赖系统，和 Node.js 的 NPM 中心化模块系统不一样，Deno 不依赖某一个中心化的模块托管服务，如同浏览器，你依赖的 JS/TS 文件可以是随意分布在网络各处。就如同最初的前端页面，在 HTML 的 head 中通过 script 标签引入远程 JS 脚本。

例如我们可以直接引入远程模块

```ts
import { serve } from "https://deno.land/std@v0.42.0/http/server.ts";
const s = serve({ port: 8000 });
console.log("http://localhost:8000/");
for await (const req of s) {
  req.respond({ body: "Hello World\n" });
}
```

该代码片段直接引入了 `https://deno.land/std@v0.42.0/http/server.ts` 这个文件，而无需像 Node.js 一样从 node_modules 中引入需要通过 npm 包管理先下载安装好的模块。

看起来似乎是将我们带到了 “远古时代”，其实只是回归到了浏览器本身，Deno 是完全兼容现在浏览器的标准模块系统 `ESM`，

```html
<script type="module" src="https://domain/somewhere/module.js"></script>
```

**不必再忍受庞大的 node_modules 了**

![](../images/node_modules.png)

我们都知道，Node.js 在安装依赖的时候，会将整个依赖包所有文件下载下来。这会导致 node_modules 非常大。非常占磁盘空间，并且如果们使用 Node.js 交付服务端项目，将 node_modules 打包到 Docker 镜像中，也会使我们的镜像变得非常大。这是一件极其痛苦的事情。

> 注：snowpack 是个非常有意思的工具，可以极大的改善 node_modules 体积大的问题，并且 snowpack 也是致力于推动 esm 标准。

Deno 最小的依赖单元是**文件**，而 NPM 的依赖单元是整个包。就如同树叶和树枝：

Deno 的依赖单元

![Deno](../images/leaf.png)

NPM 的依赖单元

![NPM](../images/tree_branch.png)
