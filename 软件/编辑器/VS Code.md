## 下载与安装

> [!quote]  导读
> 
> Visual Studio Code（简称 VS Code）是 Microsoft 在 2015 年 4 月 30 日 Build 开发者大会上正式宣布一个运行于 Mac OS X、Windows 和 Linux 之上的，针对于编写现代 Web 和云应用的跨平台源代码编辑器， 可在桌面上运行，并且可用于 Windows，macOS 和 Linux。它具有对JavaScript，TypeScript 和 Node.js 的内置支持，并具有丰富的其他语言（例如 C++，C#，Java，Python，PHP，Go）和运行时（例如 .NET 和 Unity）扩展的生态系统。

![[vscode-ui.png]]

### 下载

首先打开[官网](https://code.visualstudio.com/)，点击 Download for Windows（或其它系统），它就会自动跳转到帮助页面并给你下载。如果没有下载的话，就点击[直接链接](https://code.visualstudio.com/sha/download?build=stable&os=win32-x64-user)。

### 安装

打开安装包，前面的随便选，C 盘不够的不要装 C 盘，推荐加入 Path 环境变量，这样子在命令行下输入 code 就可以直接打开 VS Code 了。

![[VS Code 官网.png]]

## 拓展

VS Code 最大的功能莫过于拓展功能了。在侧边栏里面，就可以看到拓展图标（最后一个），点击即可来到拓展页面。

进去以后，会默认展示已安装的所有拓展。当然，如果你是一个新手的话，那么这里就什么也没有。

底下会有一个推荐的页面，用来推荐比较热门的拓展的，不过没什么用。点击上面的搜索框，输入拓展名字，就可以搜索可用的拓展了。

搜索完之后，就可以看到罗列出来的拓展，点击安装就可以自动下载并安装，安装完之后也可以自由地禁用、卸载或更新，十分方便。

右上角有三个小点，点进去有一些功能配置。比较有用的是「从 VSIX 安装」，这样就可以在 VS Code 的拓展商店打不开的情况下直接下载拓展文件来安装。

如果你无法搜索到拓展，那么恭喜你，你 ~~中了玛莎拉蒂~~ 的 VS Code 成功变成离线般的了，只能使用 VSIX 安装。

### 拓展推荐

#### C/C++

##### 拓展信息

[Microsoft](http://www.microsoft.com) 微软官方 C/C++ 开发插件。

##### 功能

用来开发 C/C++ 源代码文件并编译、调试等一系列功能。

###### 智能感知

C/C++ 的智能感知引擎可以在写代码的时候帮你自动完成关键字、已定义类型、函数等，只需要你键入其中的一部分字母。它会根据其类型的不同标记上不同的图标以用与区分。

需要注意的是，C/C++ 默认提供的智能感知程序默认不会导入外部库的信息，只有当你包含了所属的库文件，它才会将库里面的内容读取进内存。

只能感知也会自动补全库文件的名称，只需要在 C/C++ 的配置页面填上所需库的目录即可，或是在环境变量中加入编译器的路径，C/C++ 拓展便会自动判断该编译器的类型，并找到标准库。

###### 静态检查

C/C++ 也默认集成了静态检查引擎，该引擎使用的是微软自行研究的 MSVC 的静态检查引擎，不依赖本地编译器，并贴心地为中国用户准备了中文信息。

静态检查会在你写代码的时候定期帮你找到代码的错误与潜在的危险。但是，C/C++ 的静态检查过于迟钝，如果追求更快的速度可以使用 clangd 替换此工作。

##### 运行与调试

C/C++ 自带了一套运行与调试配置，只需要打开一个工作区，按启动调试或以非调试模式运行，C/C++ 就会自动在 .vscode 目录下新建 tasks.json 与 launch.json 两个调试信息配置文件，并根据其内容启动调试。

需要注意的是，使用 C/C++ 自带的运行与调试功能不仅需要可用的编译器用与编译源代码，还需要 gdb 等调试器来完成调试操作，包括以非调试模式运行也是需要 gdb 的。

由于 gdb 无法在中文目录下工作，请检查你要调试的文件是否处于非中文路径下，不然 gdb 将无法工作。

##### 需求

需要安装任意一款 C++ 编译器，推荐 [[GCC]]。

#### Chinese (Simplified) Language Pack

第一次安装该拓展时，VS Code 会弹出窗口询问是否立即重启并切换语言。若在 VS Code 更新之后发现中文退回了英文（拓展未被卸载）的情况，可以按 Ctrl+Shift+P 打开控制面板输入 Configura Display Language，将其切换回中文即可。

#### clangd

##### 拓展信息

用与 VS Code 的 C/C++ 自动补全、智能提示、静态检查插件，基于 LLVM。

##### 细节

相比于 C/C++ 插件来说，clangd 插件提供的 intellisense 会更加快速、智能，这点在 clangd 与 C/C++ 的对比使用中体现尤为深刻。在输入代码的时候，C/C++ 插件在检测错误时过于迟钝，而 clangd 非常快速；C/C++ 的补全仅是将所有可能的匹配显现出来，而 clangd 可以补全源文件当中没有包含的头文件里的内容，这得益于 clangd 会将所有系统目录、工作目录下的源文件载入内存，在需要的时候快速补全并自动包含。因此，clangd 在使用的时候普遍内存占用较大。

关于 clangd 的安装可以查看 [[clangd]]。

> [!attention] 注意
> 
> clangd 在 Windows 下使用时，默认不会扫描 GCC 的库，最好的方式是安装一个 MSVC（包含在 Visual Studio 内，安装详情参见 [[Visual Studio]]）。

#### Code Runner

##### 信息

Jun Han 开发的快捷代码片段运行器。

##### 细节

安装该拓展后，可以在编辑器的右上方找到三角形运行符号，点击即可。Code Runner 支持运行市面上大多数语言，包括：C, C++, Java, JavaScript, PHP, Python, Perl, Perl 6, Ruby, Go, Lua, Groovy, PowerShell, BAT/CMD, BASH/SH, F# Script, F# (.NET Core), C# Script, C# (.NET Core), VBScript, TypeScript, CoffeeScript, Scala, Swift, Julia, Crystal, OCaml Script, R, AppleScript, Elixir, Visual Basic .NET, Clojure, Haxe, Objective-C, Rust, Racket, Scheme, AutoHotkey, AutoIt, Kotlin, Dart, Free Pascal, Haskell, Nim, D, Lisp, Kit, V, SCSS, Sass, CUDA, Less, Fortran, Ring, Standard ML, Zig, Mojo。

需要注意的是 Code Runner 仅仅是通过编译脚本快速运行，编译器必须自行下载安装并将编译器的所在路径加入环境变量。另外，大多数语言都需要控制台输入来快速获取信息，可以在 Code Runner 的拓展设置里面勾选 Run in Terminal 即可在控制台输入信息，否则可能无法输入。

还有，若在编辑器内框选了代码片段，那么 Code Runner 会将代码片段保存到 tempCodeRunnerFile 文件并运行。可以在 settings.json（全局或项目）里面添加 "code-runner.executorMap" 项自行修改运行命令。

#### Error Lens

##### 信息

一款能够使错误或警告更加显眼的插件。

##### 细节

Error Lens 提供的报错不同于 VS Code 的默认报错，是红色/橙色下划波浪线，不够显眼。Error Lens 插件则会将报错的那一整行全部高亮，并在行的末尾注上错误信息，这种设计方式不仅使错误更直观，还方便查看错误的原因。

#### GitLens

##### 信息

Gitlens 是一款由 [GitKraken](https://gitkraken.com/) 开发的适用于 VS Code 的高效源代码管理插件。

##### 细节

GitLens 对 VS Code 的 Git 功能做了很大的优化。

###### GitLens 页面

在左侧边栏里面找到 GitLens，点进去就可以看到 Git 以及 GitLens 的使用教程、云端补丁（需要 Pro）以及工作区预览（也需要 Pro）。

###### GitLens Inspect 页面

这应该算是一个功能信息集成最多的一个页面了。从上到下分别是：每一次提交的详细信息、AI 解释、时间线、文件历史以及可视化文件历史（需要 Pro）。

提交信息比较好解释，就是每一次提交更改了什么内容，删去了什么文件一系列的信息。AI 解释可以理解每一次提交造成了什么改变。时间线就是记录了所有提交的时间，让你看看你有多勤奋。文件历史就是存储了一部分文件的历史版本或历史提交信息。

###### 编辑器

GitLens 对 VS Code 的文本编辑器加入了 Git 集成。例如，当你的光标悬停在某一行的时候，他会在这一行的后面用灰色字体展示出这一行的上一次改变时间。你还会发现，在有些行号的旁边或中间，会有红绿蓝的标记，这就是记录了每一行的改变信息。点开来，就可以轻松看到当前行的上一个版本，也可以退回该版本。

#### Markdown Preview Enhanced

##### 信息

Markdown 预览器，

##### 细节

相比于 Markdown All in One 来说，其提供的预览模式功能更加丰富，有多种预设的主题可以使用，并且支持导出 pdf/html 等等其它格式的文件，支持自定义 CSS。

#### Office Viewer (Markdown Editor)

##### 信息

VS Code Office 文档格式预览器 & Markdown 所见即所得编辑器。

##### 细节

主要还是做 Markdown 编辑器使用。用多种主题，同样可以导出不同格式的文件。

#### Polacode-2022

##### 信息

Polacode 的改版，修复了原版中的若干 bug 并添加了一定的自定义选项。

##### 细节

Polacode-2022 是一个代码截图工具，只需要键入 Ctrl+Alt+P 打开命令面板搜索 Polacode-2022，并按下回车打开截图窗口，就可以开始截图了。

Polacode-2022 会自动监视你的光标选择，你只需要用鼠标在源代码当中框选一段想要截取的代码，Polacode-2022 就会记录下来并展示在窗口当中。点击窗口下方的彩色圆形按钮就可以保存代码截图。

同时，还可以再窗口当中设置截图设置，比如背景颜色、是否开启阴影等。此拓展可以用在多种环境下，如 Eva Theme 中的图片就是使用 Polacode-2022 截取的。

### 美化推荐

#### Catppuccin Perfect Icons

##### 信息

Thang Nguyen 出品的图标主题，颇有都市霓虹灯的感觉。

##### 展示

![[catppucin-icon.png#pic_center]]

#### Eva Theme

##### 信息

一款由 fisheva 出品的主题。

##### 展示

白色与黑色主题。

![[eva-light.png]]

![[eva-dark.png]]

#### Fluent UI for VSCode

##### 信息

Leandro Rodrigues 发布的一款用与 VS Code 的 Fluent UI 样式修改版。

##### 展示

与 Eva Theme Dark 版本搭配：

![[eva-fluent-ui-editor.png]]

![[eva-fluent-ui-themes.png]]

![[eva-fluent-ui-multi-editor.png]]