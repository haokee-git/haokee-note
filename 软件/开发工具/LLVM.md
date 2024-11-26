> [!quote] 导读
> 
> LLVM 是构架编译器（Compiler）的框架系统，以 C++ 编写而成，用于优化以任意程序语言编写的程序的编译时间（compile-time）、链接时间（link-time）、运行时间（run-time）以及空闲时间（idle-time），对开发者保持开放，并兼容已有脚本。
> 
> LLVM 计划启动于 2000 年，最初由美国 UIUC 大学的 Chris Lattner 博士主持开展。2006 年 Chris Lattner 加盟 Apple Inc. 并致力于 LLVM 在 Apple 开发体系中的应用。Apple 也是 LLVM 计划的主要资助者。
> 
> LLVM 已经被 Apple、Microsoft、Google、Facebook 等各大公司采用。

LLVM 包含了许多不同语言的静态、动态编译器。对于我们 C/C++ 党来说，最诱人的不过是其中包含的 clang/clang++ 编译器了。

## 优势

相比于 g++ 来说，clang++ 的编译速度一流，而且拥有出色的错误提示输出，可以帮助开发者更快地找到代码种隐含的错误。clang 还有附属 clangd 语言服务器，许多自动完成提示工具都是基于 clangd 开发的。

clang++ 对语法的要求最为严格，在 clang++ 上能够通过编译的代码一般都可以在 g++/msvc 上通过编译。特别是 C++ 模板，clang++ 能够出色地在编译是抛出错误，且定位精准度非常不错。

## 安装

### Linux

#### 安装脚本

```shell
$ wget https://apt.llvm.org/llvm.sh
$ chmod +x llvm.sh
$ sudo ./llvm.sh 13
```

#### 预编译二进制

```shell
$ sudo mkdir -p /usr/local
$ cd /usr/local
$ sudo wget https://github.com/llvm/llvm-project/releases/download/llvmorg-13.0.1/clang+llvm-13.0.1-x86_64-linux-gnu-ubuntu-20.04.tar.xz
$ sudo tar xvf clang+llvm-13.0.1-x86_64-linux-gnu-ubuntu-20.04.tar.xz
$ sudo mv clang+llvm-13.0.1-x86_64-linux-gnu-ubuntu-20.04 llvm
$ export PATH="$PATH:/usr/local/llvm/bin"
```

#### 包管理器

```shell
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install clang
```

### macOS

```shell
$ brew install llvm```

### Windows

在 [LLVM 项目 Release 页面](https://github.com/llvm/llvm-project/releases)（需要加速可以看 [[Github 加速]]） 找到预编译好的 Windows 二进制包，下载到本地，然后打开安装包进行安装。

## Windows 未找到库

在 Windows 下仅安装 LLVM 使用 clang 编译程序时，可能会发生「未找到标准库」的问题。使用 `clang -v` 命令可以看到 clang 的 Target 默认是 x86_64-pc-windows-msvc，也就是 MSVC 的标准库。因此，我们需要安装 [[MSVC]] 的标准库来让 clang 使用。

如果不想安装 MSVC，并且本地已经安装好了 [[GCC]] 的话，可以将GCC 的 bin 目录放入环境变量，并在 clang 编译时加上选项 `-target x86_64-pc-windows-gnu`，即可使用 GCC 的标准库。