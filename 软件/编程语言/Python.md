## 历史

### 起源

在上世纪八十年代末，荷兰程序员 Guido van Rossum 以简单、易读为目标创建了一门编程语言。由于他最喜欢的电视剧为《蒙提·派森的飞行马戏团》，因此该编程语言被命名为 Python。

1989 年，Python 项目开始开发。第一个公开版本 Python 0.9.0 于 1991 年被发布。

### 进化

凡事都需要进化，Python 也不例外。在多年间，Python 经历了数次迭代，最突出的是 Python 2 至 Python 3 的转变。Python 3 旨在丢弃 Python 2 的包袱，解决设计上的不足，因此没有考虑兼容 Python 2。Python 3 于 2008 年发布。

### 现在

Python 已成为主流的编程语言。Python 最特别的地方就是可以方便地管理第三方库，因此 Python 的第三方库生态正不在壮大。

Python 的应用非常广泛，包括 Web 开发、数据科学以及人工智能。

## 语言实现

Python 语言只是一个规范，不同的解释器可以采用不同的方式实现 Python。包括 [[C]]、[[C++]]、Java 等，甚至可以使用 Python 自身实现，如 Pypy。

一般来说，我们讨论的 Python 基本上都是指 [[CPython]]（使用 C 语言编写的 Python 实现），是标准 Python，也是最常用的 Python 实现。

另外使用较多的还有 [[PyPy]]，它是使用 Python 编写的。PyPy 最出众的点在于运行速度。它采用即时编译技术，可以提供更快地执行速度。但是 PyPy 与许多使用 C 编写的 Python 第三方库不兼容。

## pip 使用

pip 是 Python 的包管理器，使用 pip 可以快速、方便地安装第三方包并使用。高版本的 Python 大概率已经内置了 pip，如果在终端输入 `pip` 无法正常使用则运行安装脚本 [get-pip.py](https://bootstrap.pypa.io/get-pip.py)。

### 安装包

```shell
pip install package
```

例如，我想要安装包 pandas，则可以运行命令

```shell
pip install pandas
```

### 升级包

假设刚才安装的 pandas 包已经更新了，我想要更新它，则运行

```shell
pip install --upgrade pandas
```

### 卸载包

假设 pandas 我用不到，我该如何卸载呢？

```shell
pip uninstall pandas
```

### 列出包

此外，我们可以列出已经安装的所有包名称，方便查看是否安装完毕。

```shell
pip list
```

运行该命令将列出可以升级的所有包。