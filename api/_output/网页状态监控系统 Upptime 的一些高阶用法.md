> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.tjsky.net](https://www.tjsky.net/?p=456)

> 增加需要隐藏的内容

前言

最近有构建网页集群状态监视系统的需求，经过在网上的一通翻找，找到了这个十分有创意的开源项目： Upptime

利用 GitHub Actions 每隔一段时间检查网站访问情况，若不能访问就创建 Issues 来回报异常事件, 通过 GitHub Pages 生成服务状态的页面。

上一篇文章《用 GitHub Actions 搭建网页状态监控系统 Upptime》介绍了最基础的部署步骤，下边补充一点更高阶的用法吧

更多监视类型
------

upptime 不仅仅可以监视普通站点 http 状态，还有更多类型监控项目  
只需要按格式修改增加`sites`部分代码即可

### 一般 HTTP 状态监视 (GET 请求)

### 一般 HTTP 状态监视 (其他请求)

正常的请求方式都支持，比如 POST,PUT,DELETE

### TCP ping 状态监视

比如一些需要 cookies 认证的后台页面

### 自定义 Request body

比如一些需要登录的后台页面

### 自定义站点图标

监控状态页面内站点的图标，只需要给对应项增加 icon 参数即可

### 自定义状态代码

默认配置下，Upptim 会将除了 20X 和 30X 以外的状态代码都视为站点异常，但如果你需要将 40X，50X 等状态代码视为正常状态，可以指定状态代码，只需要给对应项增加 expectedStatusCodes 参数即可

### 自定义站点超时时间

默认配置下，站点响应时间超过 30 秒才会会视为超时，你可以自行指定超时时间，以监视网站的异常卡顿，只需要给对应项增加 maxResponseTime 参数即可

### 自定义返回内容监测

这个主要是用在某些会在网站异常时并不会抛出异常代码，而是通过其他措施返回 200 状态的定义提示网页。比如使用了某些奇怪的自定义 404，502 页面，前端会在后端异常时，返回正常自定义提示网页。  
（这种设计其实违背了网页开发标准，自定义异常页应该正确回报状态代码 + 提示信息，而不是回报 200 代码 + 提示信息）  
或者监测参数，key，是否过期（比如某个页面，已登录和未登录返回的内容不同，你想监控你的状态还在不在）只需要给对应项增加__dangerous__body_down 参数即可

隐藏监控站点地址, 请求参数
--------------

github 是个开源代码平台，这个仓库也是 Public 的，任何人都可以从 yml 文件内看到你的监控配置  
但有些时候，可能你想同时监控 CDN 后的状态和原站点状态，但又不想暴露源站的 IP，或则一些需要监控的页面需要携带认证信息才可以正常访问，你不想把认证信息公开。比如上边[自定义 Request headers](https://www.tjsky.net/?p=444#Request_headers "自定义Request headers")，[自定义 Request body](https://www.tjsky.net/?p=444#Request_body "自定义Request body") 中的一些请求参数

1.  在你 repo 的 Upptime 项目中，点击 【Settings】，展开左侧的【Secrets】，点击【Actions 】 点击【 New repository secret】  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920114206.png)
2.  增加需要隐藏的内容
    

– Name: 基本上可以随便写，比如`site_main`,`key01`  
– Value: 写域名或者需要隐藏的请求参数  
– 点击 【Add secret】

比如我想隐藏域名的情况下监视谷歌的网页  
– Name: `site_baidu`  
– Value: `https://www.google.com`  
– 点击 【Add secret】

比如我想隐藏 GET 请求中需要的 key  
– Name: `MY_API_KEY`  
– Value: `aabbccddeeff11ppooiiuu2233`  
– 点击 【Add secret】

3.  在 yml 文件中需要提及隐藏内容时，使用`$刚才设置的Name`替代。

比如我想隐藏域名的情况下监视谷歌的网页

比如我隐藏 GET 请求中需要的 key

这样其他人就无法看到你监视的到底是什么站点或者 API 的权限 key 了。

设置通知渠道
------

upptime 可以在监控项目无法访问或性能降级时给你发送通知  
在本文写作时支持，邮件（多种方式），短信（多种方式），Slack，telegram，Discord，Microsoft Teams

这里就以 SMTP 邮件和 telegram 为例（我默认你知道什么是 SMTP 邮件和 telegram bot 的设置）表格中汉字请替换为实际所指的内容。

### telegram

1.  在你 repo 的 Upptime 项目中，点击 【Settings】，展开左侧的【Secrets】，点击【Actions 】 点击【 New repository secret】  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920114206.png)
    
2.  添加以下 secret
    

<table><thead><tr><th>Name</th><th>Secret</th><th>备注</th></tr></thead><tbody><tr><td>NOTIFICATION_TELEGRAM</td><td>true</td><td>开启开关</td></tr><tr><td>NOTIFICATION_TELEGRAM_BOT_KEY</td><td>bot 的 API Token</td><td>可在 <a href="https://www.tjsky.net/goto/?url=https://t.me/BotFather" title="@BotFather">@BotFather</a> 查询</td></tr><tr><td>NOTIFICATION_TELEGRAM_CHAT_ID</td><td>你的 user ID</td><td>可在 <a href="https://www.tjsky.net/goto/?url=https://t.me/userinfobot" title="@userinfobot">@userinfobot</a> 查询</td></tr></tbody></table>

### Email

1.  在你 repo 的 Upptime 项目中，点击 【Settings】，展开左侧的【Secrets】，点击【Actions 】 点击【 New repository secret】  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920114206.png)
    
2.  添加以下 secret
    

<table><thead><tr><th>Name</th><th>Secret</th><th>备注</th></tr></thead><tbody><tr><td>NOTIFICATION_EMAIL</td><td>true</td><td>开启开关</td></tr><tr><td>NOTIFICATION_EMAIL_FROM</td><td>发信邮箱地址</td><td></td></tr><tr><td>NOTIFICATION_EMAIL_TO</td><td>收信邮箱地址</td><td></td></tr></tbody></table>

3.  添加以下 secret

<table><thead><tr><th>Name</th><th>Secret</th><th>备注</th></tr></thead><tbody><tr><td>NOTIFICATION_EMAIL_SMTP</td><td>true</td><td>SMTP 发信渠道开关</td></tr><tr><td>NOTIFICATION_EMAIL_SMTP_PORT</td><td>SMTP 服务器端口</td><td></td></tr><tr><td>NOTIFICATION_EMAIL_SMTP_HOST</td><td>SMTP 服务器地址</td><td></td></tr><tr><td>NOTIFICATION_EMAIL_SMTP_USERNAME</td><td>SMTP 登录用户名</td><td></td></tr><tr><td>NOTIFICATION_EMAIL_SMTP_PASSWORD</td><td>SMTP 登录密码</td><td></td></tr></tbody></table>