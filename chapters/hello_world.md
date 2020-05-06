# 写一个 Hello World

Deno 的多数 API 是完全和浏览器兼容的，比如： [`Console`](https://developer.mozilla.org/zh-CN/docs/Web/API/Console)，[`Fetch`](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API) 等等...

我们能够像在浏览器中写 JS 一样，来编写我们的 Deno 代码。

比如一个 Hello World：

*hello_world.ts*

```ts
console.log("Hello World!");
```

我们新建了一个 `hello_world.ts` 文件，并写入了以上代码。保存并从命令行中进入到这个文件的路径下，然后输入 `deno run hello_world.ts`

```sh
> deno run source/hello_world.ts
Compile file:///Users/username/deno-projects/lets_try_deno/source/hello_world.ts
Hello World!
```

我们可以看到控制台正常输出了 `Hello World!`，目前这和 `Node.js` 并没有很大区别。唯一的区别在于，Deno 直接支持运行 TypeScript 文件

## 执行远程 Hello World 程序

我们可以将我们的脚本放置在任何可以被正常访问的 Web 服务器上，Deno 能直接运行远程脚本。

比如我们在命令行中执行以下命令：

```sh
> deno run https://raw.githubusercontent.com/deno-china/lets_try_deno/master/source/hello_world.ts

Compile https://raw.githubusercontent.com/deno-china/lets_try_deno/master/source/hello_world.ts
Hello World!
```