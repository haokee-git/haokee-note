> [!quote] 导读
> 
> Zed 是一款新的开源、使用 Rust 语言构建的编辑器，该编辑器以「以思维的速度编写代码」为卖点，通过开发人员自行编写的 gpui 库使用 GPU 进行渲染加速，并集成了 AI 功能，支持多种编程语言。开发人员是 [[Atom]] 编辑器与 [tree-sitter](https://github.com/tree-sitter/tree-sitter) 项目的原班人马，他们希望 Zed 能够成为未来的「终极编辑器」。

![[zed-ui.png]]

## 优势

相比于 [[软件/编辑器/VS Code|VS Code]]，Zed 明显地拥有着更好的性能；相比于 [[Notepad++]] 等轻量级编辑器，Zed 拥有更现代的外观与丰富的集成功能。

## 安装

理想很远大，实际好不好用需要安装了才知道。

### macOS

与其它编辑器不同，Zed 编辑器的大佬很显然有异于常人的大脑，最先选择支持的操作系统竟然是 macOS。在官网的 Download 页面可以下载安装包。

### Linux

Linux 系统在不久被支持。在终端运行以下命令即可安装：

```shell
$ curl -f https://zed.dev/install.sh | sh
```

### Windows

可惜的是，Zed 直至现在还没有官方支持 Windows 系统，但是我们可以从源代码编译得到 Windows 下的二进制可执行文件（编译后作者亲身试法发现除了拓展较少肥肠好用）。

访问 [Zed 的存储库](https://github.com/zed-industries/zed/)，克隆到本地，在项目路径下运行 `cargo build --release` 编译出可执行文件。在编译时需要下载几百个依赖，可能需要几十分钟，需要耐心等待。

编译之前确保安装了 CMake 并将其添加进环境变量、当前用户账户的名称为纯 ASCII 字符，否则会在编译的时候出现奇奇怪怪的问题。编译完之后，双击 /target/zed.exe 即可运行。

如果不想安装依赖自行编译，那么可以使用 [好渴鹅提供的已编译版本](https://www.123pan.com/s/OkLLVv-652BH)，已在最新 Windows 10 与 Windows 11 上能够正常使用，但是不确保所有版本都能打开。（需要用终端命令启动而不是文件资源管理器双击）

---

官方在 [文档](https://zed.dev/docs/development/windows) 中同样写到，我们可以安装 MSYS2，然后用 CLANG64 的 pacman 安装它。具体的，需要运行：

```shell
$ pacman -Syu
$ pacman -S $MINGW_PACKAGE_PREFIX-zed
```

接着就可以输入命令 zed 打开了。

## 缺陷

目前 Zed 在 macOS 上的稳定性已经非常良好，但是经过好渴鹅 Windows 实测仍然发现许多软件缺陷以及不完善的地方，如果你看到了不可接受的点，尽量暂时放弃 Zed。

- 老版本 Zed 会在使用过程中无缘无故闪退，不管什么情况（Windows 操作系统）；
- Zed 的 [[clangd]] 支持不完善，使用过程中可能会出现自动补全、静态分析突然消失的情况；
- Zed 使用 GPU 绘制图形，GPU 性能较差的机器会获得不好的 UI 体验；
- Zed 占用内存不算低，但是速度很快；
- 没有图形化设置界面，需要阅读官网文档并手动设置 JSON 配置文件；
- 没有调试配置，没有一键运行配置，需要手动敲命令；
- Zed 的插件市场插件较少，许多常用插件没有移植版本，这可能是 rust 开发难度较高再加上 Zed 这一款全新的编辑器使用的人不多。