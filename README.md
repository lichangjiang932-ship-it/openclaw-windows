# open-claw在Windows上安装指南

本仓库提供在 Windows 11  环境下安装和配置 OpenClaw 的完整教程，OpenClaw 安装、内部 API 配置等。

### 主要内容

#### 1.openclaw安装部署教程

##### 1\.安装npm

Windows 10 和 11 自带了包管理器 winget。你只需要打开 PowerShell（管理员身份），输入：



PowerShell

winget install OpenJS.NodeJS.LTS

在国内直接使用 npm 下载插件通常非常慢，建议在安装完 npm 后，立即在终端运行以下命令，切换到淘宝/阿里云镜像：



Bash

npm config set registry https://registry.npmmirror.com

在窗口中分别输入以下命令并回车：

##### 2\.检查npm安装是否成功

Bash

node -v

npm -v

如果看到类似 v20.x.x 和 10.x.x 的数字版本号，说明你已经成功下载并安装了 npm！

##### 3\.根据官方文档下载

\# Install OpenClaw

npm i -g openclaw



\# Meet your lobster

openclaw onboard



##### 4\.配置openclaw

###### 1.选择ai,配置api等，这里建议选择他们列表现有的模型，否者等会跑的时候会出现各种问题



###### 2\.选择想要连接的应用，我这里选择的是discord,因为我的whats和telegram对国内用户不太友好，总是出现各种问题

下载discord注册账号，建立服务器，查看服务器id,再在服务器里建立一个文字频道复制id(记住这两个id后面要用）

&nbsp;第一步：在 Discord 开发者后台创建机器人

访问门户：打开 Discord Developer Portal。



创建应用：点击右上角的 "New Application"，给你的机器人起个名字。

记住机器人的应用id

生成机器人用户：



在左侧菜单点击 "Bot"。



点击 "Reset Token"（或者第一次是 Copy Token），把这个 Token 存好，它是机器人的“身份证”，千万不要泄露。



开启权限（关键）：



在同一页面（Bot 标签下）向下滚动，找到 "Privileged Gateway Intents"。



勾选 "Presence Intent"、"Server Members Intent" 和 "Message Content Intent"。如果不勾选，你的机器人可能读不到消息。



第二步：将机器人拉入你的服务器

在左侧菜单点击 "OAuth2" -> "URL Generator"。



在 Scopes 中勾选 bot。



在下方出现的 Bot Permissions 中勾选权限（建议先勾选 Administrator 方便调试，之后再根据需求缩小范围）。



复制最下方的链接，在浏览器打开，选择你的服务器并点击授权。（以我的clash for windows为例，这里需要打开tun模式，在常规里面点击下载，地球变为绿色即可。如果不打开tun模式，discord的服务器可能不在线）

现在你的模型已经建立好了，下一步运行模型

openclaw gateway run

运行完后等待连接，连接上即可在discord发消息给openclaw指挥他，如果没反应，可以尝试私发给他，他会回复你Failed to start CLI: Error: No pending pairing request found for code: 8K6UHKQU，复制他发给你的数字，回到终端运行.\\openclaw pairing approve discord 你的数字。

最新改版似乎需要机器人id,在控制面板输入.\\openclaw config set providers.discord.applicationId "你的应用程序ID数字"

###### 3\.如果想换别的模型，可以在跑通后指挥openclaw,让他来修改
模型要选择国外版的模型，qwen一件配置即可，minmax分国内国外版，qwen也是，国内版限制贼多，glm最近太火，延迟太高，还可以白嫖英伟达模型，地址是：build.nvidia.com/models，可以免费白嫖英伟达模型，但是有请求限制，本人感觉该模型有点傻，只说话不办事


