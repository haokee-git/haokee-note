本文为 Kotlin 编译器的安装教程。关于 Kotlin 语言的信息可以查看 [[软件/编程语言/Kotlin|Kotlin]]。

## Windows

找到 [Kotlin 项目](https://github.com/JetBrains/kotlin)，打开 [Release 页面](https://github.com/JetBrains/kotlin/releases/tag/v2.0.21)，下载 kotlin-compiler-x.x.xx.zip（不要下载 kotlin-native，那是 Kotlin 原生而不是 Kotlin 编译器），解压，可以看到里面有个 bin 文件夹。

打开文件资源管理器，右键此电脑，点击高级系统设置，点击环境变量，点开系统变量 PATH，将刚才的 bin 文件夹的路径复制进来，然后一直确定。

接下来打开 cmd，输入 which kotlin。如果正确输出了 kotlin 的路径，则配置成功。

## Linux

以 Ubuntu 发行版为例。

```shell
$ sudo apt update  # 更新包管理器
$ sudo apt install default-jdk  # 安装 JDK，已经安装了的可以跳过
$ which java  # 查看 JDK 是否安装成功
$ sudo apt install snap  # 安装 Snap 包管理器，已经安装的可以跳过
$ sudo snap install kotlin --classic  # 安装 Kotlin
$ which kotlin  # 查看 Kotlin 是否安装成功
```

## macOS

使用 Homebrew 安装。

```shell
$ brew update  # 更新包管理器
$ brew install kotlin  # 安装 Kotlin
$ which kotlin  # 查看 Kotlin 是否安装完毕
```

## IntelliJ IDEA

[IntelliJ IDEA](https://www.jetbrains.com/idea/) 是由 JetBrains 开发的 Java/Kotlin/Scala IDE，可以说是 JVM 系语言开发界最好的 IDE 之一。众所周知，Kotlin 语言就是 JetBrains 开发的，因此安装 IntelliJ IDEA 就会自动安装 Kotlin（只是没有配置环境变量），先安装 [[JDK]] 就可以直接在 IntelliJ IDEA 里面创建 Kotlin 项目并使用了。