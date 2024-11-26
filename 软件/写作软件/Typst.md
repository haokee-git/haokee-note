![[typst-ui.webm]]

> [!quote] 导读
> 
> Typst 是一种新的基于标记的科学排版系统。它旨在替代 LaTeX 等高级工具和 Word 和 Google Docs 等更简单的工具。我们对 Typst 的目标是构建一个功能强大且使用愉快的排版工具。

如果你对 $\LaTeX$ 复杂的语法感到晦涩难懂，对 Word 的协作性、版本管理感到堪忧，那么可以来尝试一下 Typst——这个新生的文档构建系统。它并不是完全为了取代 [[LaTeX]]，而是给文档编写者更多自由选择的权利。

## 安装

### 官网

目前，官网的 Typst 编辑器做得是最好的。它拥有智能的动态补全，可以方便地管理项目，而且在任意地方可以使用，不需要额外安装 Typst 编译器。

缺点便是，使用官网编辑对国内用户很不友好，访问速度不能保证，且编译速度有肉眼可见的延迟。

### 本地

在 [Typst 开源项目](https://github.com/typst/typst)（Github 的加速详见 [[Github 加速]]） 当中找到 Release 发布页面，下载最新的 Typst 安装器。

下载到本地后打开进行安装，然后将安装目录放入系统 PATH 环境变量当中。打开命令提示符，输入 `typst -v` 即可查看是否安装成功。

## VS Code 拓展

[[软件/编辑器/VS Code|VS Code]] 是一种热门的编辑器。像其它语言一样，Typst 也可以通过拓展在 VS Code 上提供对 Typst 的支持。需要注意的是，使用 VS Code 拓展需要首先安装 [[#本地]] Typst 编译器。

- **Typst LSP**：为 Typst 提供语言服务器，可以实现自动补全、静态检查等；
- **Tinymist Typst**：提供 Typst 的实时预览拓展（Typst Preview 以弃用）；
- **Typst Sync**：用于 Typst 本地包管理和同步的工具。