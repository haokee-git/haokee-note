![[sublime-text-ui.png]]

## 简介

[Sublime Text](https://www.sublimetext.com/) 是一款轻量级的跨平台文本编辑器，自带对多种语言的语法高亮与简单代码补全。同 [[软件/编辑器/VS Code|VS Code]] 一样，Sublime Text 也有自己的插件市场，但是插件相对不多。

> [!attention] 注意
> 
> Sublime Text 其实是收费软件。在使用过程中会弹出弹窗提示购买，但是不购买也不会对功能造成任何损失。

## 汉化

Sublime Text 的默认界面是中文的，既不能在设置里面直接使用中文，也没有像 [[软件/编辑器/VS Code|VS Code]] 直接在侧边栏里面集成插件市场很方便地下载汉化插件。作为一个中国人，成天看着需要额外花费脑子算力的英文彩蛋算什么呢？因此我们需要对 Sublime Text 进行汉化。

实际上，Sublime Text 是有插件系统的，只是需要使用命令面板开启。按 Ctrl+Shift+P 打开命令面板并输入 Package Control: Install Package，然后就会开始下载，需要耐心等待。

过了一会，就会弹出一个消息框，点击即可打开插件市场。输入 Chinese，安装第一个插件。接下来重新启动 Sublime Text（关闭所有窗口并重新打开），并在菜单栏的 Help 最下面的 Language 里面勾选简体中文，即可。