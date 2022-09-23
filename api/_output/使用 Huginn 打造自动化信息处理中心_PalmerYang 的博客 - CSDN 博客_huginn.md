> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/unreliable_narrator/article/details/124309672)

一. Huginn 简介
============

在北欧神话中，奥丁的肩膀上坐着两只乌鸦，一只名叫 Huginn，一只名叫 Muninn。这两只乌鸦告诉奥丁他们的所见所闻，毫无遗漏。奥丁在黎明时派出它们，它们飞遍全世界然后在晚餐之前回来汇报，因此，奥丁能知晓很多事情。在 [Huginn](https://github.com/huginn/huginn) 的项目主页上，作者对它有详细的介绍。我们同样可以通过 Huginn 创建不同的代理，通过这些代理发送 HTTP 请求获得相关数据，然后将获取到的数据进行处理，就可以在互联网上面收集到各类我们需要的信息了。通过 Huginn 我们可以比较方便的实现如下功能:

*   监控你关心的事项例如知乎、微博、贴吧等平台指定的信息，一旦监控到信息，邮件通知你。
*   监控各大购物平台商品信息，一旦发现折扣信息，邮件通知你。
*   支持各种形式的发送和接收 WebHooks。
*   抓取网页内容并且在它们发生变化时发送邮件给你。
*   将获得的数据进行相应的格式处理并输出，例如 RSS。
*   跟踪天气的变化，如果监测到明天要下雨或下雪，就会发邮件提醒你。

总得来说，Huginn 可以帮助我们做好两件事情，一是定制化推送或提醒，二是聚合数据。

### 1. 定制化推送或提醒

首先，定制化推送或提醒就像你平时设定闹钟一样，设定好时间或条件后，当时间或条件满足时，Huginn 就会把信息推送给你，或提醒你该去做某件事情。比如说，明天下雨，提醒你带伞；电视剧或漫画更新，提醒你去观看或直接推送给你；感兴趣的商品降价，提醒你去购买；发生有趣的热点新闻，也会推送给你… 诸如此类生活中很多零散的信息地处理，我们每天都在接收并处理这些信息。

### 2. 聚合数据

聚合数据是指在将自己关注的包括但不仅限于微信公众号、知乎、简书、豆瓣、微博、Instagram 等相关平台的资讯信息收集起来，在同一个平台进行阅读，RSS 技术就能实现上述的功能，但是因为很多网站官方都没有提供 Rss 支持，那么可以通过 Huginn 将自己关注的信息渠道都制作成一个个 RSS 源，然后在 RSS 阅读器中集中阅读。

二. 安装 Huginn
============

### 1. 常规手动安装 Huginn

如果是常规安装方式，需要安装依赖包、ruby 环境、数据库、nginx、huginn 及各种配置。容易出错，因此不推荐此种安装方式，具体安装步骤可以参考[官网教程](https://github.com/huginn/huginn/wiki/Novice-setup-guide)。

### 2.[Docker](https://so.csdn.net/so/search?q=Docker&spm=1001.2101.3001.7020) 安装 Huginn(推荐)

1.  首先你需要安装配置好 Docker 环境。
    
2.  然后通过 docker 来部署:
    
    ```
    docker search huginn/huginn
    docker pull huginn/huginn
    docker run -it -p 3000:3000 huginn/huginn
    ```
    
3.  然后在浏览器打开`http://localhost:3000`即可看到效果，使用默认账号登录：
    
    ```
    用户名： admin
    密码：password
    ```
    

### 3.Huginn 更换 Mysql 数据库

安装 Huginn 时会附带有一个轻量的数据库，但 Huginn 一删里面的数据就没了，所以非常有必要将 Huginn 的数据存储在 mysql 中可以方便我们对数据进行管理。

1.  在 docker 中配置好 mysql 和 huginn。
    
2.  创建 huginn 容器时指定 mysql 数据库的信息。
    
    ```
    docker run  --name huginn -p 3000:3000 -e MYSQL_PORT_3306_TCP_ADDR=172.0.0.1 -e HUGINN_DATABASE_NAME=huginn -e HUGINN_DATABASE_USERNAME=root -e HUGINN_DATABASE_PASSWORD=123456 huginn/huginn
    ```
    
3.  最后在浏览器中输入 http:// 你的服务器 IP:3000 并访问。
    

### 4. 将 huginn 部署到 Heroku

[Heroku]([About Heroku | Heroku](https://www.heroku.com/about)) 是一个支持多种编程语言的云平台即服务，该平台提供了一些免费的云计算服务，如果我们不想自己购买云服务器，可以将 huginn 部署到 Heroku。如果你要使用免费方案的话，你需要注意以下几点：

*   使用 Heroku 免费方案的用户，其每个网站在 30 分钟内无人访问后便会自动关闭，再有人访问时才会自动重新打开，因此为了使 Huginn 网站能长时间运行，可以使用类似 [uptimerobot](https://uptimerobot.com/) 的[网站监控](https://cloud.tencent.com/product/cat?from=10680)服务，不停地 ping 你的 Huginn 网站地址；
*   Heroku 免费方案只允许用户所有的应用每个月运行的总时长不超过 550 个小时（绑定信用卡的用户可额外再获得 450 个小时），这意味着你无法保证部署好的 Huginn 网站每个月每天都在运行，因此，你可选择绑定信用卡，或者让你的 Huginn 网站每天只允许 18 个小时，这样的话，你的网站每天都可以在运行；
*   Heroku 免费方案提供给用户的 Postgres [数据库](https://cloud.tencent.com/solution/database?from=10680)只有 5M，存储的数据不能超过 10000 行，因此你需要控制 Agent 生成的事件的保留周期，同时限制数据库中 Agent 日志文件的长度，比如`heroku config:set AGENT_LOG_LENGTH=20`。
*   Huginn 安装在 heroku 的过程中默认使用的是 SendGrid 的邮箱服务器，这还需要我们添加 SendGrid 插件才能正常使用，但是添加插件需要先添加信用卡，因此，非信用卡用户无法使用 SendGrid 的邮箱服务器，建议添加其它邮箱服务器，比如，gmail 邮箱服务器。

##### 部署到 Heroku 的操作步骤：

1.  注册 [Heroku](https://www.heroku.com/) 平台账号，然后下载安装 [Heroku Toolbelt](https://toolbelt.heroku.com/)；
2.  远程登录 Heroku：`heroku login`
3.  创建 app：`heroku create xxx`（xxx 为 app 的名字，下同）；
4.  将 app 下载到本地：`heroku git:clone --app xxx`
5.  将 [huginn](https://github.com/cantino/huginn) 源代码全部下载拷贝到本地 app 的文件夹内；
6.  进入 app 文件目录，依次执行命令：`cp .env.example .env` 和`bundle`；
7.  提交代码变更：`git add .`、`git commit -am 'commit code'`；
8.  最后，执行脚本：`bin/setup_heroku`，完成部署。

> 如果嫌自己部署过于麻烦，也可以参考 [Huginn 官方(https://github.com/huginn/huginn#deployment) 的一键部署到 Heroku 平台的方案。

##### 使用自己的邮箱[服务器](https://cloud.tencent.com/product/cvm?from=10680)

在安装过程中默认使用的是 SendGrid 的邮箱服务器（安装后需要自行配置），你也可以使用其他邮箱服务器，下面以谷歌邮箱服务器为例，需要进行以下配置：

`heroku config:set SMTP_DOMAIN=google.com`  
`heroku config:set`[`[email protected]`](https://huginn.cn/cdn-cgi/l/email-protection)  
`heroku config:set SMTP_PASSWORD=somepassword`  
`heroku config:set SMTP_SERVER=smtp.gmail.com`  
`heroku config:set`[`[email protected]`](https://huginn.cn/cdn-cgi/l/email-protection) `# 指定显示的发件人邮箱地址`

三. Huginn 基本概念
==============

如果将 Huginn 比如成一个数据加工工厂，每个 Agents 就像是一个个具有不同功能的车间，Agent 可以接收数据并对数据进行加工，然后将加工好的数据输出。一组串联起来的 Agents 通过不断传递加工 Event(产品) 组成了一条流水线 (scenarios)。

### 1.Agent：

Agent 就是一个代理，例如抓取网页数据，清洗网页数据，输出为 Rss 源，这里的每一步都相当于是一个不同种类的车间，他们可以彼此依赖形成流水线，也可以单独工作。

### 2.Scenario：

Scenario 就是一系列 Agent 的集合，就相当于是包含了很多车间的流水线，主要是对一系列 Agent 的集合进行归类，方便识别。

### 3.Event：

每一个 Agent 执行一次，输出就是 Event，相当于是车间加工出来的产品，前一个`车间/Agent`输出的 Event 可以传递给下一个`车间/Agent`使用，再次进行加工。

> 显然，Huginn 能做什么，不能做什么，关键看它提供了哪些 Agent。

四. 入门实例 - Huginn 下雨天通知带雨具
=========================

例如，我们想把某个城市的天气预报数据抓取，对数据进行分析，判断明天是否会下雨，然后通过邮件提前通知明天带雨伞。 那么，我们需要写三个 Agents，第一个 Agent 抓取天气预报的数据，第二个 Agent 会对天气预报的数据进行判断，判断明天是否会下雨， 最后一个 Agent 通过邮件通知明天下雨需要带雨伞。在 Huginn 中，会按照下图所示的流程进行工作：  
![](https://img-blog.csdnimg.cn/img_convert/9db77ba80872b05e3348ae30bd1fb479.png)

### 1. 创建抓取天气数据的 Agent

#### 创建 Agent 代理

先登录 Huginn，然后在左上角处点击创建新代理（New Agent）:  
![](https://img-blog.csdnimg.cn/img_convert/aaf54baf302cda5d05dc948bee8658eb.png)

#### 选择代理类型

由于我们是对 html 网页类型进行解析, 因此创建一个 Website 的代理:  
![](https://img-blog.csdnimg.cn/img_convert/a0fd09ed53ee8edb5a7cad33245eb49f.png)

#### 基本信息填写

![](https://img-blog.csdnimg.cn/img_convert/f7bd07180cec5bead3e5b741b4308635.png)

*   红色部分为基本信息功能。
*   黄色部分为指导说明文档。
*   蓝色部分为抓取选项配置。
*   绿色部分为调试保存功能。

下面先看基本信息区主要有如下几个选项:

*   Type(代理类型): 选择代理的类型上一步我们选择的是 Website, 因此这里就不再选择了。
*   Name(名称)：给这个 agent 取个名字，自己随便起一个就行。
*   Schedule(日程)：调度周期，表示在什么时候自动执行这个 agent，比如 Every 1d 表示每一天执行一次、Every 2h 表示每 2 小时执行一次、8pm 表示每天下午 8 点执行等等；选择 3pm，每天下午 3 点执行一次，根据实际需要设置，比如你抓取的内容更新比较频繁，就把时间间隔设置的小一些，Every 5m、Every 10m 之类的。
*   Controllers(控制): 除了系统定义之外，此代理上面的计划可以由这些用户定义的代理运行或控制，不用填写。
*   Keep events(事件保留时间)：表示事件保留的时间；我们从网页上面获取到的信息都是一个 event，Huginn 会把这些 event 保留在本地，你可以通过这个参数来设置这些 events 在本地保留多少时间，超过这个时间，Huginn 会把数据清除，暂时设置成 forever 永不清除。
*   Sources(来源端)：表示这个 agent 处理的数据来源是哪个 agent。我们现在创建的 agent 是第一个 agent，所以不需要从其他 agent 传递数据（也就是上面说的 events）过来，所以这个留空。
*   Receivers(接收端)：表示这个 agent 处理完数据之后把这些数据传入到哪个 agent。用来转化数据，数据转化完之后，可能还需要其他 agent 把这些数据做进一步的转化。
*   Scenarios(场景分类)：表示这个 agent 是数据哪个 Scenario 的，就是把这一系列的代理打个组这个分类，比较方便查看。

#### Options 配置填写

Options：这个非常关键，就是通过这个配置文件（JSON）来进行网络请求和数据解析相关的操作的，Options 配置其实就是一个 JSON 文件，最右上角的切换视图（Toggle View）可以切换视图和源码的编辑模式:  
![](https://img-blog.csdnimg.cn/img_convert/0f9396ec98dfb7853c432c19f24c238d.png)  
Website Agent 的 Options 主要的元素有如下：

*   url：网站地址，表示我需要从哪个网站获取数据。
*   type：数据解析的类型，支持的类型有 `xml`、`html`、`json`、`text` 四种，当前网址返回的是 html，所以这里我们填写 `html`。如果其他场景，返回的类型可能就是 `json` 或者 `xml`了, 需要具体分析。
*   mode：表示获取数据的模式，这里选择 `on_change`。
    *   on_change：在数据有更改时才会获取作为 events。
    *   merge：把新数据和输入的数据进行合并。
    *   all：获取所有数据。
*   extract：用来配置（JSON）从这个网站解析出真正我们想要的数据。如果 `type` 是 `html`，则每个数据通过 `css` 选择器或者 `xpath` 来定位元素的位置然后解析出真正的数据。

打开[深圳天气预报, 深圳 7 天天气预报, 深圳 15 天天气预报, 深圳天气查询 (weather.com.cn)](http://www.weather.com.cn/weather1d/101280601.shtml)，f12 呼出开发者工具，然后分析网页的内容，可以看到元素对应的关系如下:  
![](https://img-blog.csdnimg.cn/img_convert/61c23938e43cc337f7324c7027e8d244.png)

根据如上网页的对应关系，编写 Options 如下:

```
{
	"expected_update_period_in_days": "2",
	"url": "http://www.weather.com.cn/weather1d/101280601.shtml",
	"type": "html",
	"mode": "on_change",
	"extract": {
		"day": {
			"css": "#today .clearfix li[1] .wea",
			"value": "text()"
		},
		"day_temperature": {
			"css": "#today .clearfix li[1] .tem span",
			"value": "text()"
		},
		"day_wind": {
			"css": "#today .clearfix li[1] .win span",
			"value": "normalize-space(.)"
		},
		"night": {
			"css": "#today .clearfix li[2] .tem span",
			"value": "text()"
		},
		"night_temperature": {
			"css": "#today .clearfix li[2] .win span",
			"value": "normalize-space(.)"
		},
		"night_wind": {
			"css": "#today .clearfix li[2] .wea",
			"value": "text()"
		}
	}
}
```

获取抓取到的结果:  
![](https://img-blog.csdnimg.cn/img_convert/ca00a886aa7ae7b2c84664516c6a2028.png)

> 如果想看抓取到的页面具体的数据有哪些可以在 extract 中定义一个`"html内容": {"css": "html","value": "."}`将 html 标签中的所有内容输出进行查看。

**Json 格式数据解析**

1.  如果网页获取到的是如下的 JSon 数据：
    
    ```
    { "results": {
        "data": [
          {
            "title": "Lorem ipsum 1",
            "description": "Aliquam pharetra leo ipsum."
            "price": 8.95
          },
          {
            "title": "Lorem ipsum 2",
            "description": "Suspendisse a pulvinar lacus."
            "price": 12.99
          },
          {
            "title": "Lorem ipsum 3",
            "description": "Praesent ac arcu tellus."
            "price": 8.99
          }
        ]
      }
    }
    ```
    
2.  填写抓取规则：
    
    ```
    "extract": {
      "title": { "path": "results.data[*].title" },
      "description": { "path": "results.data[*].description" }
    }
    ```
    
3.  抓取到的数据：
    
    ```
    [
      {
        "title": "Lorem ipsum 1",
        "description": "Aliquam pharetra leo ipsum."
      },
      {
        "title": "Lorem ipsum 2",
        "description": "Suspendisse a pulvinar lacus."
      },
      {
        "title": "Lorem ipsum 3",
        "description": "Praesent ac arcu tellus."
      }
    ]
    ```
    

### 2. 过滤天气数据 Agent

#### 创建 TriggerAgents

过滤 Agent 用的是`TriggerAgent`。建立一个 TriggerAgent。把刚才创建的 WeatherAgent 设置为源。TriggerAgents 包含一套规则，所有这一切都必须为触发匹配。![](https://img-blog.csdnimg.cn/img_convert/1464648308df12ef5d8da274ea9ffefd.png)

#### Agents 配置填写

keep event 这里选择的是 false，意思是不生成过滤之后的事件，直接传递 message 的内容给下一个 agent。如果你希望对过滤后余下的信息进一步利用，比如再次过滤之类，可以选择 true 以保留事件。`type`指的是类型，regex 指的是正则匹配，系统会检测上一个 agent 生成的内容（这里选择的是`path：title`，意思是把传递过来的事件中的 title 作为过滤的对象），和`value`中内容进行比较，如果这个 event 中包含这些`value`，那么生成事件，否则不生成。`value`中的竖分割线指的是或的意思，出现其中任何一个词即可通过过滤器，生成事件。!regix 指的是不匹配，它会检测`path`和`value`的相似程度，如果`path`中出现`value`的值，则不输出，反之，则通过过滤器并输出、生成事件。  
![](https://img-blog.csdnimg.cn/img_convert/a7c2e57be1aa4277738495a132fc5dd0.png)

### 3. 通知用户的 Agent

将 huginn event 的内容推送到通知平台。这样的服务商比较不错的有两个：

*   邮件 agent。
*   slack agent。

其中邮件推送最经济实惠，不受平台约束；slack 是一个和企业微信比较像的国外交流软件，可能面临着封杀的危险，但是功能丰富，支持桌面端、Chrome 插件、iOS 和 Android 端，界面漂亮，并且可以自己选择把消息推送到哪一个群组。

五. 进阶实例抓取 Github 点赞最多的项目列表生成 Rss
================================

抓取 Github 数据生成 Rss 需要进行三个步骤也就是需要三个 Agent:

1.  获取 Github 点赞最多的十条项目列表数据的 Agent。
    
2.  根据列表数据获取项目详情数据的 Agent。
    
3.  将数据组合生成 Rss 数据进行输出的 Agent。  
    ![](https://img-blog.csdnimg.cn/img_convert/e3d5d994f1112728722e6bd68cd486d7.png)
    

> 以下内容是针对静态网页的抓取步骤指南，如果需要抓取动态网页（大型网站有一些用的是动态，普通网站还是静态为主），其实就在以下步骤之前多一步，用 Phantom Js Cloud Agent 渲染动态网页成静态页面后接下文的步骤即可。

### 1. 创建 Agent 抓取列表数据

#### 新建列表页的 Agent

先登录 Huginn，然后在左上角处点击创建新代理（New Agent）:  
![](https://img-blog.csdnimg.cn/img_convert/a6aaef4780142084ef192a255b00abfc.png)

#### 选择代理类型

由于我们是对 html 网页类型进行解析，因此创建一个 Website 的代理:  
![](https://img-blog.csdnimg.cn/img_convert/bbd1d2be0ea14cdf703843511fdabbde.png)

#### 基本信息填写

抓取 [github star 最多 star 的项目](https://github.com/search?q=stars%3A%3E10000)

*   1. 通过 F12 查看元素，可以看到左边每一条项目对应的是右边源代码里面 class 为 repo-list 的 ul 标签中的 li 标签，对应关系如下:  
    ![](https://img-blog.csdnimg.cn/img_convert/0fdefe51ec95d6cedd6a2468807c01a7.png)
    
*   2. 编写解析规则，通过 Css 选择器和 Xpath 进行元素定位都可以。
    
    *   使用 Css 选择器进行元素定位取出数据:
        
        ```
        {
          "expected_update_period_in_days": "2",
          "url": "https://github.com/search?q=stars%3A%3E10000",
          "type": "html",
          "mode": "on_change",
          "extract": {
            "title": {
              "css": ".repo-list .v-align-middle",
              "value": "text()"
            },
            "url": {
              "css": ".repo-list .v-align-middle",
              "value": "@href"
            },
            "desc": {
              "css": ".repo-list  .mb-1",
              "value": "text()"
            },
            "stars": {
              "css": ".repo-list .mr-3 .Link--muted",
              "value": "text()"
            }
          }
        }
        ```
        
    *   使用 xpath 进行元素定位取值:
        
        ```
        {
          "expected_update_period_in_days": "2",
          "url": "https://github.com/search?o=desc&q=stars%3A%3E10000&s=stars&type=Repositories",
          "type": "html",
          "mode": "on_change",
          "extract": {
            "title": {
              "xpath": "//*[@id=\"js-pjax-container\"]/div/div[3]/div/ul/li[*]/div[2]/div[1]/div[1]/a",
              "value": "string(.)"
            },
           "url": {
             "xpath": "//*[@id=\"js-pjax-container\"]/div/div[3]/div/ul/li[*]/div[2]/div[1]/div[1]/a",
              "value": "@href"
            },
            "desc": {
              "xpath": "//*[@id=\"js-pjax-container\"]/div/div[3]/div/ul/li[*]/div[2]/p",
              "value": "normalize-space(.)"
            },
            "stars": {
              "xpath": "//*[@id=\"js-pjax-container\"]/div/div[3]/div/ul/li[*]/div[2]/div[2]/div/div[1]/a",
              "value": "normalize-space(.)"
            }
          }
        }
        ```
        

> *   title 和 url,desc，stars 表示对抓取字段映射的名称，可随意命名；
> *   属性用 @属性名进行取值 @href 表示抓取对应 css 标签的 href 属性值，还有 @src，@title 等等；
> *   如果要抓取对应标签的值，可填`.`(包括 html 代码的全部内容），`string(.)`（只包含对应标签的值），text() 等同 string(.)
> *   normalize-space 是 xpath 的语法可以去除多余的空格。

*   3. 调试，点击 dry run:  
    ![](https://img-blog.csdnimg.cn/img_convert/3844da9d2b294c1d0fc000929a92270b.png)
*   4. 可以看到我们抓取到的数据了:  
    ![](https://img-blog.csdnimg.cn/img_convert/7acd217a2888c2c03ca8a2e3f15f61fc.png)

然后点击 save 保存，保存后 run 一下，然后就会有生产出很多 events，就是获取到的数据。如果没有获取到可能是数据库的问题。这里我们已经抓到 Github 列表页的数据了，下面我们根据列表页抓到的的 Url 取去抓详情页的数据。

### 2. 创建 Agent 抓取 GIthub 项目的详情页

#### 新建详情页的 Agent

同样的，Type 选择`Website Agent`，由于详情是需要依赖列表中跳转详情的列表链接，Sources 选中刚才创建的列表 Agent，选择框勾选好:  
![](https://img-blog.csdnimg.cn/img_convert/17eacec212aac1061fa836e89a2eb0bd.png)

#### 根据依赖的 Agent 获取详情页数据

{{url}}即第一个 Agent 传过来的超链接参数，需要用到第一个 agent 的参数需要用 {{}} 包起来就可以了，这里 mode 一定填写 merge，这样两个 Agent 的字段就组合到一起了:  
![](https://img-blog.csdnimg.cn/img_convert/90c25e6e8a2fa34de07c699c1ea413a5.png)

```
{
  "expected_update_period_in_days": "2",
  "url": "https://github.com{{url}}",
  "type": "html",
  "mode": "merge",
  "extract": {
    "hovertext": {
      "css": "html",
      "value": "."
    }
  }
}
```

#### 调试详情页 Agent

同样的选择一个接受到的 event 测试一下  
![](https://img-blog.csdnimg.cn/img_convert/edccf6c10432cd8af97f8f5832d6aed0.png)

可以看到数据已经组合起来了:  
![](https://img-blog.csdnimg.cn/img_convert/63eea594b2e2c4b1272234dff5441426.png)

#### 保存详情页 Agent

点击 Save 保存，此时我们点击 github 列表数据 Agent 的 run 功能生成数据:

![](https://img-blog.csdnimg.cn/img_convert/2ed44321fb2c4318dde541641c976173.png)

查看生成的 Events 数据:

![](https://img-blog.csdnimg.cn/img_convert/a900d7da8875299b375b11d4d9232539.png)

可以看到列表 Agent 的时候也将详情的 Agent 进行执行了，并且将数据合并生成:

![](https://img-blog.csdnimg.cn/img_convert/cc1141cc1dad8e6040de5facda9a2a1c.png)

### 3. 创建输出成 RSS 数据的 Agent

#### 新建 Rss 输出的 Agent

Type 选择 Data output Agent  
![](https://img-blog.csdnimg.cn/img_convert/210df3bb18ddabcdc1d0276df88e90ca.png)

#### 依赖详情页 Agent

Sources 选择详情页 Agent，secrets 填写 RSS 地址自定义的末尾名称，item 下就是 RSS 中的每一条信息了，填写上对应参数，其他默认即可。最后点击保存  
![](https://img-blog.csdnimg.cn/img_convert/08a7df400a010bd07e3bfcec77548ca7.png)

```
{
  "secrets": [
    "Github"
  ],
  "expected_receive_period_in_days": 2,
  "template": {
    "title": "Github点赞数前十名排行榜",
    "description": "本数据来自于GitHub官方",
    "item": {
      "title": "{{title}}",
      "description": "Secret hovertext: {{hovertext}}",
      "link": "{{url}}"
    }
  },
  "ns_media": "true"
}
```

至此，一个专属 RSS 源就已生成

#### 添加到 Rss 源到 Rss 阅读器

点击 Agent  
![](https://img-blog.csdnimg.cn/img_convert/38c3804881f3843ddcb69c8fd90293be.png)  
点击 Agent 就能看到下图所示，把它添加到 RSS 阅读器上去吧。  
![](https://img-blog.csdnimg.cn/img_convert/7ba81b905d7b51ca8d1fbf4ccb692986.png)  
后续只要定时或者是手动执行第一个获取列表数据的 Agent 就回去执行后续的两个 Agent 生成 Rss 数据源，通过 RSS 阅读器进行订阅我们就可以看到抓取的信息流了。

六. 补充知识 Html 元素定位
=================

上文中笔者使用了 Css 选择器来定位元素，关于在 HTML 中定位元素常用的方式有三种正则表达式，xpath 提取，css 选择器。之前笔者在 Python 爬虫的相关文章中也有专门的讲解，有兴趣的同学欢迎前去考古。

### 1.Css 选择器定位元素

在 CSS 中，选择器是一种模式，用于选择需要添加样式的元素。Css 的定位更灵活，因为他它用到的更多的匹配符和规格。“CSS” 列指示该属性是在哪个 CSS 版本中定义的。（CSS1、CSS2 还是 CSS3。）

<table><thead><tr><th>选择器</th><th>例子</th><th>例子描述</th><th>CSS</th></tr></thead><tbody><tr><td>.class</td><td>.intro</td><td>选择 class=“intro” 的所有元素。</td><td>1</td></tr><tr><td>#id</td><td>#firstname</td><td>选择 id=“firstname” 的所有元素。</td><td>1</td></tr><tr><td>*</td><td>*</td><td>选择所有元素。</td><td>2</td></tr><tr><td>element</td><td>p</td><td>选择所有<p>元素。</p></td><td>1</td></tr><tr><td>element,element</td><td>div,p</td><td>选择所有 元素和所有<p>元素。</p></td><td>1</td></tr><tr><td>element element</td><td>div p</td><td>选择 元素内部的所有<p>元素。</p></td><td>1</td></tr><tr><td>element&gt;element</td><td>div&gt;p</td><td>选择父元素为 元素的所有<p>元素。</p></td><td>2</td></tr><tr><td>element+element</td><td>div+p</td><td>选择紧接在 元素之后的所有<p>元素。</p></td><td>2</td></tr><tr><td>[attribute]</td><td>[target]</td><td>选择带有 target 属性所有元素。</td><td>2</td></tr><tr><td>[attribute=value]</td><td>[target=_blank]</td><td>选择 target=“_blank” 的所有元素。</td><td>2</td></tr><tr><td>[attribute~=value]</td><td>[title~=flower]</td><td>选择 title 属性包含单词 “flower” 的所有元素。</td><td>2</td></tr><tr><td>[attribute|=value]</td><td>[lang|=en]</td><td>选择 lang 属性值以 “en” 开头的所有元素。</td><td>2</td></tr><tr><td>:link</td><td>a:link</td><td>选择所有未被访问的链接。</td><td>1</td></tr><tr><td>:visited</td><td>a:visited</td><td>选择所有已被访问的链接。</td><td>1</td></tr><tr><td>:active</td><td>a:active</td><td>选择活动链接。</td><td>1</td></tr><tr><td>:hover</td><td>a:hover</td><td>选择鼠标指针位于其上的链接。</td><td>1</td></tr><tr><td>:focus</td><td>input:focus</td><td>选择获得焦点的 input 元素。</td><td>2</td></tr><tr><td>:first-letter</td><td>p:first-letter</td><td>选择每个<p>元素的首字母。</p></td><td>1</td></tr><tr><td>:first-line</td><td>p:first-line</td><td>选择每个<p>元素的首行。</p></td><td>1</td></tr><tr><td>:first-child</td><td>p:first-child</td><td>选择属于父元素的第一个子元素的每个<p>元素。</p></td><td>2</td></tr><tr><td>:before</td><td>p:before</td><td>在每个<p>元素的内容之前插入内容。</p></td><td>2</td></tr><tr><td>:after</td><td>p:after</td><td>在每个<p>元素的内容之后插入内容。</p></td><td>2</td></tr><tr><td>:lang(language)</td><td>p:lang(it)</td><td>选择带有以 “it” 开头的 lang 属性值的每个<p>元素。</p></td><td>2</td></tr><tr><td>element1~element2</td><td>p~ul</td><td>选择前面有<p>元素的每个</p><ul><li>元素。</li></ul></td><td>3</td></tr><tr><td>[attribute^=value]</td><td>a[src^=“https”]</td><td>选择其 src 属性值以 “https” 开头的每个 元素。</td><td>3</td></tr><tr><td>[attribute$=value]</td><td>a[src$=“.pdf”]</td><td>选择其 src 属性以 “.pdf” 结尾的所有 元素。</td><td>3</td></tr><tr><td>[attribute*=value]</td><td>a[src*=“abc”]</td><td>选择其 src 属性中包含 “abc” 子串的每个 元素。</td><td>3</td></tr><tr><td>:first-of-type</td><td>p:first-of-type</td><td>选择属于其父元素的首个<p>元素的每个</p><p>元素。</p></td><td>3</td></tr><tr><td>:last-of-type</td><td>p:last-of-type</td><td>选择属于其父元素的最后<p>元素的每个</p><p>元素。</p></td><td>3</td></tr><tr><td>:only-of-type</td><td>p:only-of-type</td><td>选择属于其父元素唯一的<p>元素的每个</p><p>元素。</p></td><td>3</td></tr><tr><td>:only-child</td><td>p:only-child</td><td>选择属于其父元素的唯一子元素的每个<p>元素。</p></td><td>3</td></tr><tr><td>:nth-child(n)</td><td>p:nth-child(2)</td><td>选择属于其父元素的第二个子元素的每个<p>元素。</p></td><td>3</td></tr><tr><td>:nth-last-child(n)</td><td>p:nth-last-child(2)</td><td>同上，从最后一个子元素开始计数。</td><td>3</td></tr><tr><td>:nth-of-type(n)</td><td>p:nth-of-type(2)</td><td>选择属于其父元素第二个<p>元素的每个</p><p>元素。</p></td><td>3</td></tr><tr><td>:nth-last-of-type(n)</td><td>p:nth-last-of-type(2)</td><td>同上，但是从最后一个子元素开始计数。</td><td>3</td></tr><tr><td>:last-child</td><td>p:last-child</td><td>选择属于其父元素最后一个子元素每个<p>元素。</p></td><td>3</td></tr><tr><td>:root</td><td>:root</td><td>选择文档的根元素。</td><td>3</td></tr><tr><td>:empty</td><td>p:empty</td><td>选择没有子元素的每个<p>元素（包括文本节点）。</p></td><td>3</td></tr><tr><td>:target</td><td>#news:target</td><td>选择当前活动的 #news 元素。</td><td>3</td></tr><tr><td>:enabled</td><td>input:enabled</td><td>选择每个启用的 元素。</td><td>3</td></tr><tr><td>:disabled</td><td>input:disabled</td><td>选择每个禁用的 元素</td><td>3</td></tr><tr><td>:checked</td><td>input:checked</td><td>选择每个被选中的 元素。</td><td>3</td></tr><tr><td>:not(selector)</td><td>:not§</td><td>选择非<p>元素的每个元素。</p></td><td>3</td></tr><tr><td>::selection</td><td>::selection</td><td>选择被用户选取的元素部分。</td><td>3</td></tr></tbody></table>

CSS 选择器有很多，像标签选择器、类选择器、ID 选择器、关系选择器、伪类选择器、分组选择器等等，但是只需要掌握常用的几种就可以满足定位元素的需求。

以下述 HTML 为例，总结下 CSS 选择器的用法：

```
<div id="menu" class="menu" title="menu">
	<ul>
		<li id="first" class="catagory book">
			<a id="book">
			</a>
		</li>
		<li id="second" class="catagory food">
			<a id="food">
			</a>
		</li>
		<li>
			<a id="clothes">
			</a>
		</li>
		<li title="submenu">
			<a id="furniture">
			</a>
		</li>
	</ul>
	<a href="....">
		Welcome to Our Store
	</a>
</div>
```

1.  标签选择器  
    使用 HTML 标签来选择元素，例如：
    
    ```
    driver.findElement(By.cssSelector("li"));   //将选择所有li元素
    driver.findElement(By.cssSelector("*a*")); //将选择所有a元素
    ```
    
2.  类选择器  
    使用类名来选择元素，使用方法：.class， 例如：
    
    ```
    driver.findElement(By.cssSelector("div.menu")); //将选择class为menu的div元素
    driver.findElement(By.cssSelector(".catagory")); //将选择id为first的元素和id为second的元素，因为这两个元素的class里都含有catagory
    ```
    
3.  ID 选择器  
    使用 ID 来选择元素，使用方法：#id，例如：
    
    ```
    driver.findElement(By.cssSelector("a#clothes")); //将选择id为clothes的a元素
    ```
    
    也可以写成：
    
    ```
    driver.findElement(By.cssSelector("#clothes")); //因为id是唯一的所以还是会选择id为clothes的a元素
    ```
    
4.  关系选择器  
    **div,p** 作用：选择所有 div 元素和 p 元素  
    **div>p** 作用：选择 div 的直接子元素中的所有 p 元素  
    **div p** 作用：选择 div 的后代元素中的所有 p 元素
    
5.  属性选择器  
    **[title]** 作用：选择所有具有 title 属性的元素  
    **[title=‘menu’]** 作用：选择所有 title 属性值等于’menu’的元素  
    **[title~=‘menu’]** 作用：选择所有 title 属性值包含 menu 的元素，注意：menu 必须是一个 word，且有空格与其他单词分开  
    __[title_=‘menu’]_* 作用：选择所有 title 属性值包含 menu 的元素，注意：此时 menu 为 substring，而不是 word  
    **[title|=‘menu’] ** 作用：选择所有 title 属性值以 menu 开头或者等于 menu 的元素  
    **[title^=‘menu’]** 作用：选择所有 title 属性值以 menu 开头的元素  
    **[title$=‘menu’]** 作用：选择所有 title 属性值以 menu 结尾的元素  
    **div[title=‘menu’]** 作用： 选择所有 title 属性值等于 menu 的 div 元素
    
6.  通用选择器  
    方法：*
    
    ```
    div ul *; //选择div ul 下的所有子元素，包括li和a元素
    ```
    
7.  伪类选择器  
    伪类选择器很多，只总结下用过的: nth-child(n)
    
    ```
    p:nth-child(2) 作用：选择作为第二孩子的p元素
    ```
    

### 2.Xpath 定位元素

XPath 是一门在 XML 文档中查找信息的语言。XPath 可用来在 XML 文档中对元素和属性进行遍历。XPath 使用路径表达式来选取 XML 文档中的节点或者节点集。这些路径表达式和我们在常规的电脑文件系统中看到的表达式非常相似。XPath 含有超过 100 个内建的函数。这些函数用于字符串值、数值、日期和时间比较、节点和 QName 处理、序列处理、逻辑值等等。. 在 XPath 中，有七种类型的节点：元素、属性、文本、命名空间、处理指令、注释以及文档节点（或称为根节点）。[XML](https://so.csdn.net/so/search?q=XML&spm=1001.2101.3001.7020) 文档是被作为节点树来对待的。树的根被称为文档节点或者根节点。详情请参考 [XPath 教程 (w3school.com.cn)](https://www.w3school.com.cn/xpath/index.asp)

### 3. 定位元素总结

在浏览器中按 F12 打开开发者工具，然后选择你要的元素，**右键**选择 **Inspect**。可以看到 审查元素信息已经出来了。**右键**选择之后然后复制。我们既可以复制成 Xpath 的也可以复制成 Css 选择器的路径。

七. Huginn 总结
============

Huginn 可以订阅任意你想要订阅的网站与平台，例如微信公众号、简书、知乎、博客、图虫、等等，只要有网页同时生成了 CSS，你就可以派出你的 “Agent” 去把他们抓回来，然后将他们“分门别类”，任意处置了。Huginn 的门槛就在于环境的部署以及 Website Agent 规则的制定。虽然说 Huginn 有 scenarios 可供导入导出，但是目前为止还没有一个大规模的 scenarios 库，所以 Huginn 普及是非常困难的。目前，大家可以在这里找到几个可供使用的脚本库：http://huginnio.herokuapp.com/scenarios。

参考资料:

[huginn/huginn: Create agents that monitor and act on your behalf. Your agents are standing by! (github.com)](https://github.com/huginn/huginn)

[上手 huginn 的第一篇教程：一个定时监控黄金价格的 rss - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/75730603)

[简单上手的 huginn 教程（2）——将抓取的内容推送至微信 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/80725216)

[简单上手的 huginn 教程（3）——对监控的时间进行更精确的控制 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/83507407)

[huginn | 全网数据监控与通知工具—安装教程、全方位介绍 | VPS 精选网 (vpsjxw.com)](https://www.vpsjxw.com/vps_use/huginn_intro/)

[利用 Huginn 抓取任意网站 RSS 和微信公众号更新 - 打造一站式信息阅读平台 | 麦田一棵葱 (52maicong.com)](https://www.52maicong.com/shiyong/8314.html)

[超详细! 如何利用 Huginn 制作专属 RSS - 谁是小菜鸡 - 博客园 (cnblogs.com)](https://www.cnblogs.com/liujiangblog/p/12115804.html)

[Huginn 中文指南：搭建自己的 iFTTT](https://www.jianshu.com/p/d3407cc3df5c)