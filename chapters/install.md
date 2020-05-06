# 安装/升级

Deno 运行时被编译为单一可执行文件，我们只需要将对应操作系统的可执行文件下载就可以运行，不需要像 Node.js 额外的从安装程序释放出可执行文件和依赖文件。

不过，为了便于快速根据操作系统下载对应正确的 Deno 可执行文件，Deno 官方提供了一个一键安装脚本。

## 安装最新版本

**通过 Shell 安装:**

```sh
curl -fsSL https://deno.land/x/install/install.sh | sh
```

等待脚本自动下载完成。然后能看到如下提示：

```sh
################################################### 100.0%
Archive:  /Users/username/.deno/bin/deno.zip
  inflating: deno
Deno was installed successfully to /Users/username/.deno/bin/deno
Manually add the directory to your $HOME/.bash_profile (or similar)
  export DENO_INSTALL="/Users/username/.deno"
  export PATH="$DENO_INSTALL/bin:$PATH"
Run '/Users/username/.deno/bin/deno --help' to get started
```

根据提示在 `~/.bash_profile` 中将环境变量配置好，就安装完成了。

**通过 PowerShell  安装:**

```powershell
iwr https://deno.land/x/install/install.ps1 -useb | iex
```

如果遇到 `请求被中止: 未能创建 SSL/TLS 安全通道` 的错误提示。只需要在执行安装脚本之前运行一下命令就可以正常安装：

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
```

**更多安装方式**

查看更多安装过程方式，可以参考 [https://github.com/denoland/deno_install](https://github.com/denoland/deno_install)

## 验证安装

在命令行执行 `deno --version` 如果安装成功，将会看到如下的 Deno 版本信息输出：

```
> deno --version
deno 1.0.0-rc1
v8 8.2.308
typescript 3.8.3
```

## 升级 Deno

因为 Deno 一直在不断开发，发版本的频率也比较高。如果我们要升级本地安装的 Deno 可以，重复上面的安装过程，将会覆盖安装最新版本

### 使用 `deno upgrade` 命令升级版本

我们可以使用安装脚本来升级安装 Deno，同时 Deno 本身提供了一个更方便的命令来帮助我们升级到最新版本

我们可以在命令行中输入 `deno upgrade` 就能方便的自动升级到最新版本

```sh
> deno upgrade
Checking for latest version
New version has been found
Deno is upgrading to version 1.0.0-rc1
downloading https://github.com/denoland/deno/releases/download/v1.0.0-rc1/deno-x86_64-apple-darwin.zip
downloading https://github-production-release-asset-2e65be.s3.amazonaws.com/133442384/f86bf880-8e43-11ea-971c-4fabd344ea89?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20200506%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20200506T093800Z&X-Amz-Expires=300&X-Amz-Signature=7dab378ee41b9a6d8c19b0ec9c8e9f0119596aa082afdd5cd91fe463e97e882f&X-Amz-SignedHeaders=host&actor_id=0&repo_id=133442384&response-content-disposition=attachment%3B%20filename%3Ddeno-x86_64-apple-darwin.zip&response-content-type=application%2Foctet-stream
Archive:  /var/folders/j4/k8b4sdr17jd81rj7l60m0n140000gn/T/.tmpgS0rFi/deno.zip
  inflating: deno
Upgrade done successfully
```