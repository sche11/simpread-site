> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/354650871)

> 前言题图是 LYT 作者的笔记库图谱截图 距离上一次的插件 推荐相关文章更新已经过去了三个月，三个月内 Obsidian 社区的插件翻了几番，从原来的二十来个变成了现在的129个，所以我从里面挑出我日常使用的插件与各位…

前言
--

题图是 LYT 作者的笔记库图谱截图

距离上一次的插件[推荐相关文章](https://zhuanlan.zhihu.com/p/308612160)更新已经过去了三个月，三个月内 Obsidian 社区的插件翻了几番，从原来的二十来个变成了现在的 129 个，所以我从里面挑出我日常使用的插件与各位分享一下，希望各位能从中获益。

### Search on Internet

**神器之二**，神器之一是 Note Refactor，关于 Note refator 的相关介绍可以去看以前的文章。Search on internet 利用 Obsidian 强大的 iframe 支持，实现了右键根据选中的关键词进行网络搜索的功能，当你设置了

```
https://www.google.com/search?&q={{title}}
```

其中的 `{{title}}` 为你选中的内容，然后启动这个搜索命令后，你可以快速地在 Ob 内部打开搜索页面（也可以在外部打开浏览器的搜索页面）。可以极大地加强你采用 Obsidain 拆书 / 研习的体验。

链接：[HEmile/obsidian-search-on-internet](https://github.com/HEmile/obsidian-search-on-internet)

### Note folder Autorename

功能简述：将笔记转换为文件夹，即你可以将这个笔记的相应的子笔记放在一个文件夹中，而文件夹本身就是一个笔记；类似 Onenote 的页面、子页面，你可以在页面的基础上构件子页面，也可以在子页面的基础上构件子子页面，十分方便。

链接：[pjeby/note-folder-autorename](https://github.com/pjeby/note-folder-autorename)

### Tag wrangler

当你需要对已经在很多文档中使用的标签进行更改的时候该怎么办呢？之前我们可以采用 BAT 脚本、python 脚本或者 AHK 脚本来对各个标签进行更改，但是这显然需要一定的编程基础，或者借用其他人已经写好的脚本实现，但是一旦遇到需要更改其中部分代码的情况，我们就开始寻求 Obsidian 内的插件解决方案了。在还没有全库替换功能的前提下，tag wrangler 可能是最好的标签更改替换应用。

当你安装了这个插件后，当你在你的标签栏上对一个标签右键式会出现新的操作命令，例如删除、重命名、将标签设置或不设置在搜索条件等；其中你采用重命名以后，全库内的所有同名标签都会被自动更改，十分方便。

链接：[pjeby/tag-wrangler](https://github.com/pjeby/tag-wrangler)

### Obsidian Query Language

当我们构件了一个 INDEX 页面，我们想要实时的了解自己的笔记的总数变化情况、最近的编辑笔记、最近创建的笔记、创建许久更改的笔记等等，我们不可能也不应该手动去做这些笔记的链接以及记录，于是我抱着只干最少的活的理念，找到了 Obsidian Query Language，这是一个为 Obsidian 而生的脚本语言。

当你采用下述的代码，在渲染界面就可以实时展示自己的笔记的数量了：

```
```oql
name: 我总共有
query:
    path: "'_Tempcard"
template: "string"
format: "{name}: {count} 个ZK笔记"
```
```

![](https://pic1.zhimg.com/v2-6a3ae878d2a4987ca58a868736317ef4_r.jpg)

利用插件自带的其它检索式，甚至能生成对应的表格：

```
```oql
name: Folder 1
query: "'_Tempcard" 
template: "list" # Renders to a list with notes linked
format: "{created}: {title}"
sort: 'created' 
limit: 10 # Limit it to the first 10
```
```

链接：[jplattel/obsidian-query-language](https://github.com/jplattel/obsidian-query-language)

### Obsidian dataview

如果你用完 Obsidian Query Language 后期待在 Obsidian 中更强大的 Query 甚至数据表功能，那你应该看一下 Obsidian dataview，它是目前 obsidian 插件社区中最具有潜力的插件，因为它已经开始展现出了一定的可视化变动表格的能力。

利用以下的查询语言：

```
```dataview
table time-played, length, rating
from "games"
sort rating desc
```
```

它可以生成一个简易但是展示良好的数据表：

![](https://pic4.zhimg.com/v2-128d52e2eb406645fcc5f48938edc953_r.jpg)

数据表中的数据基于你的笔记的 Frontmatter 中的数据，当你采用多个参数，也就是例如书籍评分、书籍年份、书籍类别来对每个笔记进行分类的话，那你可以很随意就获得一张很全面的书籍清单。

链接：[https://github.com/blacksmithgu/obsidian-dataview](https://github.com/blacksmithgu/obsidian-dataview)

### Journey

**神器之三**，我们总是会想要了解自己的笔记之间的联系，双链给了查看我们一个笔记与另一个笔记之间的机会，但是我们却无法快速地得到两个略显遥远的笔记之间的关系，如图，

![](https://pic3.zhimg.com/v2-f74e726aa6acb072bb68e5f9f84eae0a_r.jpg)

我们又要如何得知图中的两个箭头对应的笔记之间的关系呢，尽管图谱给了一个稍微可视化的途径我们，但是对于我们来说，文字描述显然更为具体。

而插件 Journey 恰好就是为了这个而生的，利用它，我们可以快速得到笔记与笔记之间的关系。

![](https://pic2.zhimg.com/v2-ee7420f18b6a92cc3f35bc89568cd669_r.jpg)

但我们输入笔记名（会自动建议）且查找后，我们就可以快速得到笔记与笔记之间的连接方式，有可能是通过标签、正向链接的笔记以及反向链接的笔记，而我们得到的结果也可以直接复制成带有链接的文字，方便我们点击查看；利用这个插件，很多彼此之间看似不可能有联系的笔记，都被一一串联了起来，最后，我们会得到自己的 WISDOM。

![](https://pic1.zhimg.com/v2-e8e733af94d07f3e96e35158d407e5c4_r.jpg)

链接：[akaalias/obsidian-journey-plugin](https://github.com/akaalias/obsidian-journey-plugin)

### Citations

当想要在 obsidian 中实践卢曼笔记法的话，我们总是会在制作文献卡片上遇到大大小小的问题，其中最关键的困难就是无法直接快速地引用对应的文献，为了解决这个问题，Obsidian 社区在先有人编写 Zotero 插件来加强 zotero 导出 markdown 效果，而在后，有人为 Obsidian 写了一个快速引用插件，名叫 Citations。Citations 插件可以加载你导出的文献信息 json 或者 bib，**如果你 Zotero 中安装了 betterbibtex 插件，那么当你导出整个文件夹的文献时，可以选择 Keep update 选项**，可以在你导入文献的同时更新对应的文献信息。

链接：[hans/obsidian-citation-plugin](https://github.com/hans/obsidian-citation-plugin)

### Markdown Formatting Assistant

对于习惯了 Word 或者其它具有可视化格式更改功能的人来说，一个浮动格式更改面板或者位于顶部的格式更改列显然是无法割舍的，当开始使用 Obsidian 后，这种不可割舍显然让他们陷入困境，但是，Markdown Formatting Assistant 正好就是将他们从这种困境中解救出来的良剂，如图所示，是 Markdown Formatting Assistant 支持的格式面板操作，当选中文本后，点击其中对应的格式符号，就可以快速对文字进行格式修正。

链接：[Reocin/obsidian-markdown-formatting-assistant-plugin](https://github.com/Reocin/obsidian-markdown-formatting-assistant-plugin)

### Recent Files

当库里的文件多了起来后，我们会经常陷入忘了上上个打开的文件是什么的困境，而 Obsidian 不会保持已经关闭的文件清单的跳转历史，所以你用返回上一个文件的方式经常会遇到无法使用的困境，对于有浏览打开文件历史需求的人来说，Recent files 就是他们的好帮手了。它的功能为展示最近的文件打开历史，可以解决一些人的痛点。

链接：[tgrosinger/recent-files-obsidian](https://github.com/tgrosinger/recent-files-obsidian)

总结
--

以上就是我推荐的全部插件，其中有一些插件是我在写笔记或者用 Obsidian 辅助学习的时候高频使用的插件，也帮助我构建起了属于自己的工作流，随着插件标准的越来越标准化，以及官方积极的支持，相信 Obsidian 的插件会越来越多，最后能通过各种不同的插件满足不同的人的特别需求，下次再见。