> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/60964590)

总体步骤分三步，Agent Event Flow 如下：

![](https://pic3.zhimg.com/v2-e158c5fcf7bf3367fcda041bd6c5e3e6_b.jpg)

获取热门书评页面（[https://book.douban.com/review/best/](https://book.douban.com/review/best/)）的各个书评链接
---------------------------------------------------------------------------------------------

1）创建 website agent，基本配置如下：

![](https://pic4.zhimg.com/v2-1b6c33368a1ea31c5100ae4427b157f7_r.jpg)

2） option 配置

只用获取各个书评的 URL 即可，xpath 获取的方式【[利用 Huginn 打造一站式信息阅读平台](https://huginn.cn/blog/huginn/%E5%88%A9%E7%94%A8-huginn-%E6%89%93%E9%80%A0%E4%B8%80%E7%AB%99%E5%BC%8F%E4%BF%A1%E6%81%AF%E9%98%85%E8%AF%BB%E5%B9%B3%E5%8F%B0)】中说的比较清楚，借助 [XPath Helper](https://chrome.google.com/webstore/detail/xpath-helper/hgimnogjllphhhkhlmebbmlgjoejdpjl?hl=zh-CN) 确认。

```
{
  "expected_update_period_in_days": "2",
  "url": "https://book.douban.com/review/best/",
  "type": "html",
  "mode": "on_change",
  "extract": {
    "url": {
      "xpath": "//*[@id]/div/h2/a",
      "value": "@href"
    }
  }
}
```

创建获取全文的 website agents
----------------------

1）基本配置，主要是在 Source 中要添加上一步创建的 website agent

![](https://pic4.zhimg.com/v2-202d99bb5551726f8df143194c7ee35f_r.jpg)

2）. option 配置

```
{
  "expected_update_period_in_days": "2",
  "url_from_event": "{{url}}",
  "type": "html",
  "mode": "merge",
  "extract": {
    "fulltext": {
      "xpath": "//*[@id=\"link-report\"]",
      "value": "."
    },
    "sdtitle": {
      "xpath": "//*[@id=\"content\"]/div/div[1]/h1/span",
      "value": "string(.)"
    }
  }
}
```

3. 创建 RSS 输出的 agent
-------------------

1）agent type 选择 Data Output Agent

2）基本配置，与前面类似，主要是 Sources 中要添加上一个 website agent

![](https://pic3.zhimg.com/v2-5e67cb59125e4dd06b3055c60f575536_r.jpg)

3） option 配置

主要是配置 RSS 条目（item）的三个字段（link、title、description）的内容，具体如下

```
{
  "secrets": [
    "a-secret-key"
  ],
  "expected_receive_period_in_days": 2,
  "template": {
    "title": "豆瓣最佳点评全文",
    "description": "豆瓣最佳点评全文",
    "item": {
      "link": "{{url}}",
      "title": "{{sdtitle}}",
      "description": "{{fulltext}}"
    },
    "link": "https://book.douban.com/review/best/"
  },
  "ns_media": "true"
}
```

成果 --TinyTinyRSS 的显示情况
----------------------

![](https://pic1.zhimg.com/v2-7b824902952712e8ee88471f314be380_r.jpg)

参考文章 1：

[利用 Huginn 打造一站式信息阅读平台](https://huginn.cn/blog/huginn/%E5%88%A9%E7%94%A8-huginn-%E6%89%93%E9%80%A0%E4%B8%80%E7%AB%99%E5%BC%8F%E4%BF%A1%E6%81%AF%E9%98%85%E8%AF%BB%E5%B9%B3%E5%8F%B0)