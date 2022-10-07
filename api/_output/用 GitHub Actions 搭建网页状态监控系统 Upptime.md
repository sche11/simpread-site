> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.tjsky.net](https://www.tjsky.net/?p=444)

> 点右上角的 【Settings】

**前言**

最近有构建网页集群状态监视系统的需求，难点主要在于有 20 多个站需要监控状态。  
收费的网页状态这个量级的套餐大都有点贵，免费的要么没有这个量级的套餐，要么自己搭建的步骤过于复杂。  
于是经过在网上的一通翻找，找到了这个十分有创意的开源项目： [Upptime](https://www.tjsky.net/goto/?url=https://github.com/upptime/upptime "Upptime")

利用 GitHub Actions 每隔一段时间检查网站访问情况，若不能访问就创建 Issues 来回报异常事件, 通过 GitHub Pages 生成服务状态的页面。

1.  访问 [Upptime](https://www.tjsky.net/goto/?url=https://github.com/upptime/upptime "Upptime") 项目
2.  点击 【Use this template】按钮  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920104706.png)
    

**注意：这是个模版项目，所以不要像常见的项目那样，去直接点右上角的 fork。**

3.  创建 repo  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920104943.png)

– 输入 Repository name（比如 upptime）  
– 勾选 【Include all branches】  
– 点击 【Create repository from temple】

4.  耐心等待几分钟，项目就会 fork 到你的账号下

![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920105430.png)

1.  进入你刚才 repo 到自己账号下的项目
2.  点右上角的 【Settings】
    
3.  在左侧 【Code and automation】 下找到 【Pages】
    
4.  将 【Branch】 设置为 【gh-pages】
    
5.  点击 【Save】
    

因为这个项目是利用 bot 实现自动化提交，需要给予 bot，commit 和 publish 的权限，所以我们需要设定一个 Personal Access Token

1.  点击网页右上角自己的头像，点 【Settings】  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920112402.png)
2.  点击左侧最下方的【Developer settings】  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920112346.png)
    
3.  点击左侧下方的【Personal access tokens】 ，点击左上角的 【Generate new token】新建一个 token  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920112318.png)
    
4.  新建 token
    

*   Note: upptime
*   Select scopes: 勾选【repo】和【workflow】（你直接勾 workflow，repo 就全勾上了）
*   Expiration：选【No expiration】（无期限）
*   点击页面最下方的 【Generate token】  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920112248.png)

5.  复制 token  
    注意一定要在这里复制好，错过这个页面你就再也看不到 token 了。  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/wp_editor_md_7893221186749f328692c8e4b19998c5.jpg)
    
6.  返回你 repo 的 Upptime 项目。点击 【Settings】，展开左侧的【Secrets】，点击【Actions 】 点击【 New repository secret】  
    ![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920114206.png)
    
7.  给 bot 设定 token
    

– Name: GH_PAT  
– Value: 上边第 5 步里复制的 token  
– 点击 【Add secret】

1. 回到你 repo 的 upptime 项目，点击【Code】，点击 【.upptimerc.yml】  
![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920115018.png)

2. 点击铅笔按钮编辑文件  
![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920115158.png)

3.  按照以下模版修改文件

4.  修改完成后在点击页面最下的【Commit changes】按钮，提交修改。

![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920122308-1024x419.png)

一般情况下，在你修改. upptimerc.yml 后，Actions 就会自动开始运行。  
你会看到一个黄圈圈在转。运行成功会显示绿色的勾，运行失败会显示红色的叉。  
如果出现红叉，一般都是你修改 yml 文件时，什么地方写错了，比如少打了一个字母啊，空格漏了啊，代码对齐有问题，少写了什么必须设置的参数，什么参数设置错误了。请仔细检查。

![](https://www.tjsky.net/wp-content/uploads/2022/09/20220920105430.png)

1.  进入你刚才 repo 到自己账号下的项目
2.  点右上角的 【Settings】
    
3.  在左侧 【Code and automation】 下找到 【Pages】
    
4.  `Your site is live at XXXXXX`这里就是你的监控状态页面啦
    
5.  Active Incidents 显示目前的异常事件，Live Status 显示目前监控状态，Past Incidents 显示过去的异常事件
    

把如下内容粘贴到. upptimerc.yml 的最后

*   upptime 可以实现的功能远不止于此，还可以实现 TCP 监视，监视网页内容，监视网页延迟，隐藏监控，自定义监控频率，自定义通知渠道（比如通过邮件，短信，telegram 机器人，webhook，Discord 发送异常通知）详情请查看后续文章[《网页状态监控系统 Upptime 的一些高阶用法》](https://www.tjsky.net/?p=456 "《网页状态监控系统 Upptime 的一些高阶用法》")
    
*   虽然理论上他是 5 分钟监控一次，但 github 大部分时间不允许这么短的间隔，所以实际会是每隔 10~20 分钟监控一次。