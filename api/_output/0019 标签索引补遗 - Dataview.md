> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [obsius.site](https://obsius.site/5d442x5j3q4i0j2g2b3m)

> 做了标签索引页，标签变得有条理了。

> *   [《遇见 Obsidian》系列笔记汇总目录](https://meta.appinn.net/t/topic/37042)
> *   如果觉得有用就支持一下作者：[老鼠爱发电](https://afdian.net/@daomishu)

做了标签索引页，标签变得有条理了。

但想必在制作的过程中你就发现了一个问题：哪些标签已经登记好了，哪些标签还没登记，很容易闹不清啊，所以有点越整理越乱。

什么，你没感觉？！你笔记都不够两位数，先别说话，乖乖记笔记去。

所以整理过程中我用了两个查询辅助（均使用 dataviewjs 代码块插入）：

### 无标签笔记

```
/* 获取所有页面，然后过滤，条件是没有标签 */
const pages = dv.pages().where(b => !b.tags);
/* 输出标题，这里标题中加上了数量 */
dv.header(2, "无标签笔记 - "+pages.length)
/* 输出笔记列表 */
dv.list(pages.file.link);
```

三句代码，效果我挺满意的。

### 未索引标签

列出所有当前文件不具有的标签。（如果标签在当前页面中，那显然就是在上面索引中登记了。

```
/* 获取当前页面中所有标签 */
const IndexTags = dv.current().file.etags;
/* 查询所有包含标签的页面 */
const pages = dv.pages().where(b => b.tags && b.tags.length);
/* 准备一个标签对象 */
const tags = {};
/* 遍历所有标签，并计数 */
for(let t of pages.file.tags){
  if(IndexTags.indexOf(t)===-1){
    tags[t] = tags[t] ? tags[t]+1 : 1
  }
}
/* 准备一个标签数组 */
const tagsList = []
/* 将标签整理后存入数组 */
for(let t in tags){
  tagsList.push(t+' '+tags[t])
}
/* 输出标题，包含标签数量 */
dv.header(2, "未索引标签 - "+tagsList.length)
/* 输出标签列表 */
dv.list(tagsList)
```

这样把未整理的都列出来，甚至标记上数量，就非常方便整理。这些查询也可以用其他方式书写，代码可以再简洁一些。不过我喜欢把数量显示出来，看着爽！