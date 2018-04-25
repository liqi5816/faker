# 模板样例

* [ ] ## 工商商标爬取样例

![](/assets/商标爬取1.png)

商标爬取任务内容是对上图中的数据进行爬取。爬取的json模板如下所示：

```
{
    "siteName": "商标爬取1596期",
    "domain": "sbgg.saic.gov.cn",
    "startURL": [
        "http://sbgg.saic.gov.cn:9080/tmann/annInfoView/annSearchDG.html?annNum=1596&totalYOrN=true"
    ],
    "thread": "1",
    "maxPageGather": "-1",
    "retry": "2",
    "sleep": "0",
    "timeout": "5000",
    "charset": "",
    "urlReg": "",
    "titleXPath": "",
    "titleReg": "",
    "contentXPath": "",
    "contentReg": "",
    "authorXPath": "",
    "authorReg": "",
    "categoryXPath": "",
    "categoryReg": "",
    "typeName": "trademark",
    "publishTimeXPath": "",
    "publishTimeReg": "",
    "publishTimeFormat": "",
    "lang": "",
    "country": "",
    "callbackURL": [],
    "userAgent": "Mozilla/5.0 (Windows NT 5.2) AppleWebKit/534.30 (KHTML, like Gecko) Chrome/12.0.742.122 Safari/534.30",
    "proxyHost": "",
    "proxyPort": "0",
    "proxyUsername": "",
    "proxyPassword": "",
    "doNLP": true,
    "saveCapture": true,
    "spiderType": "trademark",
    "ajaxSite": false,
    "needTitle": false,
    "needContent": false,
    "needPublishTime": false,
    "useSelenium": false,
    "gatherFirstPage": false,
    "autoDetectPublishDate": false,
    "trademark": true,
    "dynamicFields": [],
    "fileFields": [],
    "staticFields": [],
    "clickFields": []
}
```

sitename:模板名称一般格式   商标爬取模板+商标期数

domain:爬取的主页面

startURL:开始爬取的页面，如果不指定页面，程序会从domain页面下开始爬取，会爬取过多无效数据

thread:指启动线程数，如：线程数为10.同一个网页可分成10分进行爬取。spiderType为trademark不适应。

maxPageGather:最大爬取数量，不管页面有多少，这个属性的值后马上停止。如果改为-1为爬取全部数量。

sleep:为睡眠时间。

timeout：反应时间，如果在规定时间内没有反应，则跳过这条数据。

typemame:内容索引，存到es库中，关系到后面的查询和删除、新增逻辑。

callbackurl:默认为\[\]。

userAgent:用户代理。一般沒什麽特殊要求，保持默认。

proxyPort:端口号保持默认。

doNLP:自然处理语言true为选择。

saveCapture:保存网页快照，默认为选择true，好对应相应的数据。

trademark：是对此模板专门设置的模式。只有抓取商标时才会选上这个模式。（true为选择，false为取消）

设置好模板之后先点回填表格，这样json模板里的数据会回填到表格中，然后点击抓取样例数据，看抓取的数据是否满足条件，满足提交任务，不满足重洗修改模板后提交任务。

* [ ] ## 搜狐新闻爬取样例

![](/assets/sohu.png)

由上图可见得网页上的信息比较杂，广告较多，而我们需要的内容只是中间的几条。而选择其中一个点进去

![](/assets/sohu1.png)

会发现网站的连接都是从www.sohu.com/a/后面加一些数字跟下划线。所以，我们根据对所需要的页面然后进行数据爬取。利用正则表达式规定爬取的页面，从而可以过滤去一些不必要的数据。模板如下所示：

```
{
    "siteName": "sohu",
    "domain": "www.sohu.com",
    "startURL": [
        "http://www.sohu.com/tag/65239"
    ],
    "thread": "1",
    "maxPageGather": "-1",
    "retry": "2",
    "sleep": "0",
    "timeout": "5000",
    "charset": "",
    "urlReg": "http://www\\.sohu\\.com/a/.*",
    "titleXPath": "",
    "titleReg": "",
    "contentXPath": "",
    "contentReg": "",
    "authorXPath": "//*[@id='user-info']/h4/a",
    "authorReg": "",
    "categoryXPath": "//*[@id='article-container']/div[2]/div[1]/div[1]/div/span[3]",
    "categoryReg": "",
    "typeName": "webpage",
    "publishTimeXPath": "//*[@id='news-time']//text()",
    "publishTimeReg": "\\d{4}-\\d{2}-\\d{2} \\d{2}:\\d{2}",
    "publishTimeFormat": "yyyy-MM-dd hh:mm",
    "lang": "",
    "country": "",
    "callbackURL": [],
    "userAgent": "Mozilla/5.0 (Windows NT 5.2) AppleWebKit/534.30 (KHTML, like Gecko) Chrome/12.0.742.122 Safari/534.30",
    "proxyHost": "",
    "proxyPort": "0",
    "proxyUsername": "",
    "proxyPassword": "",
    "doNLP": true,
    "saveCapture": true,
    "spiderType": "commons",
    "id": "",
    "ajaxSite": false,
    "needTitle": false,
    "needContent": false,
    "needPublishTime": false,
    "useSelenium": false,
    "gatherFirstPage": false,
    "autoDetectPublishDate": false,
    "trademark": false,
    "dynamicFields": [],
    "fileFields": [],
    "staticFields": [],
    "clickFields": []
}
```

