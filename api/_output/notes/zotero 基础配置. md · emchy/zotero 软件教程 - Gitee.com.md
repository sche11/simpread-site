> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [gitee.com](https://gitee.com/tughv/zotero-plug-in/blob/master/notes/zotero%E5%9F%BA%E7%A1%80%E9%85%8D%E7%BD%AE.md)

> 文献管理软件 zotero 的使用教程，没有任何违规的内容

[zotero 使用教程 1](https://gitee.com/link?target=https%3A%2F%2Fwww.bilibili.com%2Fvideo%2FBV1eY41187ft%3Ffrom%3Dsearch%26seid%3D16982179123616172064%26spm_id_from%3D333.337.0.0)

[zotero 使用教程 2](https://gitee.com/link?target=https%3A%2F%2Fwww.bilibili.com%2Fvideo%2FBV1ZE411p7qT%2F%3Fspm_id_from%3D333.788.recommend_more_video.1)

[](#zotero%E7%9A%84%E6%8F%92%E4%BB%B6%E5%AE%89%E8%A3%85%E5%8F%8A%E5%8A%9F%E8%83%BD%E6%95%99%E7%A8%8B)zotero 的插件安装及功能教程
----------------------------------------------------------------------------------------------------------------------

软件安装好会自动添加到 word 里面, 如果没有安装 word，去自己学校的网站找找看，或者自己找破解版。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20211029142202564.png)

[](#1-%E8%BD%AF%E4%BB%B6%E5%AE%89%E8%A3%85%E5%8F%8A%E6%B5%8F%E8%A7%88%E5%99%A8%E6%8F%92%E4%BB%B6%E9%85%8D%E7%BD%AE)1. 软件安装及浏览器插件配置
----------------------------------------------------------------------------------------------------------------------------------

*   使用浏览器去访问 [zotero 网站](https://gitee.com/link?target=https%3A%2F%2Fwww.zotero.org%2F)

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20210701172607641.png)

*   左边是软件的下载链接，下载软件的安装包，在 pc 安装即可。右边是插件下载快捷键，跟着完成即可。
    
*   对于谷歌浏览器，`zotero connector`无法连接到插件的商店，需要使用离线安装的办法将插件安装到浏览器里面，将离线插件`zotero connector`里面的`zotero-connector.crx`。谷歌浏览器的插件安装方法百度。
    
*   对于 edge 和 firforx，点击 **Install xxx connector** 就会跳转到应用商店下载。
    

[](#2-%E5%9D%9A%E6%9E%9C%E4%BA%91%E7%9B%98%E5%90%8C%E6%AD%A5%E5%A6%82%E6%9E%9C%E4%B8%8D%E9%9C%80%E8%A6%81%E5%A4%9A%E5%8F%B0%E7%94%B5%E8%84%91%E7%99%BB%E5%BD%95%E4%B8%80%E4%B8%AA%E8%B4%A6%E5%8F%B7%E8%BF%9B%E8%A1%8C%E5%90%8C%E6%AD%A5%E5%88%99%E6%97%A0%E9%9C%80%E6%AD%A4%E6%AD%A5%E9%AA%A4)2. 坚果云盘同步（如果不需要多台电脑登录一个账号进行同步则无需此步骤）
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

== 文档后面有使用 onedrive 同步的办法 ==

坚果云如果不开通会员每个月只有 1g 的上传流量

这里使用坚果云配置同步功能

1.  注册一个坚果云账号
2.  在账户信息右边的安全选项里面添加应用

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20210701172837530.png)

3.  注册一个 zotero 账号，登陆，如下勾选。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E5%9F%BA%E7%A1%80%E9%85%8D%E7%BD%AE.assets/image-20220115144608118.png)

3.  在 zotero 软件 编辑 - 首选项里面登录 zotero 账号，在文件同步里面选择 webDAV
4.  里面的密码是坚果云里面应用密码，账号为坚果云账号

[](#3-zotero%E6%9B%B4%E6%94%B9%E6%95%B0%E6%8D%AE%E4%BF%9D%E5%AD%98%E4%BD%8D%E7%BD%AE)3. zotero 更改数据保存位置
-------------------------------------------------------------------------------------------------------

因为 zotero 的数据和 zotero 的安装位置是分开的，而且数据默认的保存位置在 c 盘，对于 c 盘数据不够大的小伙伴应该希望能够更改数据保存位置。

注意：选择该自定义位置时请**不要**选择 onedrive 之类的在电脑上的磁盘空间，这样会导致数据库损坏，选择普通的磁盘文件夹就行了，建议像我这样命名，看名字就知道这是 zotero 的文件夹。

`编辑-首选项-高级-文件和文件夹`

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220104200032473.png)

点击选择，软件重启，即可更在数据保存的位置。

[](#4-word%E9%87%8C%E9%9D%A2%E6%B2%A1%E6%9C%89zotero%E9%80%89%E9%A1%B9%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95)4. word 里面没有 zotero 选项解决办法
-------------------------------------------------------------------------------------------------------------------------------------

1.  如果 word 版本太老需要安装较新的版本
2.  `编辑-首选项-引用-文字处理软件`

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220104200346733.png)

[](#5-zotero%E9%85%8D%E7%BD%AEscihub)5. zotero 配置 scihub
--------------------------------------------------------

[参考链接](https://gitee.com/link?target=https%3A%2F%2Fwww.52pojie.cn%2Fforum.php%3Fmod%3Dviewthread%26tid%3D1237319)

1.  编辑 - 首选项 - 高级 - 设置编辑器

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/085506avh9tq54zi3d7dr5.png)

2.  搜索 findPDF，双击搜索结果
    
    ![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/085508inoopvf4qvdryol4.png)
3.  双击后打开的对话框中输入下方的代码，原本输入框里面会自带一个 **==[]==**, 将其删掉就行。
    
    ```
    { "name":"Sci-Hub",   "method":"GET",   "url":"http://sci-hub.ren/{doi}",   "mode":"html",   "selector":"#pdf",   "attribute":"src",   "automatic":true }
    ```
    
    即可使用 Sci-Hub 作为源进行文献自动下载
    
    ![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20211029142955401.png)
    

对于一些无法开放获取的文献，右键 -> 找到可用的 PDF，软件就会到 scihub 上查找并下载，如果失败，就需要自己去下载然后拖入对应的目录。

[](#6-zotero%E9%85%8D%E7%BD%AEquicklookzotero6%E8%AF%A5%E5%8A%9F%E8%83%BD%E5%B7%B2%E7%BB%8F%E5%A4%B1%E6%95%88)6. zotero 配置 quicklook(zotero6 该功能已经失效)
-----------------------------------------------------------------------------------------------------------------------------------------------------

该软件的功能是在不打开文件的情况下快速预览，敲击空格键就可以预览内容，再敲击空格键就可关闭。

1.  需要先安装 **quicklook.msi** 的软件

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20211029142559735.png)

2.  在 zotero 里面安装插件

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20211029142624983.png)

然后找到 **quicklook** 的插件文件，点击即可，该软件可以通过敲击**空格键**快速预览内容而不用打开文件，节省时间。

==zotero_beta 版本的 quicklook 失效解决办法在`Zoteroquicklok_for_beta`文件夹里面 ==

[](#7-zotfile%E6%8F%92%E4%BB%B6%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8Equicklook%E6%8F%92%E4%BB%B6%E7%9A%84%E5%AE%89%E8%A3%85%E6%AD%A5%E9%AA%A4%E5%AE%8C%E5%85%A8%E4%B8%80%E8%87%B4)7. zotfile 插件的安装与 quicklook 插件的安装步骤完全一致
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

zotefile 插件的作用是能够自动重命名 pdf

为了避免麻烦，不建议使用这个插件，就我的使用感受来说，没有很强的功能，不使用倒是能省去很多烦恼。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220104193647975.png)

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220104193800947.png)

`custom location`可以选择一个文件夹按照 zotero 里面的目录结构保存 pdf

use subfolder defined by 是重新保存 pdf 的规则。

[](#8-zotero%E6%9B%B4%E6%94%B9%E5%BC%95%E7%94%A8%E5%AF%B9%E8%AF%9D%E6%A1%86)8. zotero 更改引用对话框
---------------------------------------------------------------------------------------------

编辑 -> 首选项 -> 引用文字处理软件，勾选**使用添加引用的经典对话框**

如果不勾选使用添加引用的静电对话框，在 word 里面引用文献的时候弹出的将是搜索框，可根据自己的喜好选择。

这种经典模式在文章较多的时候引用不是很方便，可以参考 [zotero 配合 better_bibtex 引用文献](https://gitee.com/tughv/zotero-plug-in/blob/master/notes/zotero%E9%85%8D%E5%90%88better_bibtex%E5%BC%95%E7%94%A8%E6%96%87%E7%8C%AE.md)

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20211029144016165.png)

[](#9-%E5%AE%89%E8%A3%85%E6%89%B9%E9%87%8F%E6%94%B9%E6%96%87%E7%8C%AE%E8%AF%AD%E8%A8%80%E4%B8%BAen%E7%9A%84%E6%8F%92%E4%BB%B6)9. 安装批量改文献语言为 en 的插件
--------------------------------------------------------------------------------------------------------------------------------------------------

改插件解决的是中英文混排时，`等和et al`不能混合使用的问题，如果在引用时，英文文献的作者超过三个时，就会以`等`结尾，而不是`et al`，所以需要将`zotero`中的该文献语言改成`en`。

插件的位置为`zotero插件->delitemwithatt.xpi`

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220102094646845.png)

右键点击选中的文献，将语言设置为 en，即可批量改语言为 en。

[](#10-%E9%80%89%E6%8B%A9%E4%B8%AD%E8%8B%B1%E6%96%87%E6%B7%B7%E6%8E%92%E7%9A%84csl)10. 选择中英文混排的`csl`
----------------------------------------------------------------------------------------------------

将该文件夹`style`里面的的文件复制到 zotero 数据库的`style`文件夹里面，重启`zotero`

，即可在样式里面看到添加的引文格式，尝试使用一下这几个不同的格式就知道他们之间的区别了。

更多中英文混排样式：[https://gitee.com/redleafnew00/Chinese-STD-GB-T-7714-related-csl](https://gitee.com/redleafnew00/Chinese-STD-GB-T-7714-related-csl)

[](#11-%E8%87%AA%E5%8A%A8%E5%A1%AB%E5%85%85%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%9A%84%E6%8F%92%E4%BB%B6)11. 自动填充影响因子的插件
--------------------------------------------------------------------------------------------------------------------------

安装 zotero IF.xpi 插件，就可以在右键里面看到影响因子的功能，影响因子的位置在`版权`里面填充，最新版本的插件是填充到`索书号`里面。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220102095222741.png) ![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220102095333707.png)

[](#12-%E7%AC%94%E8%AE%B0%E8%BD%AF%E4%BB%B6marktext)12. 笔记软件 marktext
---------------------------------------------------------------------

*   找到 marktext 安装包，github 上面可以下载
*   运行 mdRegrester.reg，这样就可以右键新建`markdown file`
*   marktext 的使用教程[参考博客](https://gitee.com/link?target=https%3A%2F%2Fblog.csdn.net%2Fmus123%2Farticle%2Fdetails%2F104294246) (marktext 是支持 md 语法的编辑器，和 typora 一样使用，且免费)

[](#13-%E8%8C%89%E8%8E%89%E8%8A%B1%E6%8F%92%E4%BB%B6)13. 茉莉花插件
--------------------------------------------------------------

安装插件`jasminum-v0.1.2.xpi`，该插件是一个对中文文献起到功能增强的插件，当将知网下载的 pdf 拖到 zotero 里面，他能够帮你自动提取里面的关键信息并建立分类，能够将中文名合并。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220104195405966.png)

茉莉花插件 PDFtk 报错的解决方法，如下：

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E5%9F%BA%E7%A1%80%E9%85%8D%E7%BD%AE.assets/image-20220319102940507.png)

下载软件里面的`pdftk`安装，在 zotero 里面的首选项做如下配置，选择 pdf 安装目录下的 bin 目录。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E5%9F%BA%E7%A1%80%E9%85%8D%E7%BD%AE.assets/image-20220319103120690.png)

[](#14-%E6%8F%90%E5%8F%96word%E9%87%8C%E9%9D%A2%E7%9A%84%E6%89%80%E6%9C%89%E5%BC%95%E7%94%A8%E6%96%87%E7%8C%AE%E7%9A%84%E7%BD%91%E7%AB%99)14. [提取 word 里面的所有引用文献的网站](https://gitee.com/link?target=https%3A%2F%2Frintze.zelle.me%2Fref-extractor%2F)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1.  点击选择文件，写人作文自己要提取的 word，== 注意：提交的 word 不能取消文献链接 ==

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220106164058390.png)

2.  选择要导出的引文格式

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E9%85%8D%E7%BD%AE%E5%8F%8A%E4%BD%BF%E7%94%A8.assets/image-20220106164218836.png)

3.  `Download`下载即可，然后在相关软件里面导入。

[](#15--zotero%E5%88%A9%E7%94%A8onedrive%E5%90%8C%E6%AD%A5)15 . zotero 利用 onedrive 同步
-------------------------------------------------------------------------------------

1.  注册一个 zotero 账号，登陆，如下勾选。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E5%9F%BA%E7%A1%80%E9%85%8D%E7%BD%AE.assets/image-20220115115707732.png)

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E5%9F%BA%E7%A1%80%E9%85%8D%E7%BD%AE.assets/image-20220115115312105.png)

2.  将`D:\appData\zoteroFile`下面的 storage 剪切到`onedrive`所在的文件夹，这样在`D:\appData\zoteroFile`里面就没有`storage`文件夹了，下面才能用命令在该文件夹下面建立该文件夹链接。
    
3.  用管理员身份打开`cmd`，使用命令`mklink /j "数据库所在的文件夹\storage" "onedrive文件夹\storage"`，即可将`zoteroFile`里面的 storage 指向`onedrive`里面的`storage`，`zoteroFile`里面只是一个链接文件，真正的文件在`onedrive`里面。软连接所在的文件夹就是在这里建立一个快捷链接，点击这个快捷链接就相当于到文件夹所在的真正位置而不用去打开文件的真正位置。
    

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E5%9F%BA%E7%A1%80%E9%85%8D%E7%BD%AE.assets/image-20220416190503922.png)如果使用了`zotfile`自定义了文件夹，那么只需要像上面那样将 zotfile 的文件夹剪切到云盘，再在本地建立软连接

4.  在另一台电脑上只需要将本地的这两个文件夹和云盘里面的文件夹建立软连接即可

== 注 ==：两台电脑上的数据保存的盘符和路径最好保持一致，即自定义的数据存储路径在两台电脑上保持一致（如在第一台电脑上数据的保存位置为`D:\appData\zoteroFil`，那么第二台电脑上也应该使用此路径，因为 zotfile 在重命名后的 pdf 文件路径使用的是绝对位置，如果两台电脑的数据保存位置不一致会导致 pdf 找不到），这样使用`zotfile`自定义文件保存位置同步后不会出现找不到文件的问题。

![](https://gitee.com/tughv/zotero-plug-in/raw/master/notes/zotero%E5%9F%BA%E7%A1%80%E9%85%8D%E7%BD%AE.assets/image-20220115115312105.png)