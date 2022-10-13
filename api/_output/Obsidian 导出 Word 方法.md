> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.uncoverman.com](https://www.uncoverman.com/the-way-markdown-to-word-in-obsidian.html)

> Markdown 格式，只要接受了，就会爱上它。

[_Obsidian_](https://www.uncoverman.com/tags/Obsidian)[_Plugin_](https://www.uncoverman.com/tags/Plugin)

Markdown 格式，只要接受了，就会爱上它。虽然会有标记符号在其中，但是不开预览模式，基本也能障碍阅读。

但是对于普通人来说，直接看 md 文件并不友好。这时，我们会考虑，能否把 md 文件导出成为 Word 格式？

当然可以。

[](#Pandoc-软件 "Pandoc 软件")Pandoc 软件
-----------------------------------

Pandoc 的出现就是为了解决这个问题。它就是一把「瑞士军刀」，可以实现多种文本格式的相互转换，不仅可以把 md 文件导出为 Word，还可以导出为 PDF、ePub 甚至是 PPT，更多的格式转换可以查阅[官网](https://www.pandoc.org/index.html)。

使用方法是下载安装 Pandoc，通过以下的一个命令行就能实现文件的转换。

[](#Obsidian-集成-Pandoc "Obsidian 集成 Pandoc")Obsidian 集成 Pandoc
--------------------------------------------------------------

单独使用 Pandoc 需要用命令行操作指令，并不友好，我常常忘了具体的指令是什么，用到的时候需要上网搜一下。Obsidian 集成了 Pandoc，可以通过图形化的界面实现文本之间的格式转换。

具体步骤如下：

1、安装 [Pandoc](https://www.pandoc.org/installing.html) 软件。  
2、安装 Obsidian 的 Pandoc 插件。  
3、在 Obsidian 的 Pandoc 插件设置中配置 Pandoc path，即 Pandoc 程序的路径。Pandoc path 可以通过命令行工具获取。比如 `/opt/homebrew/bin/pandoc` 或者 `C:\Pragram Files\Pandoc\pandoc.exe`。

![](https://vip2.loli.io/2022/08/14/JjxDYoGy2zaFVIb.png)

![](https://vip2.loli.io/2022/08/14/K19763ctYDrbgN4.png)

4、完成配置之后，打开需要导出的文档，通过 `Command`+`P`（Windows 上是 `Ctrl`+`P`）调出命令面板，选择导出格式。

![](https://vip2.loli.io/2022/08/14/D1CgFNOkp4EhAVM.png)

[Previous: Weekly | 遗忘](https://www.uncoverman.com/weekly-4.html "Weekly | 遗忘") [Next: Weekly | 擦枪未走火](https://www.uncoverman.com/weekly-3.html "Weekly | 擦枪未走火")