urlReg:就是我们上述所述的规定查询的页面，注意“.”一定要加转义。

authorXPath:作者位置的xpath，可以从网页上找到作者名字的位置。这个xpath一定要在我们规定的页面中，就是上面的urlReg中

publishTimeXPath:发布时间的xpath。

publishReg:我们获取的xpath上的数据会有各种各样，为了方便管理，我们这里会将网页上的数据取出后重新定义。

publishTimeFormat:我们获取的时间进行格式化，相当于simpleDataFormat中的模型。

* [ ] ## 天涯论坛爬取样例

![](/assets/论坛.png)

论坛页面和新闻页面一样，广告和其他垃圾信息很多，所以我们要对里面的信息进行筛选，同样是采取规范开始链接的方式，可以看到urlReg同样设置了数据。

```
{
    "siteName": "天涯社区-食在天涯",
    "domain": "bbs.tianya.cn",
    "startURL": [
        "http://bbs.tianya.cn/list-1138-1.shtml"
    ],
    "id": "",
    "thread": "1",
    "maxPageGather": "-1",
    "retry": "2",
    "sleep": "0",
    "timeout": "5000",
    "charset": "",
    "urlReg": "http://bbs\\.tianya\\.cn/post-1138-.*",
    "titleXPath": "//*[@id='post_head']/h1/span[1]/span/text()",
    "titleReg": "",
    "contentXPath": "//*[@class='bbs-content']/text()",
    "contentReg": "",
    "authorXPath": "//*[@id='post_head']/div[2]/div[2]/span[1]/a/text()",
    "authorReg": "",
    "categoryXPath": "//*[@id='bd']/div[2]/p/em/a[2]/text()",
    "categoryReg": "",
    "typeName": "webpage",
    "publishTimeXPath": "//*[@id='post_head']/div[2]/div[2]/span[2]/text()",
    "publishTimeReg": "\\d{4}-\\d{2}-\\d{2} \\d{2}:\\d{2}:\\d{2}",
    "publishTimeFormat": "yyyy-MM-dd hh:mm:ss",
    "lang": "",
    "country": "",
    "callbackURL": [],
    "jpgReg": "",
    "jpgXPath": "",
    "needjpg": "on",
    "jpegReg": "",
    "jpegXPath": "",
    "needjpeg": "on",
    "pngReg": "",
    "pngXPath": "",
    "needpng": "on",
    "gifReg": "",
    "gifXPath": "",
    "needgif": "on",
    "userAgent": "Mozilla/5.0 (Windows NT 5.2) AppleWebKit/534.30 (KHTML, like Gecko) Chrome/12.0.742.122 Safari/534.30",
    "proxyHost": "",
    "proxyPort": "0",
    "proxyUsername": "",
    "proxyPassword": "",
    "doNLP": true,
    "saveCapture": true,
    "spiderType": "commons",
    "ajaxSite": false,
    "needTitle": false,
    "needContent": false,
    "needPublishTime": false,
    "useSelenium": false,
    "gatherFirstPage": false,
    "autoDetectPublishDate": false,
    "trademark": false,
    "dynamicFields": [],
    "fileFields": [
        {
            "regex": "",
            "xpath": "",
            "name": "jpg",
            "need": true
        },
        {
            "regex": "",
            "xpath": "",
            "name": "jpeg",
            "need": true
        },
        {
            "regex": "",
            "xpath": "",
            "name": "png",
            "need": true
        },
        {
            "regex": "",
            "xpath": "",
            "name": "gif",
            "need": true
        }
    ],
    "staticFields": [],
    "clickFields": []
}
```

跟上面几个模板对比下，我们可以发现这个模板多了fileFields这个属性。

fileFields:这是抓取文件的属性，可以定义抓取文件的类型。如果不选则不抓取。

