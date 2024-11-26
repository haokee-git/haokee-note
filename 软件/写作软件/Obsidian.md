![[obsidian-ui.png]]

## 优点

Obsidian 是优秀的笔记软件，也使用 Markdown 语法。相比于 VS Code 来说，Obsidian 内置了很多新奇的功能；相比于 Typora 来说，Obsidian 有内置的插件市场，插件同样很多，可以进行高度个性化。新版也加入了所见即所得编辑模式，支持很多 Markdown 拓展语法。

## 缺点

云存档需要 €€£，所见即所得编辑模式体验感不如 [[Typora]]。

## 发布

当你在 [[软件/写作软件/Obsidian|Obsidian]] 里面编写完文档后，又该如何展览到网上/发布给别人看呢？根据现在的情况，好渴鹅总结出了三种比较靠谱的发布方式（好渴鹅自己已经尝试过了）。

### 官方发布

订阅官方的发布服务（按月订阅 10 美元/月，按年订阅 8 美元/月），然后在 Obsidian 内登入账号，打开官方核心发布插件，即可选择需要发布的内容、网站设置。

- **优点**：使用方式简单、不折腾；
- **缺点**：费用较贵。

### 导出页面部署

安装 Obsidian 插件 Webpage HTML Exporter，并使用命令将所有文档导出成可以部署的 HTML 格式，并上传到云服务器/静态网站托管服务内，即可展览。

- **优点**：导出免费，使用方式较简单；
- **缺点**：云服务器大多要付费，且导出有 bug。

### Digital Garden

通过 Digital Garden 插件将笔记托管在 Github 上，通过 Netlify 部署。

- **优点**：完全免费，接近官方发布；
- **缺点**：需要使用 [[Github 加速]]，且配置难。

## 自定义域名

适用于官方发布。

官方发布的功能已经非常完善了，在「发布」页面可以很详细地设置站点属性，也可以通过 publish.css 来自定义样式，但是对自定义域名支持并不良好。尽管官方已经在文档里面说明了自定义域名的步骤，但是好渴鹅仍然在配置域名的时候遇到了很大的困难，在此就分享配置过程。

首先，我们需要找一家域名提供商和域名服务商。这里建议直接使用官方推荐（也是保证一定能成功）的 [Cloudflare](https://www.cloudflare-cn.com/) 作为提供商/服务商，各项服务安排得明明白白，而且由于在国外不需要麻烦的实名认证和域名备案。

注册完用户之后，即可来到 Dashboard 页面。在左侧 Domain Registration 里面找到 Register Domains（登记域名，已经登记了的可以跳过这一步），搜索喜欢的名字，挑选一个通过信用卡或者是 PayPal 支付。

接下来回到 Dashboard，同样是 Domain Registration，点击 Manage Domain（管理域名），找到刚才注册的域名并点击 Manage，在右边 Quick actions 点击 Update DNS configuration，即可来到 DNS 解析记录页面。

在下方 DNS management for xxx 可以查看已生效的解析，或者是添加新的解析。我们点击 Add Record，Type（类型）选择 CNAME，Name 输入域名前缀，例如你的域名是 domain.com，想要让 www.domain.com 作为网站域名就输入 www，@ 表示根域名，即 domain.com。Target（目标）输入 Obsidian 官方文档里面要求输入的 publish-main.obsidian.md，注意不要有任何更改。然后将 Proxy status 打开，TTL 不变，点击 Save 即可。

接着我们点击左边的 SSL/TLS，看到右边的 SSL/TLS encryption，点击 Configure，将 Custom SSL/TLS 设置为 Full。（这一点非常重要，不然默认的 Flexible 会导致循环重定向）

然后打开我们的 Obsidian，打开发布，打开网站设置，点击自定义域名，在自定义 URL 里面输入刚才的域名，注意解析记录里面如果填了域名前缀的话也要加上，然后一路保存。

等待十分钟……不出意外地好了，如果没有成功可以顺着网线给我一巴掌。