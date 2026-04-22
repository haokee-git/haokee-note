> [!abstract] 电子扫盲这一块
> 
> 最近，我利用闲置的 AI Studio Key 配合云服务器使用 New API 开源项目开了一个 [中转站](https://api.haokee.org/) 并免费提供给班上同学使用。同时，在为班上同学讲解使用 API Key 的方式时，我意识到班上同学对于这一块的了解程度太少。
> 
> 考虑到一个一个教培是不现实的，因此我写了这一篇简单的、实用的文章。

- [b] 本文图片均以我的中转站为例。但事实上，所有的 AI API 接入方式都是极其相似的。

## 获取 API Key

首先，要确保你的账户是有余额的，并且不要过低，否则根本无法使用。

![[{75689A73-A4B7-42A6-90A7-740578A6F4B9}.png]]

然后，在侧边栏找到令牌管理（或含有 Key、Token 等字样的），打开来。若你之前没有申请过 Key，这里应该是空的；如果非空且不需要申请新的，直接跳过这一章。

![[Pasted image 20260404161704.png]]

点击“添加令牌（或 API Key 等字样）”。

![[Pasted image 20260404161741.png]]

名称当中，填写一个有意义的就行了。分组是本中转站特有的设置，保持默认即可。过期时间自用的话就“永不过期”。其它的不用管，提交即可。

你可以申请多个令牌。所有的令牌本身无额度，都是共用的账户额度。如果后期你发现某个令牌使用情况异常，那很有可能是被盗用了。可以考虑通过删除来避免损失。

![[Pasted image 20260404162005.png]]

点击复制密钥即可。有些厂商为了安全，仅在申请时告诉你 Key 的具体代码。**此时必须将其保存下来，否则以后将无法再次看见密钥**。

## 接入聊天客户端

聊天客户端有很多，如 [ChatBox](https://chatboxai.app/zh/)、[Cherry Studio](https://www.cherry-ai.com/) 等等。此处推荐使用 [ChatBox](https://chatboxai.app/zh/)，因为它提供 Web 在线使用功能，无需单独下载软件。

打开官网，然后启动网页版。

![[Pasted image 20260404162823.png]]

进去之后，不要犹豫，直接点击左下角 Settings，（看不懂中文的在 General Settings 的 Language 那里改成简体中文），然后打开 Model Provider（模型提供商），根据你想用的模型类型选择具体提供商。例如：你想用 Gemini 就选 Gemini。

![[Pasted image 20260404163831.png]]

此时最重要的一步来了：将 API Host（API 主机）改成对应站点的名字。例如使用我的中转站，就将其改成 <https://api.haokee.org>；走官方 API 的不用改。

然后将刚才复制的 API Key 填入上方。

接着点击 Check（检查）按钮，选择任意一个（最好速度快）模型进行测试，看到成功提示即可。

![[{C7F27A01-1B40-420F-BC92-CF1D2B670514}.png]]

回到主页，即可享受聊天。记得在右下方切换模型。

## 接入 Coding Agent 客户端

如果你是官方 API，大部分 Coding Agent 客户端都是可以使用的；如果是中转 API，必须要可以切换 Base URL 的才能正常使用。

本文以 Cline 为例。这是一个 VS Code Coding Agent 插件，在插件市场上安装即可。

随后在侧边栏打开 Cline 主页面，选择 Bring my own API key 并 Continue，并在 API Provider 当中选择自己想要的模型对应提供商。中转 API 同理，但是需要改 Base URL。

![[{190D6999-292B-44B0-8168-6B5E383DDEF1}.png]]

接着填入 API Key。

对于中转 API，勾选 Use custom base URL 并填入中转站的 URL。

然后在下方选择模型、思考预算。其余内容按需设置。最后 Continue。即可来到真正的聊天界面。

（可选）点击右上角设置按钮并选择 General Settings，在 Preferred Language 当中选择 Simplified Chinese - 简体中文，否则对于语言一致性差的模型（如 Gemini 系列），可能会出现“给中文回复英文”的情况。