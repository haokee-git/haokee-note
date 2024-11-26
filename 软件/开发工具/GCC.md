> [!quote] 导读
> 
> GCC 是 GNU Compiler Collection 的简写，是为 GNU 操作系统开发的一款编译器，目前被大多数类 UNIX 系统（Linux、BSD、macOS等）采纳为标准的编译器。GCC 支持很多种编程语言，包括 C、C++、Fortran、Ada 等，并且包含了这些语言依赖的标准库。GCC 是按模块化设计的，可以加入新语言和新 CPU 架构的支持。GCC 是自由软件，任何人都可以使用或更改这个软件。

> [!tip] 提示
> 
> 注意：由于现在的 GCC 当中编译 C 的编译器是 gcc，编译 C++ 的编译器是 g++，因此在后面的安装教程当中可能会出现混用的情况，一般情况下没有关系，都能检测是否成功安装 GCC。

## Windows

Windows 下，GCC 的实现是 MinGW。

首先转到官方[下载地址](https://sourceforge.net/projects/mingw-w64/files/mingw-w64/mingw-w64-release/)或直接下载后面的安装包，然后一只向下翻找到 MinGW-W64 Online Installer，也就是在线安装器，但是不要点。继续往下翻到并下载 [x86_64-posix-seh](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-posix/seh/x86_64-8.1.0-release-posix-seh-rt_v6-rev0.7z)，下载就行了。

![[MinGW 下载.png#pic_center|50%]]

下完之后，打开压缩包，就能够发现里面有一个大文件夹叫做 mingw64。假设你把这个文件夹解压到 `C:\Program Files\` 目录下（没解压到这里也没关系），那么 `C:\Program Files\mingw64` 里面就会有很多文件夹，其中就有一个叫做 bin 的文件夹。把这个文件夹的路径包括这个文件夹自己复制下来。

然后右键此电脑，打开属性，打开高级系统设置，打开环境变量，在系统变量里面找到 Path，双击打开，新建一个，把刚才的路径复制进去，然后一路点确定。

在开始菜单栏或其它位置打开命令提示符，输入 `g++.exe -v`，如果输出出来了一大段版本信息，那么就是配置成功了；如果显示“未找到……”，那么就重新阅读一遍本文档试一下。

![[MinGW 安装检测.png]]

## Linux

Linux 下 GCC 一般都是默认安装的，在终端中输入 `gcc --version` 就可以判断。如果没有安装，那么可以使用如下命令极速安装。

```Shell
$ sudo apt install build-essential
```

然后继续使用 `gcc --version` 或 `g++ --version` 进行测试，应该就安装成功了。