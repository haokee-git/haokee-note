> [!quote] 导读
> 
> Git 是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理。也是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。Torvalds 开始着手开发 Git 是为了作为一种过渡方案来替代 BitKeeper。

总之来说，Git 可以管理你或小或大的各种项目，并以简单的形式推送到一些网站（例如 Github 等）上面。

## 安装

### Windows

打开 Git 官网的[下载页面](https://git-scm.com/download/win)，点击下载 [64 位安装包](https://github.com/git-for-windows/git/releases/download/v2.45.1.windows.1/Git-2.45.1-64-bit.exe)（无法访问可以转到 [[Github 加速]]）。下载了之后就可以开始安装了，不懂的尽量不要乱动，直接默认就行了。

![[Git 官网.png]]![[下载链接.png]]

安装完之后在开始菜单打开命令提示符，并在里面尝试输入 `git`。如果发现命令行报错“未找到程序”那么应该就是还没有配置环境变量。

在文件资源管理器里面右键此电脑，打开属性，点击高级系统设置，打开环境变量，在系统变量里面找到 Path，将 `安装目录\cmd` 放进去，一路点确定，应该就可以了。

### Linux

```Shell
$ sudo apt update
$ sudo apt install git
```

## 基本操作

### 推送

首先，你需要准备一个文件夹，用来存放你的项目内容。在这个文件夹里面打开终端或者是 Git Bash，然后执行以下命令初始化 Git 本地仓库。

```Shell
$ git init
```

可以看到，这个项目文件夹下面多了一个隐藏的子文件夹 `.git`，也就是存放 Git 缓存的地方，没有必要不要乱动。然后我们需要将所有文件添加到 Git 的暂存区里面。

```Shell
$ git add .
```

`.` 就是当前目录下的所有文件，这里也可以填写文件夹或文件的名称。接下来我们就需要推送到网站上面了。我们需要配置用户名和，可以通过以下命令配置。

```Shell
$ git config user.name "用户名"
$ git config user.email "邮箱名"
```

配置完之后我们就要进行提交了。使用以下命令进行提交：

```Shell
$ git commit -m "提交信息"
```

然后，我们需要连接到远程仓库。考虑到最近各大网站都将默认分支更改为了 main，那么以下分支名都为 main。使用以下命令连接：

```Shell
$ git remote origin "git 位置"
```

一般 git 位置在网站上可以看到，例如 github（不知如何加速请转到 [[Github 加速]]）就是 `https://github.com/用户名/项目名.git`。然后使用以下命令推送到 main 分支：

```Shell
$ git push origin main
```

> [!attention] 注意
> 
> 如果推送失败了的话，很大概率是你之前没有拉取过，可以尝试拉取以下再推送。