> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/531924705)

> Obsidan 应该拥有更好的标注方案，如果你苦恼于 Obsidian 的标注割裂感，可以看看此方案，完美的解决了 Obsidian 标注的问题。前言 同步助手 1.1.0 与 标注嵌入模式 与 SimpRead Unreader Sync 2.1.0 实现：集成标…

> Obsidan 应该拥有更好的标注方案，如果你苦恼于 Obsidian 的标注割裂感，可以看看此方案，完美的解决了 Obsidian 标注的问题。

前言
--

[同步助手 1.1.0](https://zhuanlan.zhihu.com/p/530526202) 与 [标注嵌入模式](https://github.com/Kenshin/simpread/discussions/4070) 与 [SimpRead Unreader Sync 2.1.0](https://zhuanlan.zhihu.com/p/531439945) 实现：

集成标注到 Obsidian，在 Obsidian 中标注并实时同步标注到 Obsidian，不仅如此还可以管理你的稍后读。

Obisdian 的「弊端」
--------------

Obsidian 这类工具的最大的弊端是：标注场景与 Obsidian 分裂以及标注的规则太弱，无论什么方式都需要在原文基础上标注，然后再同步到 Obsidian 并再次修改。

简悦为了降低这个「门槛」，推出了一系列措施包括：

1.  [Markdown 辅助增强插件](https://zhuanlan.zhihu.com/p/505235831) → 用更灵活强大的模板规则来定制
2.  [导入到 Obsidain](https://zhuanlan.zhihu.com/p/504280066) → 自动同步来自 ➊ 的标注到 Obsidian
3.  [SimpRead Unreader Sync](https://zhuanlan.zhihu.com/p/521932257) → 为 Obsidian 集成 ➊ 和 ➋ 专门针对 Obsidian 重度使用用户

最后，得益于 [同步助手 1.1.0 内置的标注嵌入模式](https://zhuanlan.zhihu.com/p/530526202)，终于解决了「最后一步」这个难题。

视频演示
----

前置知识
----

如果要实现上面的操作，需要知识库相关配置的支持，新用户可以通过下面的教程设置。

[新用户教程：一站式知识库配置](https://zhuanlan.zhihu.com/p/532227053)

完成上述配置后接下来是本篇教程的重点部分。

SimpRead Unread Sync
--------------------

此插件没有上架到 Obsdian 第三方社区，通过此方式实现自动安装。

### Beta Reviewers Auto-update

一个 Obsidian Plugin 可以方便用户安装未上架到 Obsdian 插件市场的插件，细节 [请看这里](https://github.com/TfTHacker/obsidian42-brat)。

在 Obsidian 插件市场搜索 brat 然后安装即可。

![](https://pic2.zhimg.com/v2-d2d72c452386c2c7784bc0724dba0c11_r.jpg)

### 安装

打开 BRAT 选项，并找到下图所示的内容

![](https://pic4.zhimg.com/v2-f9024a014ebafb96357fb4eee1d1701b_r.jpg)

点击打开并输入 SimpRead Sync Plugin 地址与版本号，点击 **Add Plugin** 即可。（截图跟你使用时的版本会不一样）

![](https://pic3.zhimg.com/v2-4bc99fff77ab40c387a76847748f8a9e_r.jpg)

*   SimpRead Sync Plugin 地址 → [https://github.com/Kenshin/simpread-obsidian-plugin](https://github.com/Kenshin/simpread-obsidian-plugin)
*   版本号 → 打开 [Release](https://github.com/kenshin/simpread-obsidian-plugin/releases/latest) 然后找最新的一个即可。（截图跟你使用时的版本会不一样）

![](https://pic4.zhimg.com/v2-8d1cb6b50137007e3186b354a1b7447f_r.jpg)

### 配置

SimpRead Unread Sync 的配置很简单，只需要指定目录以及指定模板，其余默认即可。

简悦的配置文件目录与上面配置自动同步时为同一目录即可。

![](https://pic4.zhimg.com/v2-7621672811ac3289d8d74258035d781b_r.jpg)

至此，大部分配置以及结束，接下来需要了解一个很重要的概念：「模板」

模板
--

> 这是来自 [简悦社区](https://t.me/simpread) 用户 [1wingedangel](https://github.com/1wingedangel) 基于 [同步助手 1.1.0](https://github.com/Kenshin/simpread/discussions/4049#discussioncomment-2982511) 与 [标注嵌入模式](https://github.com/Kenshin/simpread/discussions/4070) 与 [SimpRead Unreader Sync 2.1.0](https://github.com/Kenshin/simpread/discussions/2889) 形成的新的工作流（模板）。

模板是 SimpRead Unread Sync 的核心，为了降低难度，简悦官方维护一个 [模板库](https://github.com/Kenshin/simpread/discussions/2153)，按文中的例子，可以直接使用 [Obsidian 模板 · 标注嵌入模式版](https://github.com/Kenshin/simpread/discussions/2153#discussioncomment-2983977)。

### 截图

如果你配置后会得到下图所示的效果。

![](https://pic4.zhimg.com/v2-461095b51a0010cfb95659837fff6487_r.jpg)

### 稍后读

```
---
title: "{{title}}"
alias: 
<% if ( unread.note && unread.title != unread.note ) { %>  - "{{note}}"
<% } %>  - "{{title}}"
created-date: {{create|yyyy-mm-dd'T'HH:MM:sso}}
type: Simpread
<% if (unread.img) { %>banner: "<%- unread.img %> "
banner_icon:  
<% } -%>
tag: {{ |tag| | }}
idx: {{idx}}
---

# {{title}}
<%
let ifURI = "http://localhost:7026/unread/"+unread.idx
%>
> [!example]- [ 内部链接](<<%= ifURI %>>) [ 外部链接](<{{ext_uri}}>)    
> URI:: [ ](<<%= ifURI %>>) [ ](<{{ext_uri}}>) 
> intURI:: [ 内部链接](<{{int_uri}}>)

%%
> [!example]+ **Comments**  
> ```dataview
> TABLE 
>     WITHOUT ID
>     link(Source, dateformat(date(Source), "yyyy-MM-dd")) as Date___, 
>     regexreplace(rows.Comments,"^@@\[\[.+?\]\]\s","") as "Comments"
> FROM "journals"
> WHERE  contains(cmnt, this.file.name)
> FLATTEN cmnt as Comments
> WHERE contains(Comments, this.file.name)
> GROUP BY file.link as Source
> SORT rows.file.day desc
> ```
>  **Description**:: {{desc}}
%%

> [!md] Metadata  
> **标题**:: [{{title}}]({{url}})  
> **日期**:: [[{{create|yyyy-mm-dd}}]]  
<% if ( unread.annotations.length > 0 ) { %>
## Annotations

{{annotations}}
<% } -%>
<% if ( unread.tags.includes('Highlights') ) { %>
![[<%% tp.file.title %>_mentions#Highlight Mentions]]
<% } -%>
<% if ( unread.refs ) { %>
## Reference   
{{-|refs}}  
<% } %>
```

**链接的 Callouts 调整为极速版链接**。直接点击即可在 Obsidian 的新面板打开稍后读的本地 HTML 文件。

链接 Callouts 内新增 field （URI、intURI）来给 dataview 提供查询用途。具体自行学习一下 dataview 的用法，网上有很多。

### 标注

```
<%
let colors = [ '#B4D9FB', '#ffeb3b', '#a2e9f2', '#a1e0ff', '#a8ea68', '#ffb7da' ],
    color  = colors[ annote.color ];
let chls = [ 'srhl1', 'srhl2', 'srhl3', 'srhl4', 'srhl5', 'srhl6' ],
    chl  = chls[ annote.color ];
let iframeURI = "http://localhost:7026/unread/"+unread.idx+"#id="+annote.id
if (unread.note && unread.title != unread.note) {
var filetitle = unread.note;
}
else {
var filetitle = unread.title;
}
let wikilinks = "[[SR" + unread.idx + "@" + filetitle + "| ]]";
-%>
<% if (annote.note.startsWith("######")) { %>
<% 
let note = annote.note.slice(7);
-%>
###### <% if (note) { %><%- note %><% } else { %>{{an_text}}<% } %>
<% } else if (annote.note.startsWith("######")) { %>
<% 
let note = annote.note.slice(6);
-%>
###### <% if (note) { %><%- note %><% } else { %>{{an_text}}<% } %>
<% } else if (annote.note.startsWith("####")) { %>
<% 
let note = annote.note.slice(5);
-%>
#### <% if (note) { %><%- note %><% } else { %>{{an_text}}<% } %>
<% } else if (annote.note.startsWith("###")) { %>
<% 
let note = annote.note.slice(4);
-%>
### <% if (note) { %><%- note %><% } else { %>{{an_text}}<% } %>
<% } else { %>
> [!<%= chl %>] <%- wikilinks %> <mark style="background-color: <%= color %>">Highlights</mark> [ ](<<%= iframeURI %>>) [ ](<{{an_ext_uri}}>) {{#|an_tag| }}  
{{{html_format|>|{{an_html}}}}}
<% if (annote.refs) { -%>
{{> -  |an_refs}}
<% } -%>
<% if (annote.note) { -%>
<% if (annote.note.startsWith("todo:") == false && annote.note.startsWith("done:") == false) { -%>
>  
> -  {{an_note}}
> ^sran-{{an_id}}
<% } else { -%>
<% 
let note = annote.note.slice(6);
if (annote.note.startsWith("todo:")) {
  var taskStatus = " "; }
  else {
  var taskStatus = "x";
}
-%>
> ^sran-{{an_id}}

- [<%= taskStatus %>] <%- note %> #web ^srtask-{{an_id}}
<% } -%>
<% } else { -%>
> ^sran-{{an_id}}
<% } -%>
<% } -%>
```

**标注的内部链接全部换成极速版的标注链**。直接点击即可在 Obsidian 的新面板打开稍后读的本地 HTML 文件。

### Callouts 支持简悦的标注颜色

直接定制 callouts 的颜色需要自定义 CSS，把这段代码保存为 css 文件之后复制到 obsidian 的 snippets 文件夹，在外观设置中导入该 css 即可。

```
.callout[data-callout="srhl1"] {
    --callout-color: 180, 217, 251;
    --callout-icon: none;
}
.callout[data-callout="srhl2"] {
    --callout-color: 255, 235, 59;
    --callout-icon: none;
}
.callout[data-callout="srhl3"] {
    --callout-color: 162, 233, 2421;
    --callout-icon: none;
}
.callout[data-callout="srhl4"] {
    --callout-color: 161, 224, 255;
    --callout-icon: none;
}
.callout[data-callout="srhl5"] {
    --callout-color: 168, 234, 104;
    --callout-icon: none;
}
.callout[data-callout="srhl6"] {
    --callout-color: 255, 183, 218;
    --callout-icon: none;
}
```

生成文献笔记
------

按照简悦知识库的配置方式，会出现 1234-title@annote.md 的文件，此文件就是文献笔记，让 Obsidan 读取到此文件的方案有很多，下面列举几种。

### Command Support

在 Obsidian 使用 sr 呼出 Command Support 然后通过下面任意其一的方式找到需要生成文献笔记的稍后读。

![](https://pic3.zhimg.com/v2-db4b94223925181e857cf2ce4f706b8e_r.jpg)

### 使用自动化 + 同步助手的辅助增强方案

当配置知识库时，设置了当加入稍后读后生成 Markdown 的自动化时

![](https://pic4.zhimg.com/v2-690a967a0886ff5fa8eca18b50150f67_r.jpg)

再结合同步助手的辅助增强，将 .md 生成后自动设置为 Obsidian 对应的文件夹

![](https://pic1.zhimg.com/v2-154e520040e3dd1180b2eaac6d7ebfb0_r.jpg)

都可以方便的将文献笔记生成到 Obsidian 对应的文件。

如何使用
----

SimpRead Unread Sync 已经集成了标注，可以使用下面的两种方式。

### 通过 Command Support

![](https://pic2.zhimg.com/v2-30dd263ba1009426033213526166c74d_r.jpg)

### 在模板中加入特定 URL

只要你的 Markdown 包含下面的 URL（上面的模板以及包含了这两个链接的定制化）

`http://localhost:7026/unread/xxx` 或 `http://localhost:7026/unread/xxx#id=123456789`

并且在阅读视图或者 Callouts 中即可点击链接后自动打开标注页。

至此，模板设置也全部完成。

基于此的最简工作流
---------

1.  阅读模式使用 live Editor 后生成快照
2.  编辑稍后读元数据、加入稍后读
3.  接下来就在 Obsidian 完成

### **注意**

*   此方案使用了最简单的方式，即只在简悦的扩展端使用加入稍后读产生本地快照这个步骤。
*   进入 Obsidain 后使用 Command Support 找到需要标注的稍后读，并生成对应的文献笔记。

### 进阶

此方案的核心：加入稍后读后生成 **文献笔记 + 本地快照**，所以能实现它们的方式有很多中：

1.  加入稍后读 / 标注时生成 HTML 以及 Markdown
2.  仍可以使用 [Markdown 辅助增强插件](https://zhuanlan.zhihu.com/p/505235831) 与 [导入到 Obsidain 插件](https://zhuanlan.zhihu.com/p/504280066) 方案

实现更完善的文献笔记生成和使用场景。

关于简悦极速版结合 Hover Editor 的使用小结
----------------------------

简悦极速版结合 Hover Editor 可以实现稍后读的置顶浮动窗口，方便做一些更加复杂的工作流。

*   把任意文献笔记通过页面预览的方式创建 Hover Editor 窗口
*   激活 Hover Editor 的窗口聚焦（必须，除非你设置了自动聚焦）
*   打开触发简悦极速版的任意链接。此时会在 Hover Editor 的新面板里打开简悦极速版的稍后读页面
*   关闭原来的任意文献笔记

关联
--

简悦与 Obsidian 都是基于 Local first 概念，即使只是轻量级使用简悦，也可以实现很多联动：

*   [利用简悦插件 Live Editor 来助力你的双向链接笔记剪藏流程](https://zhuanlan.zhihu.com/p/412710060)
*   [自动导入标注到 Obsidian（不使用同步助手方案）](https://github.com/Kenshin/simpread/discussions/3932)
*   [利用 Dataview + Blue Topaz + Markdown 辅助增强 + 导入到 Obsidian 插件，实现对标注的汇总与回顾](https://github.com/Kenshin/simpread/discussions/3807)

关于简悦与 Obsidian 的更多联动 [请看这里](https://github.com/Kenshin/simpread/discussions?discussions_q=label%3Aobsidian)。