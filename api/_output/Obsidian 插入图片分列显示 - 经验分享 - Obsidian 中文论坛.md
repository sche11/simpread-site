> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [forum-zh.obsidian.md](https://forum-zh.obsidian.md/t/topic/10189) ![](https://forum-zh.obsidian.md/user_avatar/forum-zh.obsidian.md/edoy/90/4733_2.png)

1. 下载安装 Contextual Typography 的最新版本  

![](https://forum-zh.obsidian.md/uploads/default/optimized/2X/e/e22c5ddfe922899ee3361d3a3842a4b32351ef26_2_690x333.png)

2. 复制以下代码，改文件后缀为 .css 或者直接从[插入图片分列 10](https://github.com/zremboldt/obsidian-media-grid) 下载

```
/* This snippet requires Contextual Typography 2.2.1+ */
/* https://github.com/mgmeyers/obsidian-contextual-typography */

:root {
  --content-base-width: 45rem;
}

/* ----------------------------------------- */
/* Handle overall content width */
/* ----------------------------------------- */

/* Wrapper with padding keeps content from bumping the edges */
.markdown-preview-view.is-readable-line-width {
  padding-inline: 30px;
}

/* Container controlling overall max content width */
.markdown-preview-view.is-readable-line-width .markdown-preview-section {
  width: 100%;
  max-width: var(--content-max-width, 45rem); /* Second value is fallback in case user isn't using Style settings */
}

/* All children of overall container are divs */
.markdown-preview-view.is-readable-line-width .markdown-preview-section > div {
  margin-inline: auto;
  width: min(var(--content-base-width), 100%);
}

/* Specific children of overall container that contain media */
.markdown-preview-view.is-readable-line-width .markdown-preview-section div[data-is-embed] {
  width: 100%;
}

/* ----------------------------------------- */
/* Make media items display in rows */
/* ----------------------------------------- */

/* p tags wrap each row */
.markdown-preview-view.is-readable-line-width .markdown-preview-section div[data-is-embed] > p {
  display:grid;
  grid-template-columns:repeat(auto-fit, minmax(0, 1fr));
  grid-gap: var(--media-grid-gap, 7px);
  margin: 0;
}

/* Remove breaks from the document flow */
.markdown-preview-view.is-readable-line-width .markdown-preview-section div[data-is-embed] > p br {
  display: none;
}

/* Media items sourced from your vault are wrapped in a span – media linked from the web is not wrapped */
.markdown-preview-view.is-readable-line-width .markdown-preview-section div[data-is-embed] > p > span {
  display: flex;
}

/* Apply this to all img/video tags in a row whether they're wrapped in a span or not */
.markdown-preview-view.is-readable-line-width .markdown-preview-section div[data-is-embed] > p img,
.markdown-preview-view.is-readable-line-width .markdown-preview-section div[data-is-embed] > p video {
  flex: 1;
  align-self: stretch;
  object-fit: cover;
  border-radius: var(--media-border-radius, 4px);
}

/* Create gaps between rows */
.markdown-preview-view.is-readable-line-width .markdown-preview-section div[data-is-embed] + div[data-is-embed] {
  margin-top: var(--media-grid-gap, 7px);
}

/* ----------------------------------------- */
/* Style settings */
/* ----------------------------------------- */

/* @settings
name: Media Grid Snippet
id: media-grid-snippet
settings:
  -
      id: content-max-width
      title: Grid width
      description: Set the max width of your grid layouts.
      type: variable-select
      allowEmpty: false
      default: var(--content-base-width)
      options:
          - 
              label: Base width
              value: var(--content-base-width)
          - 
              label: Small
              value: calc(var(--content-base-width) + 5%)
          - 
              label: Medium
              value: calc(var(--content-base-width) + 10%)
          - 
              label: Large
              value: calc(var(--content-base-width) + 20%)
          - 
              label: Full width
              value: 100%
  -
      id: media-grid-gap
      title: Grid gap
      description: Set the gap size between items in your grid layouts.
      type: variable-number-slider
      format: px
      default: 7
      min: 0
      max: 80
      step: 1
  -
      id: media-border-radius
      title: Border radius
      description: Set the border radius of your images and videos.
      type: variable-number-slider
      format: px
      default: 4
      min: 0
      max: 40
      step: 1
*/
```

3. 在设置中选择外观，拉到最底部 css 代码片段选项，点击文件夹图标选择第二步中创建的 .css 文件，点击文件夹图标旁边的更新图标，更新。

![](https://forum-zh.obsidian.md/uploads/default/original/2X/6/696e8fa9e5f21a6ad6767f72d6d935a4b1c26e45.png)  
![](https://forum-zh.obsidian.md/uploads/default/original/2X/b/b74e8cff8d6aa055e319873fced64d81363652df.png)

4. 打开第二步中 .css 文件的按钮，完成。

5. 图片插入示例：插入的图片链接两行之间不要空行，自动实现图片分列效果

![](https://forum-zh.obsidian.md/uploads/default/original/2X/2/25105068aafee047f1c1e1591bda1436a86737f7.png)

6. 效果  

![](https://forum-zh.obsidian.md/uploads/default/optimized/2X/2/2759a112eaf6dff7fce0e050a543f8546a321779_2_690x441.jpeg)

原教程地址：  
[Obsidian 插入图片分列 10](https://github.com/zremboldt/obsidian-media-grid)  
参考教程：  
[Obsidian 图片分列显示 9](https://www.uncoverman.com/obsidian-image-grid-setting.html)

![](https://forum-zh.obsidian.md/letter_avatar_proxy/v4/letter/1/8edcca/90.png)

失败。不知道为啥，还是一如既往地竖排显示。

![](https://forum-zh.obsidian.md/user_avatar/forum-zh.obsidian.md/edoy/90/4733_2.png)

切换一下视图，是在阅读视图里才能分列

![](https://forum-zh.obsidian.md/letter_avatar_proxy/v4/letter/1/8edcca/90.png)

还需要 front-matter 区写上 `cssclass: img-grid`才成功。

![](https://forum-zh.obsidian.md/user_avatar/forum-zh.obsidian.md/edoy/90/4733_2.png)

我发的这个教程不需要，按底下参考教程里那么设置才需要。