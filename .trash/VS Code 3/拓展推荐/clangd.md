## 拓展信息

用与 VS Code 的 C/C++ 自动补全、智能提示、静态检查插件，基于 LLVM。

## 细节

相比于 [[C／C++]] 插件来说，clangd 插件提供的 intellisense 会更加快速、智能，这点在 clangd 与 [[C／C++]] 的对比使用中体现尤为深刻。在输入代码的时候，[[C／C++]] 插件在检测错误时过于迟钝，而 clangd 非常快速；[[C／C++]] 的补全仅是将所有可能的匹配显现出来，而 clangd 可以补全源文件当中没有包含的头文件里的内容，这得益于 clangd 会将所有系统目录、工作目录下的源文件载入内存，在需要的时候快速补全并自动包含。因此，clangd 在使用的时候普遍内存占用较大。

关于 clangd 的安装可以查看 [[clangd 安装]]。

> [!attention] 注意
> 
> clangd 在 Windows 下使用时，默认不会扫描 GCC 的库，最好的方式是安装一个 MSVC（包含在 Visual Studio 内，安装详情参见 [[软件/IDE/Visual Studio/安装与使用|安装与使用]]）。