Github 是一个面向开源及私有软件项目的托管平台，也是世界上最大的代码托管平台。只支持 Git 作为版本库格式，因此名叫 Github。

Github 在国内是很难进行访问的，不管你的网络是百兆宽带还是万兆宽带，只要人品不好，就很难访问地很流畅。因此，好渴鹅便整理了这些关于如何加速 Github 的方式。

## Watt Toolkit

Watt Toolklit（别称瓦特工具箱，原名 Steam++）是一个包含多种加速服务的工具箱，其中就有 Github。打开[官网](https://steampp.net/)，点击下载自己系统对应的版本，然后安装就行了。安装之后点击网络加速页面，在平台加速里面勾上 Github，点一键加速就可以了。

> [!attention] 注意
> 最新版本的 Watt Toolkit 必须使用 Windows 10 以上操作系统才能运行。

## UsbEAm Hosts Editor

这个就是直接修改 Hosts 了。可能会比上面的 Watt Toolkit 的加速还要快一些，但是使用一段时间之后就可能会出现连接不上的问题。

首先，打开[官网](https://www.dogfight360.com/blog/475/)，找到下载位置，解压后打开解压的文件夹，双击可执行应用程序就可以打开页面了。

打开程序之后，点击左下角的按钮，找到开发者相关当中的 github.com 并点击，就可以看到有很多的 ip 可供选择。点击检测延迟，就会检测并排序，选择最上面的两个点击应用选中就行了。

事实上，很多时候延迟最靠前的 ip 选中之后可能出现无法连接的情况，这是很正常的，尝试后面几个就行了。如果经常出现这种情况，就需要重新测试延迟。

因此，Windows 10 及以上的系统就尽量使用 Watt Toolkit 吧。

## Github 520

这个也是基于修改 Hosts，但是是手动修改。官网页面在[这里](https://github.com/521xueweihan/GitHub520)，但是你都能上 Github 了还加速干吗？咳嗯，其实可以先去 [Gitee](https://gitee.com/inChoong/GitHub520) 修改完了再去 [Github](https://github.com/521xueweihan/GitHub520) 修改。

如何修改？在项目页面往下翻，就可以看到一大段的代码框，复制里面的所有内容，粘贴到系统 Hosts 文件的末尾就可以了。

系统的 Hosts 文件在哪里呢？Windows 在 `C:\Windows\System32\drivers\etc\hosts`，Linux 在 `etc/hosts`，需要打开管理员或 Root 权限修改。

然后重新打开 Github，大概率就能发现能够成功访问了。