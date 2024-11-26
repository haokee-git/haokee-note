##  信息

Jun Han 开发的快捷代码片段运行器。

## 细节

安装该拓展后，可以在编辑器的右上方找到三角形运行符号，点击即可。Code Runner 支持运行市面上大多数语言，包括：C, C++, Java, JavaScript, PHP, Python, Perl, Perl 6, Ruby, Go, Lua, Groovy, PowerShell, BAT/CMD, BASH/SH, F# Script, F# (.NET Core), C# Script, C# (.NET Core), VBScript, TypeScript, CoffeeScript, Scala, Swift, Julia, Crystal, OCaml Script, R, AppleScript, Elixir, Visual Basic .NET, Clojure, Haxe, Objective-C, Rust, Racket, Scheme, AutoHotkey, AutoIt, Kotlin, Dart, Free Pascal, Haskell, Nim, D, Lisp, Kit, V, SCSS, Sass, CUDA, Less, Fortran, Ring, Standard ML, Zig, Mojo。

需要注意的是 Code Runner 仅仅是通过编译脚本快速运行，编译器必须自行下载安装并将编译器的所在路径加入环境变量。另外，大多数语言都需要控制台输入来快速获取信息，可以在 Code Runner 的拓展设置里面勾选 Run in Terminal 即可在控制台输入信息，否则可能无法输入。

还有，若在编辑器内框选了代码片段，那么 Code Runner 会将代码片段保存到 tempCodeRunnerFile 文件并运行。可以在 settings.json（全局或项目）里面添加 "code-runner.executorMap" 项自行修改运行命令。