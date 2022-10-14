> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [forum-zh.obsidian.md](https://forum-zh.obsidian.md/t/topic/292) ![](https://forum-zh.obsidian.md/user_avatar/forum-zh.obsidian.md/临安/90/4120_2.png)

大家好，这里是差生文具多的热爱折腾的研究生临安。在 @boninall 的鼓励下开了这篇帖子，分享一下我的文献笔记流程。因为我的整个过程都非常简单（其实也是因为技术小白），所以使用的都是基本功能，虽然用了`Dataview`插件，但是也只是最基础的`table`展示而已。

**本文只展示文献查找阅读和整合知识的流程，不包括写作过程。**

我的流程大体上是：查询并获取文献 → 阅读标注并做文献笔记 → 标记问题 → 整合主要观点 → 回顾并解决。下面会按照这个顺序展开叙述。

### 查询并获取文献

在阅读文献时我倾向于针对某个领域集中了解，从综述入手，到十分重要的标志性文献，再到与其相关的我自己比较感兴趣的文献。所以首先就是搜索并整理到自己的文献库中。搜索功能最常用的当然是 [Google Scholar 53](https://scholar.google.com/) 和 [CNKI 30](https://www.cnki.net/)，同时我也会使用 [Connected Papers 92](https://www.connectedpapers.com/)，可以十分方便地看到与当前文献相关的其他文献，以及亲疏关系、权重大小等等信息。

在搜索到合适的文献后，就用浏览器插件获取到 Zotero 中。如果安装了油猴脚本的 [Sci-Hub Button 109](https://greasyfork.org/zh-CN/scripts/370246-sci-hub-button) 脚本，那么在储存信息到 Zotero 的时候，很多文献的 pdf 会直接被下载并附到该条目上，还是比较方便的。  

![](https://forum-zh.obsidian.md/uploads/default/optimized/1X/98fc70b2a19a7c7c401aef5eae73ead258f23934_2_690x416.jpeg)

### 阅读文献做笔记及标记问题

在阅读一篇较为重要的论文时，我倾向于在笔记里反应出它原本的一些结构，方便回顾时理清思路，同时也会把比较重要的观点标出来放在最前面，这样在与其他文献进行链接时，用鼠标悬停的方式就能直接看到前两行的重要信息，比较快捷。在记笔记的过程中如果引用了其他论文中较为重要的观点，则也用`[[]]`先标出来，之后再补充阅读并做笔记。  

![](https://forum-zh.obsidian.md/uploads/default/optimized/1X/3d16d61a407c0029f6d5a203d74872e920d4d079_2_690x416.jpeg)

在阅读论文中一定会产生疑问，或者是有看不懂的地方需要进一步查找资料，或者是对该篇文章有思考，这个时候我会提另做一个 ZK 笔记链接到这篇文章，按需求和内容打上不同的 tag，方便之后汇总获取。  

![](https://forum-zh.obsidian.md/uploads/default/optimized/1X/21de805888af4961a029bd3c42c2af249e692872_2_690x416.jpeg)

### 整合主要观点

只看单独的论文笔记肯定是意义不大的，需要将各种观点放在一起才比较容易了解这个方向的全貌，所以我会开一个关于这个主题的汇总笔记，把各个论文中重要的观点尽量用一句话概括后放到这里，同时链接到原论文笔记，这样可以理清思路，也为写综述创造了很多方便。  

![](https://forum-zh.obsidian.md/uploads/default/optimized/1X/ed1f1185d0ce0cd34013c1e637c81b387a36b3be_2_690x416.jpeg)

![](https://forum-zh.obsidian.md/uploads/default/optimized/1X/ef6d38197917b7362741ad94ae74ff1ef15e6696_2_690x416.jpeg)

### 问题和想法的回顾

前面提到了单独列出来的问题笔记和思考笔记，在需要回顾时可以采用搜索的方式，比如我用`#question`和`#thoughts`来标记这两种笔记，直接搜索即可，还可以搭配相关的领域 tag 一起搜索。另外也可以用`Dataview`将其列出。  

![](https://forum-zh.obsidian.md/uploads/default/optimized/1X/3eedd27ec0978fe02e166f6bbc4aeb9723ad6501_2_690x416.png)

经过以上的流程，在积累了一段时间的相关笔记之后就可以在图谱中查看了，通过不同的颜色和圆点的大小可以看出哪些文献相关的最多，产生的问题（红色）都和哪些论文有关，有哪些论文一直在和别的论文发生关联却没有被阅读和记录（浅灰色），又有哪些论文虽然属于这个领域却没有和其他论文产生关联，是这个领域比较孤僻没价值还是自己看得不够全面？  

![](https://forum-zh.obsidian.md/uploads/default/optimized/1X/71a666b48d34d4e70a9fa16b3d13233a11a2d2e3_2_690x416.png)

### 结语

一直以来单纯的阅读和记笔记对我来说并不是特别大的问题，使用什么方式都没关系。我在阅读文献时遇到的最大的问题其实是 “如何回忆起我曾经看过某篇论文？”“这个观点好眼熟，可是它出现在哪篇文章里来着？”Obsidian 对我来说主要就是解决了这个问题。本地化和 markdown 配合模板使记笔记的过程安心且快捷，双链功能和图谱功能方便建立笔记间的联系，标签系统加上多样化的搜索方式使笔记都能被找到，再加上`Dataview`插件的动态获取及展示使得维护成本非常低，基本就可以完成所有的工作了。而且非常重要的是，没有技术门槛，实现的过程没有什么负担。

对于 Obsidian 的高级功能我了解得不多，也许是没有需求，也许是有需求但自己并未发现，还需要不断学习。欢迎小伙伴们交流自己的高效率方法~

附：作为一个健忘症晚期患者，为了方便直达常用项目，我也设置了一个 “首页” 作为索引，欢迎查看关于我的工作区设置的分享帖 ๑╹◡╹)ﾉ”：[『晒晒我的工作区』原生主题 + Snippets 爱好者 | 学生党 308](https://forum-zh.obsidian.md/t/topic/178)