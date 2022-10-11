> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [gitee.com](https://gitee.com/tughv/zotero-plug-in/blob/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.md)

> 文献管理软件 zotero 的使用教程，没有任何违规的内容

如何用源码打包自己的插件

有时候我们想用的一个插件作者没有更新或者直接失联了，那可太难受了，不能因为作者跑路了插件就不用了吧，当然要自己动手了。

我是用的是在 win 里面安装 deepin 虚拟机.

### [](#%E7%AC%AC%E4%B8%80%E6%AD%A5-%E5%8E%BBgithub%E4%B8%8B%E8%BD%BD%E6%BA%90%E7%A0%81)第一步 去`github`下载源码

一般来说，作者会把源码托管到`github`上，当然了，并不是所有的作者都会这么干，没有源码就没办法下载了。

比如时间`2022-03-27`，[MaxKuehn/zotero-scholar-citations: Zotero plugin for auto-fetching numbers of citations from Google Scholar (github.com)](https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2FMaxKuehn%2Fzotero-scholar-citations) 就没有适配到版本 6，我们把这个仓库下载下来，当然是在`linux`里面了。

查看一下文件结构。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/%E6%88%AA%E5%9B%BE_%E9%80%89%E6%8B%A9%E5%8C%BA%E5%9F%9F_20220327225915.png)

`build.sh`是打包插件的脚本，`chrome.manifest`,`install.rdf`，`chrome文件夹`是组成插件的重要部分，其中`install.rdf`是安装插件时程序会验证版本的文件，打开看一下。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/%E6%88%AA%E5%9B%BE_%E9%80%89%E6%8B%A9%E5%8C%BA%E5%9F%9F_20220327230322.png)

`maxversion`里面的数字说明这个插件最大适配的版本，只要把这个`5.0.*`改成`6.0.*`即可。一般来说，`zotero`很少会变更 api，只要这个没有变，5 的插件到了 6 还能用。

[](#%E7%AC%AC%E4%BA%8C%E6%AD%A5-%E6%89%93%E5%8C%85%E6%8F%92%E4%BB%B6)第二步 打包插件
-----------------------------------------------------------------------------

在终端里面执行`./build.sh`这个打包程序就行了。你可以打开这个`build.sh`看下里面的内容，如果你能自己改得话更好了。然后就可以看到打包好的插件。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/%E6%88%AA%E5%9B%BE_%E9%80%89%E6%8B%A9%E5%8C%BA%E5%9F%9F_20220327230749.png)

其实这个脚本就是把需要的组件用 zip 打包到一起，如果有些插件的源码里面没有个脚本，可以参照这个写一个。

[](#1-%E4%BF%AE%E6%94%B9%E7%89%88%E6%9C%AC%E9%AA%8C%E8%AF%81)1. 修改版本验证
----------------------------------------------------------------------

插件`.xpi`就是将源码打包成了一个文件，将`xpi`改成`zip`然后解压。

按照如下修改，`maxversion`里面的数字说明这个插件最大适配的版本，只要把这个`5.0.*`改成`6.0.*`即可。一般来说，`zotero`很少会变更 api，只要这个没有变，5 的插件到了 6 还能用。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/%E6%88%AA%E5%9B%BE_%E9%80%89%E6%8B%A9%E5%8C%BA%E5%9F%9F_20220327230322.png)

这样在安装插件的时候软件检查就能通过版本检查。

[](#2-%E4%B8%8B%E8%BD%BDgit)2. 下载 git
-------------------------------------

到 [git](https://gitee.com/link?target=https%3A%2F%2Fgit-scm.com%2F) 网站下载 git 工具.

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/image-20220407094143121.png)

下载适合你的系统的版本，并安装。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/image-20220407094212548.png)

[](#3-%E6%96%B0%E5%BB%BA%E6%89%93%E5%8C%85%E8%84%9A%E6%9C%AC)3. 新建打包脚本
----------------------------------------------------------------------

这个`builds`文件夹是我自己建立的，用于保存打包插件的地方，你的不一定有。

在你的插件文件夹里面新建一个`txt`文件，然后将后缀改成`sh`

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/image-20220407094304595.png)

用记事本打开`build.sh`，在里面填写如下代码

```
#!/bin/sh

version=2.6.5
zip -r zotero-if-${version}.xpi chrome/* chrome.manifest install.rdf
```

注：`version=2.6.5`表示你要发行的版本为 2.6.5，你可以自己修改这里的版本，`zotero-if`表示你的插件名称，你根据自己的插件名称修改，其他的东西不用改。

在文件夹里面空白处右键，左键点击`Git Bash Here`

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/image-20220407094648122.png)

在这里输入`./build.sh`，回车

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/image-20220407094803001.png)

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/%E5%A6%82%E4%BD%95%E7%94%A8%E6%BA%90%E7%A0%81%E6%89%93%E5%8C%85%E8%87%AA%E5%B7%B1%E7%9A%84%E6%8F%92%E4%BB%B6.assets/image-20220407095017016.png)

然后就可以看到生成的插件。