> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.bilibili.com](https://www.bilibili.com/read/cv14280731/)

> Huginn　　差点就放弃写 Huginn 篇了，一是我平时折腾的那些网站全是静态网页，feed43 就可以搞定了，Huginn 简直宰牛刀。

![](http://i0.hdslb.com/bfs/article/4cadb8593d38a5cd8d77914333ed826e689839c6.png)Huginn

　　差点就放弃写 Huginn 篇了，一是我平时折腾的那些网站全是静态网页，feed43 就可以搞定了，Huginn 简直宰牛刀。二是 Huginn 使用起来需要一定门槛，比如要有服务器，没服务器那就用云开发平台吧，还得备着 “梯”*zi，部署的时候得需要一些计算机知识吧，我就看个老头官网消息，感觉更没必要折腾 Huginn 了😂

　　先更新中篇的内容，就是关于 Huginn 如何使用。前篇关于 Huginn 的部署，我打算讲在 Heroku 里部署以及获取 Huginn 管理员权限。后篇是针对用 Heroku 部署 Huginn 产生的休眠问题如何解决，用服务器部署 Huginn 完全不用看后篇哈~

　　先说明一下哈，以下内容是**针对静态网页的抓取步骤指南**，如果需要抓取动态网页（大型网站有一些用的是动态，普通网站还是静态为主），其实就在以下步骤之前多一步，用 Phantom Js Cloud Agent 渲染动态网页成静态页面后接下文的步骤。

![](http://i0.hdslb.com/bfs/article/4adb9255ada5b97061e610b682b8636764fe50ed.png)

 **第一步，先抓取概要信息。**

![](http://i0.hdslb.com/bfs/article/3d2162a7f6568e7e5b900cb32b4a8d4c821ebc82.png)老 C 官网新闻

　　先看一下用来做例子的网站，Chage 的官网（我咋这么喜欢用 C 来开刀呢~😂~）

　　先登录 Huginn，然后在左上角处点击**创建新代理（New Agent）**

![](http://i0.hdslb.com/bfs/article/a0aa00538482439e47ca499923adc30b2bfd0d23.png) ![](http://i0.hdslb.com/bfs/article/15f900d3ac3a04981918f85336b42c0f398a9077.png)

　　然后**选择****代理类型（type）**，输入 web 就能出现 **Website Agent**，选择它。

　　这时出现具体设置的页面，大概分成三个区域，左上为填写代理基本信息与各个代理之间承接关系等等，左下为具体的代码，右边一大块都是帮助说明。**（帮助说明十分重要！一定要多看）**

![](http://i0.hdslb.com/bfs/article/b8d1beb635f3f3c321d665db4660099f5298971d.jpg)三大块

　　下面先看基本信息区。

　　**代理类型（Type）**不用动

　　**名称（Name）**自己随便起一个就行，比如 “第一步”，或者网站名，或者 “摘要”，自己能看明白的名字就好。

　　**日程（Schedule）**根据实际需要设置，比如你抓取的内容更新比较频繁，就把时间间隔设置的小一些，Every 5m、Every 10m 之类的。  

　　**控制（Controllers）**不用填写

　　**事件保留时间****（Keep events）**，实际使用要设置成 forever，要不工作几天就不工作了。  

　　**来源端（Sources）**，就是说你需要不需要其他代理的数据，一般创建第一个代理这项不用填。立即执行（Propagate immediately） 打勾。

　　**接收端（Receivers）**，就是说你这里抓取的信息要传递给下一步的代理，一般创建第一个代理这项不用填。

　　**场景分类（Scenarios）**，就是把这一系列的代理打个组这个分类，比较方便查看，可填可不填。

![](http://i0.hdslb.com/bfs/article/eb3cb24c240b271e61cb99a5389501becab1905c.png)基本信息![](http://i0.hdslb.com/bfs/article/4aa545dccf7de8d4a93c2b2b8e3265ac0a26d216.png)

　　代码区主要用到的有最右上角的**切换视图（Toggle View）**，**试运行（Dry Run）**，这里提供两种视图，一种是下面的这种带绿条的（图一），一种是纯代码的那种（图二）。

![](http://i0.hdslb.com/bfs/article/00c4f69df4054f11c00d03070a26903e494cd8ae.png)代码区（图一） ![](http://i0.hdslb.com/bfs/article/60bb7527b9e231e1f60ef07c6c458812652f1716.png)代码区（图二）

　　关于**切换视图（Toggle View）**有个小技巧，就是**用图二的视图写好代码，然后点击** **Toggle View，如果能正常切换回带绿条的视图，说明代码写的没问题，如果切换失败，提示出错什么的，就说明代码写的有问题，需要再检查一遍代码，尤其是符号。**

　　这个切换视图小技巧特别适合像我这种没写过代码的人，因为我对符号没意识，不是丢个, 就是丢个;“”，代码总是报错……😂

　　下面开始写代码。

![](http://i0.hdslb.com/bfs/article/46a4e26cbe198f641c2de53520851f6d3870bd48.png)

　　第一行 expected_update_period_in_days，我理解的应该是给代理设置一个更新周期，在这个周期里网页没有新消息更新，Huginn 会认定为网站没有工作（work），这项很鸡肋，不用管。

　　先**填写 url**，就是你要抓取的网页网址。

　　**类型（type）**，基本都是 html

　　**模式（mode）**，这里有三种，`all`、`on_change`、`merge。（具体见下图）`

![](http://i0.hdslb.com/bfs/article/ae0de08a62f80fef4d71ae62dec937e59e919eb8.jpg)模式（mode）

　　一般来说第一步抓取用的是 on_change 模式，到中间这一层需要上一步的数据传递过来所以要用混合模式（merge）。

　　下面该填写具体的抓取代码了，先看一下老头的网站，按 F12 调出查看器。

![](http://i0.hdslb.com/bfs/article/5a07973bcac0ebdd13abd122f0e307733f234252.jpg)

　　这里可以看出要抓取的内容都在 inf_box 这一层里面，里面包括网址信息，标题内容，时间信息等等。（如何用 F12 找到具体位置，我是凭感觉来的，反正是在中间位置，火狐浏览器右击有个检查，可以直接定位到大概位置。）  

　　下面先写**提取（extract）**里的 **url** 信息，从上图可以看到，网址在 class="inf_box" 的下面。

　　<div>  

　　　<a href="/information/media/detail-462.php">

　　根据 huginn 的帮助指南里面的举例：`"url": { "xpath": "//*[@class="blog-item"]/a/@href", "value": "."（我习惯用xpath来写，用css来写也是一样的），稍稍改一下就是下面这段代码：`

　　"url": {

    　   　"xpath": "//*[@class=\"inf_box\"]/a/@href",

     　 　"value": "."

   　 }

　　这里面的 //*[@class=\"inf_box\"]/a/@href，咋解释呢……，//* 就是网页前面的代码全部省略，只找 class 是 inf_box 的那部分，然后 /a/@href 对应的 <a href="/information/media/detail-462.php"> 这一行，value 用的 **.** 就是 <a href = 的所有值。

 **注：代码是灵活的，不唯一！**

 　   "url": {

 　　     "xpath": "//*[@class=\"inf_box\"]/a",

 　　     "value": "@href"

 　   }

　　这样写也一样可以抓出来网址，解释出来就是找 class 是 inf_box 的那部分，对应到后面的 < a，value 的值取得是 href 的值。

![](http://i0.hdslb.com/bfs/article/adf3962ff5f2750c60582eb8ce4752099f5f050a.png) ![](http://i0.hdslb.com/bfs/article/9c6e540c040fc4ba7557f3dc0f694bed1b905c1a.png)填好 url 部分

 　　点击右上角的 **Toggle View 来回切换几遍**，先保证代码没问题，然后点击 **Dry Run 试运行**。

![](http://i0.hdslb.com/bfs/article/9b2752937f8f31135bdcfc96b879d31bdc7d9614.png)

　　点击 **Dry Run。**

![](http://i0.hdslb.com/bfs/article/8da94d06debd91a5d10a733e1dbdb4153fd9ae77.png)

　　能看到正确的输出结果，url 那一行写的没问题，再**添加标题（title）**

![](http://i0.hdslb.com/bfs/article/a69125d9ad29e11273b8a9a4506632e4f5d9c24f.jpg)标题（title）

　　从上图可以看到，标题信息（title）在 class="inf_txt" 的旁边。

　　<p>12 月度、ラジオコメント出演情報！</p>

　　根据上面所讲的步骤，写出 title 的代码：

　    "title": {

　　      "xpath": "//*[@class=\"inf_txt\"]",

　　      "value": "string(.)"

　    }

　　**代码写法不唯一**，也可以写成下面这种：

　    "title": {

　　      "xpath": "//*[@class=\"inf_txt\"]",

　　      "value": "./node()"

　    }

　　解释一下这两种 value，一个是 string(.)，应该是指 class 是 inf_txt 里包含的所有字符串，再具体我也不能说清楚啦，我也没学过计算机…… 字符串是啥我也不懂…… 反正就大概这个意思啦。另一种是./node()，就是取括号外的值，<p>12 月度、ラジオコメント出演情報！</p> 这里面的 “12 月度、ラジオコメント出演情報！”正好在两个 <> 的外面，“./node()”正好可以用。

　　还可以用 normalize-space(.)，这个是去除文本中的空格和回车的值。

![](http://i0.hdslb.com/bfs/article/ca5eccc96ad10228c0e1c399fb7c55aae63ea63a.jpg)这里用./node()” 做例子

　　先点击右上角的 **Toggle View 切换几遍视图看看代码有没有问题，再点击 Dry Run 试运行。**  

 **下面贴出四种不同 value 的输出结果。**

![](http://i0.hdslb.com/bfs/article/bee1832547b5bba0bda4bf43d7eca4a15d3f85b3.jpg)"value": "./node()" ![](http://i0.hdslb.com/bfs/article/8c5f1f4c41a92b7c070a1c954c2d479e720b1b88.jpg)"value": "normalize-space(.)" ![](http://i0.hdslb.com/bfs/article/4def66c096bb49e020202870450f657d5a9707d6.jpg)"value": "string(.)" ![](http://i0.hdslb.com/bfs/article/158d2fd056fb57cd1ca94ecf0ad73bab5010ccb6.jpg)"value": "."

　　嘛，value 就那么几种写法，大不了挨个试一下看看哪个效果好 😂

　　再根据上面的步骤把日期信息也抓出来。

![](http://i0.hdslb.com/bfs/article/6df8deb25d89cdb35c900de09b9739723f8ae638.png)花式写法

　　**实际使用中，没必要把 value 值折腾这么多，我做例子才弄这么多 value 值，**千万别被我带跑偏。😂

　　Dry Run 一下。

![](http://i0.hdslb.com/bfs/article/262fa94e3a9b672b26f0dc1bbe8480d9ea8f1ef9.png)不错，都正常

　　这时候还有一个问题，url 抓出来是没有域名的，这在 RSS 阅读器里不认的，接下来需要给一个**模板（template）**。**模版和提取（extract）是同级，写在**提取（extract）的下方。****

　　  "template": {

　　　    "url1": "{{url | to_uri: _response_.url}}"

　　  }

　　指定一个新的 **url1**，url1 是刚刚抓取的 url 的 “延伸”，我感觉我解释不清了，可以理解为给刚刚抓的 url 一个“前缀” 把网址补全。**这里一定要注意别丢了符号** ，我总是忘记大括号还有逗号。

![](http://i0.hdslb.com/bfs/article/b4d7c69f7987aeb7ab7afe55499caac53e3dbdcf.jpg)添加模板（template） ![](http://i0.hdslb.com/bfs/article/d1aeed3902f4d339b532795999ad388aa610d2af.png)层级关系 ![](http://i0.hdslb.com/bfs/article/f3991036c60c17d206137c01d59cc20184fb96e7.jpg)输出结果

　　大功告成！url1 已经显示出正确的网址！

　　如果仔细看的话，会发现这样抓出来的和 feed43 抓出来的东西是一样的。😂

![](http://i0.hdslb.com/bfs/article/a731725f4218bdcfec6185da4ff3a27f85babadf.jpg)feed43 抓取结果![](http://i0.hdslb.com/bfs/article/4aa545dccf7de8d4a93c2b2b8e3265ac0a26d216.png)

　　**到了这里，可以进行第三步直接输出 XML 订阅地址，因为 RSS 阅读器都有获取全文功能，我们把 url1 这个网址告诉 RSS 阅读器，阅读器会自动加载出全文，如果阅读器获取的全文排版很乱，我们才会做第二步，就是用 Huginn 获取全文，再输出 XML 订阅添加到阅读器里。**

![](http://i0.hdslb.com/bfs/article/4aa545dccf7de8d4a93c2b2b8e3265ac0a26d216.png)

　　**第二步，根据刚刚获取到的 url1 网址，获取文章全文。**

 **创建新的代理。**

![](http://i0.hdslb.com/bfs/article/d60193ea43605756e0f84ecf050a2582f8762361.png)

　　这里要填写**来源（Sources）**了，来源就是刚刚第一步创建的代理。其他的根据自身情况填写。  

　　代码区要注意，**url 要写刚刚获得的 url1 地址 {{url1}}，模式要选择 merge。**

![](http://i0.hdslb.com/bfs/article/1a0f4c67291b2026cb8467858021ee11c6d4b223.png)

　　先进入网站看一下 F12，找到正文所对应的位置。

![](http://i0.hdslb.com/bfs/article/bc98e2d06b77320a73834201d4555fe55806670a.jpg)

　　可以找到正文内容都在 class="inf_detail_txt" 的代码中。

　　<p> 現在決まっているラジオコメント出演情報です。……</p>

　　所以在 extract 里添加 article 或者 text，名称可以自己随便取，只要你能记住就行。

　　根据上面讲到的内容写好代码。

![](http://i0.hdslb.com/bfs/article/376ce0241347e1d07447aa7eb52ccc716b85d26b.png)

　　**Dry Run** 一下。  

![](http://i0.hdslb.com/bfs/article/fe9c31612925de189115abd2a55c41f097a164a9.png)

　　这时出现这样的界面，随便**点击一个上面的 url。**

![](http://i0.hdslb.com/bfs/article/1c76f6852c68aec1f74bb77c0b8ccdaa962e0c1d.png)

　　这时**再点击 Dry Run**。

　　下面列出四种不同 value 值的输出结果。

![](http://i0.hdslb.com/bfs/article/78e75efa21d1566e916823ac853f391b6cd27574.jpg)"value": "./node()" ![](http://i0.hdslb.com/bfs/article/42ac347bac94e40727c32804dad8a2cafbe6cd18.jpg)"value": "normalize-space(.)" ![](http://i0.hdslb.com/bfs/article/046ce9214ded0007e56ae64aafe48dcbe503914a.jpg)"value": "string(.)" ![](http://i0.hdslb.com/bfs/article/923aba75f9904899d32dfdfa14ba6e41bc319c22.jpg)"value": "."

　　通过对比可以看出，"value": "./node()" 是非常完美的。"value": "string(.)" 不包括 < br > 的换行符，这样排版会乱。"value": "normalize-space(.)" 只有文本信息，这样排版很密。"value": "." 是最完整的信息。

　　用 "value": "./node()" 或者 "value": "." 都可以。

　　保存一下，这样第二步就完成了。

![](http://i0.hdslb.com/bfs/article/4aa545dccf7de8d4a93c2b2b8e3265ac0a26d216.png)

　　**终于到第三步也就是最后一步，输出 RSS 订阅地址！**码字码的我都累了……

 **再创建一个新的代理。选择 Date Out Agent**

![](http://i0.hdslb.com/bfs/article/dd4284a89ad3b56104f646982db30c9ccc2fe48e.png)Date Out Agent

　　可能有人要问了，下面不是有个 RSS 嘛，那个不是输出 RSS 订阅啊，是把别人的 RSS 作为来源输入进来……  

　　基本信息和之前差不多，**来源选择刚刚创建的代理。如果你跳过了第二步，那来源就是第一步的代理，如果你做了第二步用 huginn 来获取全文，此时的来源就是第二步的代理。**

![](http://i0.hdslb.com/bfs/article/4df380149d1aea1665403a886c62866b8756bbc9.png)来源要选对

　　剩下的代码就简单多了。

　　**secrets：是输出 XML 文件的文件名，可以改个自己好记的名称。**

　　**template 部分****见下图，都是自己自命名的。**

 **item 部分要仔细填写！**

 title 是第一步代理里面的 title。

　　description 是第二步代理里的 article，如果没做第二步，可以把这行删掉不写。

　　link 是第二步代理里面的 url。

　　pubDate 是第一步代理里面的时间。

　　可能有人要问了，为啥这里又能指定第一步代理里的信息，又能指定第二步代理的信息，还记得第二步里模式 mode 选的是 merge 吗？选择了 merge 后，就把这两步代理的信息都合并了，所以这里可以各种指定。

![](http://i0.hdslb.com/bfs/article/40594b12dfca532e0c042612fd6967df66c743af.png)

　　**保存**

　　点击你刚刚创建的 RSS 输出代理，就看到输出的 xml 文件了。

![](http://i0.hdslb.com/bfs/article/2605f56f181f0fdd0cd067fbe01a05199d66a9ac.jpg)

　　把这个 xml 地址添加到你的 RSS 阅读器里就全部完成了！

![](http://i0.hdslb.com/bfs/article/4aa545dccf7de8d4a93c2b2b8e3265ac0a26d216.png)

　　再补充一点，如果把上面的都做完后发现 events 里是空的没抓到信息，不急，**run** 一下第一步创建的代理。

![](http://i0.hdslb.com/bfs/article/3b31acf716f4dafdb1da63dacd0c23ad7d1c520e.jpg)

　　Huginn 就自动刷新了，然后就能看到新的 events 出现~

![](http://i0.hdslb.com/bfs/article/4aa545dccf7de8d4a93c2b2b8e3265ac0a26d216.png)

　　哎哟我的妈呀，可算是把 huginn 的 RSS 用法写完了，看不懂没关系，多动手写一写，试一试，报错就检查符号有没有忘记，好像没啥要再强调的东西了。

　　希望这篇小文能帮到有需要的人~😂~

![](http://i0.hdslb.com/bfs/article/4adb9255ada5b97061e610b682b8636764fe50ed.png)

　　【安利向】RSS 的世界：[cv13449742](https://www.bilibili.com/read/cv13449742)

　　【进阶篇】RSS 的世界：RSSHub 篇：[cv13543035](https://www.bilibili.com/read/cv13543035)

　　【进阶篇】RSS 的世界：Feed43 篇：[cv13544223](https://www.bilibili.com/read/cv13544223)