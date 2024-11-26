## 简介

> [!summary] 导读
> 
> 在 VS Code 当中，可以使用 Ctrl+, 打开带有 UI 设置界面，可以在此设置常用的内容。但是，如果是要单独为一个工作区修改配置而不是全局用户，又该怎么办呢？

首先我们来扯一下什么是「全局用户配置」于「工作区配置」。「全局用户配置」就是 VS Code 对当前用户所保存的配置文件，一般在用户目录下面，在「工作区配置」没有对其进行重写的情况下，所使用的配置。「工作区配置」就要高「全局用户配置」一档，若有相同的键 VS Code 将会优先使用「工作区配置」而非「全局用户配置」。因此，好渴鹅建议将主题、颜色、动画、字体等对项目通用的设置保存在全局用户配置下，对运行命令、各种语言拓展的配置保存在工作区配置文件下。（VS Code 内 UI 设置界面保存的一般是全局用户配置，也可以切换，但是不好转移）

## 位置

- **全局用户配置**：Windows 系统下，该文件在 `C:/Users/用户/AppData/Roaming/Code/User/` 目录下；
- **工作区配置**：工作区文件夹的 .vscode 文件夹下。

**名称**：settings.json。

## 格式

配置文件的格式均为 JSON 格式，例如：

```json
{
  "launch": {
    "configurations": [
      {
        "name": "C++ debug (global)",
        "type": "cppdbg",
        "request": "launch",
        "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
        "cwd": "${fileDirname}",
        "preLaunchTask": "C++ compile"
      }
    ],
  },
  "editor.tabSize": 2,
  "C_Cpp.clang_format_style": "{ BasedOnStyle: Google, ColumnLimit: 0}",
  "code-runner.runInTerminal": true,
  "code-runner.executorMap": {
    "cpp": "cd $dir && g++ -Wl,--stack=0x10000000 -std=c++14 \"$fileName\" -o \"$fileNameWithoutExt\".exe && $dir\"$fileNameWithoutExt\".exe",
  },
  "terminal.integrated.defaultProfile.windows": "Command Prompt",
  "extensions.ignoreRecommendations": true,
  "terminal.integrated.enableMultiLinePasteWarning": false
}
```

JSON 格式很简单，基本上不需要额外进行学习。语法为：大括号保存对象，中括号保存数组。但是，在配置的时候简单的语句基本上不需要缩进，困难的语句可以在网上搜索了之后照葫芦画瓢。

## 拓展

几乎所有的拓展也会使用 JSON 格式存储其配置，大部分都存在 setting.json 里面。拓展会提供拓展专属的键，可以让你更好地贴合自身习惯去使用拓展。由于数量过多，在此不再阐述。

## 常用键值

以下记录常用的键值，可以帮助新手快速配置 Settings 文件：

1. **files.autoSave**：自动保存；
2. **editor.fontFamily**：编辑器字体；
3. **editor.fontSize**：编辑器字体大小；
4. **debug.console.fontFamily**：调试控制台字体；
5. **debug.console.fontSize**：调试控制台字体大小；
6. **terminal.integrated.fontFamily**：终端字体；
7. **terminal.integrated.fontSize**：终端字体大小；
8. **editor.tabSize**：Tab 的大小；
9. **editor.cursorStyle**：光标样式；
10. **editor.wordWrap**：折行样式；
11. **editor.cursorBlinking**：光标动画样式；
12. **editor.cursorSmoothCaretAnimation**：平滑插入动画；
13. **editor.formatOnPaste**：是否在粘贴是格式化；
14. **editor.formatOnSave**：是否保存时格式化。

## 依赖

~~Settings 文件的配置依赖 VS Code~~，关于 VS Code 的安装可以查看 [[软件/编辑器/VS Code/安装与使用]]。