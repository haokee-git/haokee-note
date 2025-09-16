![[hyper-v.png]]

## 启用 Hyper-V

首先，需要查看系统版本判断是否满足运行 Hyper-V 的运行需要。需要 Windows 10/11 的专业版或企业版，且 CPU 支持 VT-c，还要有具有二级转换的 64 位处理器。

检查满足要求之后，打开 PowerShell，并在里面输入如下命令：

```shell
PS> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

然后重新启动。接着打开控制面板，选择「程序」，选择「程序与功能」，选择「打开或关闭 Windows 功能」，选择「Hyper-V」然后确定。再次重新启动。

## 创建虚拟机

在开始菜单内找到 Hyper-V 管理器并打开，选择「操作」>「新建」>「虚拟机」，即可开启向导。首先为虚拟机取个名字，然后选择存储位置，接着选择虚拟机代系，然后选择内存，接着选择虚拟交换机，然后设置虚拟磁盘，接着选择操作系统映像，最后完成创建。