> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [forum-zh.obsidian.md](https://forum-zh.obsidian.md/t/topic/10622) ![](https://forum-zh.obsidian.md/user_avatar/forum-zh.obsidian.md/boninall/90/5_2.png)

前言
==

如果有人问 Obsidian 中让人着迷的是什么，也许有人说是 Obsidian 能让人感觉到自己的知识在联系的过程中发展，也许有人说是 Obsidian 能让人自由选择满足自己的工作流，但对我来说，它最让我感觉到沉浸的是它的折腾体验，从我用 Obsidian 到现在已经过去了两年半了，在这两年半里面，我也写了接近 20 篇关于各种插件的文章（一直在磨刀，从未停下来）以及接近十个 Obsidian 插件。

正如我之前写的一篇文章中写的是，折腾、折腾、折腾让我觉得很有趣，但是回到上文中提到的 “Obsidian 能让人自由选择满足自己的工作流”，这一点绝对是存在的。从我开始用 Obsidian 以来，我看过有人用 Dataview 搭建自己的论文笔记管理体系，也见过有人用 Quickadd 来搭建自己的快速记录工作流，还见过有人用 Kanban 来管理自己写作的素材，也见过有人用纯键盘流实现极客式的跳转以及快速浏览。

接下来，我将会跟你介绍，插件开放接近两年的这一天，我还保留了什么插件，以及为了解决什么需求写了什么插件，也希望你能从这堆插件中理解为什么我会装了那么多的插件。

以下是插件一览表：

```
url-into-selection
calendar
obsidian-footnotes
obsidian-hider
hotkey-helper
obsidian-hover-editor
obsidian-icon-folder
longform
obsidian-memos
obsidian42-brat
obsidian-pandoc
privacy-glasses
obsidian-query-control
quickadd
obsidian-quickshare
readwise-official
settings-search
templater-obsidian
obsidian-task-progress-bar
obsidian-table-generator
supercharged-links-obsidian
obsidian-style-settings
obsidian-spaced-repetition
obsidian-latex-suite
link-favicon
cmdr
obsidian-better-command-palette
customizable-menu
folder-note-core
obsidian-admonition
obsidian-banners
obsidian-dynamic-highlights
tag-wrangler
obsidian-bartender
obsidian-outliner
obsidian-minimal-settings
obsidian-toggle-list
pane-relief
ob-table-enhancer
obsidian-projects
obsidian-zoom
quick-explorer
obsidian-old-note-admonitor
obsidian-sakana-widget
obsidian-kanban
obsidian-linter
obsidian-another-quick-switcher
obsidian-dynamic-embed
obsidian-patent-retrieval-table
alx-folder-note
easy-typing-obsidian
obsidian-simple-time-tracker
obsidian-excalidraw-plugin
obsidian-dataview
obsidian-nldates
```

将分成强推插件（来自后续四个类别），外观美化类、编辑增强类、普通增强类以及特殊增强类。

强推插件
====

obsidian-dynamic-highlights
---------------------------

如果要我在 Obsidian 中找一个最不可缺少的插件，这个插件估计是第一，由 NothingisLost 带来的高亮插件，在我的主业中起到了无可替代的高亮作用，而且支持设置正则表达式匹配字符的高亮样式，甚至你可以在你希望的字符前边加上一个 icon 来标注这个字符的特殊性。

obsidian-hover-editor
---------------------

即使现在出现了独立窗口功能，这个插件依旧是无法替代的，因为它实现了预览编辑的功能，而且你可以在同一个窗口中摆入多个面板来进行同时的编辑或者预览；如果说多窗口相当于多个桌子，那么 Hover Editor 就相当于在桌子上平铺的方案。

obsidian-projects
-----------------

这个插件是目前我见过在 Obsidian 中实现的可编辑数据库（基于文件夹）/ 可视化 Dataview 最优雅的插件，完毕。

obsidian-another-quick-switcher
-------------------------------

在更新了八个大版本后，这个插件已经成为了功能性最强的可视化切换器插件（截止 2022-10-05），没有之一。只要你希望在 Obsidian 中快速切换别的笔记或者别的标题项，这个插件就是你的最佳选择。

obsidian-better-command-palette
-------------------------------

更好而且更舒服的命令面板插件，可以设置常用命令，而且也可以隐藏命令；还能采用一些特殊的搜索符来搜索文件或者标签，如果不用 another quick switcher 的话，这个插件也能充当一定的切换器插件使用。

cmdr
----

原名为 Commander ，以统一了右键菜单、侧边栏、状态栏、顶部栏以及页面菜单中的所有自定义化插件的图标以及命令设置的问题。首推的插件之一。

obsidian-linter
---------------

格式规整类插件，对于有笔记格式规整要求的用户来说是一个绝对不应该错过的插件。

obsidian-latex-suite
--------------------

今年新增的首推插件，它的功能绝不仅仅限定于 LaTeX 的快速输入，它可以让你体会到最无感的字词替换功能，后续也许会写一篇文章专门介绍一下这个插件（对重复的工作真的非常好用）。

* * *

外观美化类
=====

obsidian-hider
--------------

隐藏界面元素，尤其方便小屏用户，可以隐藏下方特别长的 Status bar。历经一年以后，我依旧保留了这个插件，而且它的隐藏功能也相比去年增多了几个，包括但不限于 0.16 中的标题栏的隐藏等。

obsidian-icon-folder
--------------------

在文件夹的前方加上图标，用于标识特定的文件夹等。对于长期不会变更的文件夹结构来说，是一个很不错的插件。

privacy-glasses
---------------

历经一年，这个插件依旧被保留了下来，当然也是方便我在直播或者录像的时候可以保留隐私。

supercharged-links-obsidian
---------------------------

这个插件从去年的 “用于快速更改 Obsidian 中的笔记的 YAML 属性。” 变成了更纯粹的修改内部链接的 icon 的插件了，现在它支持反向链接面板、标题栏以及文件栏的文件单独 icon 修改，而且是根据你设置的特定的规则进行修改的，例如你设置所有的写作笔记都在前边加上某一个指定的 icon 之类。

link-favicon
------------

这个插件是今年新增的一个插件，作用就是提供外部链接的 icon，例如 github 相关的链接的前边加上一个章鱼猫 icon。

obsidian-style-settings
-----------------------

用于修改部分插件和部分主题的相关设置，历久弥新的一个插件。

obsidian-admonition
-------------------

在 Obsidian 中插入很好看的标识文本，写过相关的文章：[Obsidian 插件之 Admonition - 知乎 6](https://zhuanlan.zhihu.com/p/391252867)；在 Callout 功能出来以后，这个插件逐渐变成了单纯的插入 Callout 的更方便的插件。

obsidian-banners
----------------

在 Obsidian 笔记预览后展示头图，或者在所见即所得中展示头图，这个插件就是单纯的美化了。

obsidian-minimal-settings
-------------------------

Minimal 主题的设置插件，仅面向 Minimal 主题；如果不用这个主题的话，可以不用这个插件。

obsidian-sakana-widget
----------------------

我写的一个 Lycoris Recoil 挂件移植插件，单纯是为了写东西的时候有个东西可以玩一下。

obsidian-simple-time-tracker
----------------------------

最近新增的一个简单的计时器插件，很简单，但是也很方便。

* * *

编辑增强类
=====

url-into-selection
------------------

当你的剪切板中存在 URL，而且你选中了一段文字后在粘贴的话，你就可以自动将其转化为 `[](URL)` 这样的格式。

templater-obsidian
------------------

模板？增强插件，可以做到一切可以用 JS 实现的功能的模板插件，在两年多的发展中已经证明这个插件的实力了。

quickadd
--------

新一代的快速裁剪、添加或命令顺序执行插件，之前写过相关文章：[Obsidian 插件之 QuickAdd - 知乎 7](https://zhuanlan.zhihu.com/p/386885976) 。一年多过去了，这个插件已经成为了我日常生活中不可或缺的插件之一。

obsidian-table-generator
------------------------

我写的一个表格增强类插件，方便你一次过生成需要的行、列的表格，类 Typora 的效果。

ob-table-enhancer
-----------------

中文社区用户写的一个表格编辑插件，可以直接在所见即所得的表格中进行内容编辑。

easy-typing-obsidian
--------------------

和 linter 插件在某种形式上类似，但是 Linter 可以对多个笔记同时进行格式规整，而这个则是专注于规整当前笔记。同时提供了大量的方便中文用户输入体验的功能，可以说是经常写东西不应该错过的一个插件。

obsidian-footnotes
------------------

便于快速跳转到 Footnote（脚注），利用这个插件你可以有更好的脚注编辑体验（主要体现在快速跳转到脚注后又能快速跳转回原文）。（因为和上一年的功能没有任何的区别所以就不重复说明了。）

obsidian-outliner && obsidian-zoom
----------------------------------

增强 Obsidian 的大纲体验，方便操作大纲。

obsidian-toggle-list
--------------------

用于快速切换当前任务的状态，而且仅在你需要的循环中循环，而不是在很多个命令中循环。

* * *

普通增强类
=====

calendar
--------

日历插件。

obsidian-pandoc
---------------

增强 Obsidian 的导出体验，可以利用 Pandoc 导出 docx、LaTeX 等文件。

obsidian42-brat
---------------

专门用来下载社区还没上架的插件。

settings-search
---------------

用于在设置面板上直接搜索设置。

obsidian-query-control
----------------------

用于提供更多的 Query 控制项，同时提供了黑魔法支持反链面板以及搜索面板的 Markdown 渲染。

obsidian-task-progress-bar
--------------------------

用于查看当前的任务完成的进度条。

tag-wrangler
------------

这是一款用于快速更改标签的插件（PJ 佬开发），你安装后只需要在标签列表上的标签右键就会出现更改选项。

quick-explorer
--------------

曾经写过一条关于这个的想法：[Quick explorer 3](https://www.zhihu.com/pin/1419624869260222464)，和 0.16.0 的 inline title 实现了非常好的联动。

obsidian-bartender
------------------

用于隐藏需要偶尔出现的状态栏或者侧边栏命令，和 Mac 上的 Bartender 软件功能类似。

pane-relief
-----------

这是一款用于快速更换当前专注的页面的插件（PJ 佬开发），你安装后只需要用快捷键就可以快速切换你的页面，在 0.16 中实现了非常有趣的联动。

folder-note-core && alx-folder-note
-----------------------------------

实现类似首页 Kanban 的视图；但是很久不更新了。

readwise-official
-----------------

用于同步 Readwise 上标注的内容，不可或缺的插件之一。

obsidian-old-note-admonitor
---------------------------

用于提醒当前的笔记你多久没更新了。

hotkey-helper
-------------

用于快速在设置面板中修改快捷键。

* * *

特殊功能类
=====

obsidian-spaced-repetition
--------------------------

间隔复习插件，用于在 Obsidian 中实现间隔复习。

obsidian-quickshare
-------------------

用于在 Obsidian 中快速发布你的笔记，免费而且可以只分享单篇笔记。

obsidian-memos
--------------

这是我写的一个类 Flomo 插件。

longform
--------

用来组织小说文本的插件，我已经用它写完小说了（），体验良好，但是写完发现自己逻辑错了。

obsidian-kanban
---------------

即使最近我很少用这个插件了，但是还是无法否认它是真的好用，如果你要找一个最简单而且少标记符的本地 markdown 看板，那就这个吧。

dataview
--------

无需多言，直接看文章吧：[Obsidian 插件之 Dataview - 知乎 8](https://zhuanlan.zhihu.com/p/373623264)

obsidian-excalidraw-plugin
--------------------------

在 Obsidian 中进行绘画，之前我写过关于这个的文章：[Obsidian 插件之 Excalidraw - 知乎 2](https://zhuanlan.zhihu.com/p/387969823)

nldates-obsidian
----------------

用于快速输入当前的日期等。

* * *

总结
==

今年和上一年的区别在于，类似 `obsidian-dice-roller` 这种插件逐渐消失在了我的插件列表中，我更加注重插件本身的功能性，逐渐增加了对我编辑可使用的增强插件。而我也逐渐发现自己并不打算在 Obsidian 进行 pdf 标注等行为，所以 markmind 以及 annotator 这两个插件都被我移除了。

然后我也发现今年更多插件逐渐成为了一个整合型或者优化型插件，更进一步提升了用户的使用体验，例如 Commander 插件整合了多个 Obsidian Customize 插件功能一样。

同时我发现今年我对新插件的功能更多关注于是否对我已经成型的工作流有一定的影响，例如 obsidian-projects 就是近期我在社群中狂推的一个插件，它确实对得起我的推荐，真的建议每个人都去试用一下。

最后，希望这个系列能长久继续下去，用于观察 Obsidian 社区以及我的发展，谢谢大家阅读。

 ![](https://forum-zh.obsidian.md/letter_avatar_proxy/v4/letter/k/df705f/90.png) [](/t/topic/10622/1 "转到引用的帖子")![](https://forum-zh.obsidian.md/user_avatar/forum-zh.obsidian.md/boninall/40/5_2.png) boninall:

> obsidian-projects
> -----------------
> 
> 这个插件是目前我见过在 Obsidian 中实现的可编辑数据库（基于文件夹）/ 可视化 Dataview 最优雅的插件，完毕。

project 插件是什么，在 GitHub 上没有搜到 ![](https://forum-zh.obsidian.md/letter_avatar_proxy/v4/letter/c/a8b319/90.png) [](/t/topic/10622/1 "转到引用的帖子")![](https://forum-zh.obsidian.md/user_avatar/forum-zh.obsidian.md/boninall/40/5_2.png) boninall:

> obsidian-projects

好像只支持 0.16 以上版本？![](https://forum-zh.obsidian.md/letter_avatar_proxy/v4/letter/d/5fc32e/90.png)

安装 brat 插件，然后按照 brat 的使用方法去 git 搜 obsidian-projects 插件，添加后使用。需要 Obsidian 本体 0.16 版本。

![](https://forum-zh.obsidian.md/letter_avatar_proxy/v4/letter/d/5fc32e/90.png)

确实需要 0.16。我的不是 0.16 版本，安装不上。