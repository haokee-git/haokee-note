> [!quote] 导读
> 
> 适用于 Linux 的 Windows 子系统 (WSL) 可让开发人员直接在 Windows 上按原样运行 GNU/Linux 环境（包括大多数命令行工具、实用工具和应用程序），且不会产生传统虚拟机或双启动设置开销。

## 详细信息

WSL 是适用于 Linux 的 Windows 子系统 (WSL) 是 Windows 的一项功能，可用于在 Windows 计算机上运行 Linux 环境，而无需单独的虚拟机或双引导。 WSL 旨在为希望同时使用 Windows 和 Linux 的开发人员提供无缝高效的体验。

- 使用 WSL 安装和运行各种 Linux 发行版，例如 Ubuntu、Debian、Kali 等。 [安装 Linux 发行版](https://learn.microsoft.com/zh-cn/windows/wsl/install)并从 [Microsoft Store](https://learn.microsoft.com/zh-cn/windows/wsl/compare-versions#wsl-in-the-microsoft-store) 接收自动更新、[导入 Microsoft Store 中没有的 Linux 发行版](https://learn.microsoft.com/zh-cn/windows/wsl/use-custom-distro)，或[构建你自己的定制 Linux 发行版](https://learn.microsoft.com/zh-cn/windows/wsl/build-custom-distro)。
- 将文件存储在独立的 Linux 文件系统中，具体取决于安装的发行版。
- 运行命令行工具，例如 BASH。
- 运行常用的 BASH 命令行工具（例如 `grep`、`sed`、`awk`）或其他 ELF-64 二进制文件。
- 运行 Bash 脚本和 GNU/Linux 命令行应用程序，包括：
    - 工具：vim、emacs、tmux
    - 语言：[NodeJS](https://learn.microsoft.com/zh-cn/windows/nodejs/setup-on-wsl2)、JavaScript、[Python](https://learn.microsoft.com/zh-cn/windows/python/web-frameworks)、Ruby、C/C++、C# 和 F#、Rust、Go 等。
    - 服务：SSHD、[MySQL](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-database)、Apache、lighttpd、[MongoDB](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-database)、[PostgreSQL](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-database)。
- 使用自己的 GNU/Linux 分发包管理器安装其他软件。
- 使用类似于 Unix 的命令行 shell 调用 Windows 应用程序。
- 在 Windows 上调用 GNU/Linux 应用程序。
- 运行直接集成到 Windows 桌面的 [GNU/Linux 图形应用程序](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps)
- 使用你的设备 [GPU 加速 Linux 上运行的机器学习工作负载](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gpu-compute)。

<div align="right">——微软官网</div>

## 启用

打开开始菜单，在开始菜单中输入「启用或关闭 Windows 功能」并打开，勾选「虚拟机平台」与「适用于 Linux 的 Windows 子系统」，然后重启。

重启后，打开终端，输入 `wsl --update` 即可安装依赖。

接下来安装系统（以 Ubuntu 为例）。打开 Microsoft Store，搜索 Ubuntu 并下载需要的版本。完成后，即可在开始菜单中启动。

## 使用

第一次开启进入 WSL 时，会进入创建用户界面。需要注意的是，Linux 终端在输入密码时密码字符是**不可见**的。输入完成之后就可以正常使用 Linux 终端了。

## 附加

- 默认的 Apt 镜像源下载速度过于抽象，因此可以替换成国内镜像源（如清华镜像源等），可以加快包的下载速度。具体可以查看 [Ubuntu | 镜像站使用帮助](https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/)；
- WSL 可以与主系统 Windows 共享文件，Windows 各个磁盘文件在 /mnt 目录下，而 WSL 系统内部的存储空间可以在 Windows 的文件资源管理器的左侧 Linux 文件夹内查看；
- WSL2 可以运行 Linux GUI 应用，可以通过 [使用 WSL 运行 Linux GUI 应用](https://learn.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps) 查看使用详情。

## 远程连接（SSH）

若有在 Linux 上构建应用的需求，但是不喜欢使用命令行编码，又不愿意折腾 GUI，那么可以使用 SSH 通过 Windows 上的文本编辑器（如 [[软件/编辑器/VS Code|VS Code]] 自带 SSH，安装详见）远程编辑 WSL 上的文件，再使用 WSL 编译出应用。具体操作推荐查看 [WSL折腾之旅 SSH远程连接 - 知乎](https://zhuanlan.zhihu.com/p/355748937)。

## 其它

如果想要在 Windows 运行除 Linux 外的其它系统，可能就需要使用虚拟机来运行了。如果的确有该需求，可以查看 [[VMware 虚拟机]]。