LLVM 是以 BSD 许可来开发的开源的编译器框架系统，其中包含了 C/C++ 编译器 clang 与 clang++。其对应的基于 LSP 的语法分析器功能很强大。如 [[软件/编辑器/VS Code|VS Code]] 中的 clangd 插件，就是使用的本地 clangd 程序。

## Linux

由于 clangd 依赖它的编译器 clang，因此需要事先安装 clang。安装完 clang 之后，再安装 clangd。本文使用的包管理器是 apt。

```shell
$ sudo apt install update  # 更新包存储库信息
$ sudo apt install clang  # 安装 clang
$ which clang  # 查看 clang 是否安装成功
$ sudo apt install clangd  #  安装 clangd
$ which clangd  # 查看 clangd 是否安装成功
```

## Windows

在 clangd 插件当中，可以输入 clangd: Download language server 就可以自动从 Github 下载。但是由于众所周知的原因，Github 一般都是连接不上的。

因此我们直接从 Github 下载 LLVM，网址：[https://github.com/llvm/llvm-project](https://github.com/llvm/llvm-project)（如果无法访问可以查看 [[Github 加速]]）。在右下角找到 Release 页面，点进去下载最新版（最好是 win64 安装器）。

下载之后双击安装器进行安装。记得将 `/安装目录/bin` 加入环境变量。

## 依赖（Windows）

在 Windows 下，clangd 默认使用 MSVC 库而非 GCC，因此在 Windows 下正常使用 clangd 还需要安装 [[MSVC|MSVC]]，不然会报错：找不到库/头文件。