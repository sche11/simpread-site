> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [forum-zh.obsidian.md](https://forum-zh.obsidian.md/t/topic/9626) ![](https://forum-zh.obsidian.md/user_avatar/forum-zh.obsidian.md/白术/90/5026_2.png)

在 Obsidian 中正确配置 Pandoc Plugin 插件，分为两个步骤：安装 Pandoc 软件和配置 Pandoc Plugin 插件。

安装 Pandoc 软件
============

下载 Pandoc 软件
------------

可以在 pandoc 的[官网 8](https://pandoc.org/installing.html) 进行下载，但是太慢了，有时还会下载出错。

我是在[这里 7](https://softmall.net/apps/1617) 下载的，在 Windows11 中测试有效。

安装 Pandoc 软件
------------

![](https://forum-zh.obsidian.md/uploads/default/original/2X/3/3c63d963815b0bc0fc6e5fe0729927aba90c2d7e.png)

配置 Pandoc Plugin 插件
===================

安装 Pandoc Plugin 插件
-------------------

在 Obsidian 第三方插件库里面搜索 “**Pandoc**” 安装

![](https://forum-zh.obsidian.md/uploads/default/original/2X/9/9bc65d61fa1a91cfaa52aa5060c9c79c2726a89c.png)

在 Pandoc Plugin 插件中进行设置
-----------------------

![](https://forum-zh.obsidian.md/uploads/default/optimized/2X/0/064a82fd1c66563c61b965fa6207ff9b96496ef5_2_690x130.png)

### Pandoc path

Pandoc 软件的安装路径**非常重要**

在文件管理器中复制得到的安装路径为：C:\Program Files\Pandoc，此时还要在后面加上 “pandoc.exe"，即安装路径为：C:\Program Files\Pandoc\pandoc.exe

![](https://forum-zh.obsidian.md/uploads/default/optimized/2X/0/0021ff4445f0b80dafdaf287005048a154bbcda3_2_690x145.png)

### Export folder

文件导出路径也要设置，这个没有多少注意的地方，只要有就可以了。

![](https://forum-zh.obsidian.md/uploads/default/optimized/2X/5/52744b657a4cf8aa20a6c007545610ef9af18e56_2_690x118.png)

### 测试导出文件

输入 Ctrl+P，调出命令面板，输入 **doc**，选择导出为. doc 文件。

![](https://forum-zh.obsidian.md/uploads/default/optimized/2X/8/8cded652589ac7c8c89b83b340ac8b9aec166a09_2_690x465.png)

### 测试结果

成功导出. doc 文件

![](https://forum-zh.obsidian.md/uploads/default/original/2X/3/33aa8a32f764e724c1bd926a72eceaab84c8a688.png)