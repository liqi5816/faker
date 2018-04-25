# 模板样例

* [ ] ## 工商商标爬取样例

![](/assets/商标爬取1.png)

                                                                                                 图 1

商标爬取任务内容是对图1中的数据进行爬取。爬取的json模板如下所示：

```
{
    "siteName": "商标爬取1596期",
    "domain": "sbgg.saic.gov.cn",
    "startURL": [
        "http://sbgg.saic.gov.cn:9080/tmann/annInfoView/annSearchDG.html?annNum=1596&totalYOrN=true"
    ],
    "thread": "1",
    "maxPageGather": "10",
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

sitename:模板名称

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

* [ ] ## 搜狐新闻爬取样例
* [ ] ## 天涯论坛爬取样例

## 

* [ ] ## 微博爬取样例



