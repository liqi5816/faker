

\[TOC\]



\# 互联网数据中心（IDC）部署说明



\#\# 一、环境要求



+ jdk



  工程编译及运行需要jdk\*\*1.8\*\*或以上，编译级别为\*\*8\*\*；



\* tomcat



  tomcat版本请使用\*\*8.5\*\*或以上



\* elasticsearch



  可使用工具包\*tools\*中\*elasticsearch-5.2.2.zip\*，绿色版解压开即可使用



\* cfile



  文件存储依赖于\*gcloud\_cfileServer\*应用，IDC已经集成了\*gcloud\_cfileServer\*客户端



\* srr



  IDC通过srr调用\*gcloud\_cfileServer\*的文件存储服务，因此也依赖于\*gcloud\_srr\*应用



\* 静态资源



  IDC的UI依赖于\*GCloud-StaticRes\*，请引入该静态资源



\* nginx



  IDC无需登录即可使用，可在nginx中配置代理



\* chrome



  请使用工具包\*tools\*中提供的chrome\*\*53\*\*版本，安装时请保持默认安装 



\* chromedriver



  搭配使用特定版本chrome使用，满足selenium自动化抓取需求，在安装了chrome53版本之后，将chromedriver拷贝到chrome的默认安装路径，例如：



  &gt; \`\`\`properties

  &gt; C:/Users/xushengfeng/AppData/Local/Google/Chrome/Application

  &gt; \`\`\`



  同时请配置应用的配置文件\*configs.properties\*中的\*webDriverPath\*字段为你的chromedriver实际路径，例如：



  &gt; \`\`\`properties

  &gt; \#webDriver位置

  &gt; webDriverPath = C:/Users/xushengfeng/AppData/Local/Google/Chrome/Application/chromedriver.exe

  &gt; \`\`\`



\#\#二、部署步骤



1. 安装chrome



   请使用工具包\*tools\*中提供的chrome\*\*53\*\*版本，安装时请保持默认安装 



2. 拷贝chromedriver



   拷贝工具包\*tools\*中提供的\*chromedriver.exe\*到chrome的安装路径，例如：



   &gt; \`\`\`properties

   &gt; C:/Users/xushengfeng/AppData/Local/Google/Chrome/Application

   &gt; \`\`\`



   然后配置IDC的配置文件\*configs.properties\*中的\*webDriverPath\*字段为你的chromedriver实际路径，例如：



   &gt; \`\`\`properties

   &gt; \#配置文件configs.properties路径

   &gt; resources/configs.properties

   &gt; \`\`\`



   &gt; \`\`\`properties

   &gt; \#webDriver位置

   &gt; webDriverPath = C:/Users/xushengfeng/AppData/Local/Google/Chrome/Application/chromedriver.exe

   &gt; \`\`\`



3. 启动srr、cfile和nginx



   启动srr、cfile和nginx，然后配置IDC应用的配置文件\*service.properties\*中的字段\*registry.host\*



   和\*registry.port\*为srr的地址和端口，例如：



   &gt; \`\`\`properties

   &gt; \#配置文件service.properties路径

   &gt; resources/service.properties

   &gt; \`\`\`



   &gt; \`\`\`properties

   &gt; \#srr地址

   &gt; registry.host = 10.12.1.80

   &gt;

   &gt; \#srr端口

   &gt; registry.port = 9999

   &gt; \`\`\`



4. 启动ES



   请在启动IDC之前先启动elasticsearch，路径：



   &gt; elasticsearch-5.2.2/bin/elasticsearch.bat



   ES的默认服务发布端口是9300，可以在ES的控制台窗口中看到\*publish\_address\*，请配置IDC应用的配置文件\*configs.properties\*中的字段\*esHost\*和\*esPort\*，例如：



   &gt; \`\`\`properties

   &gt; \#配置文件configs.properties路径

   &gt; resources/configs.properties

   &gt; \`\`\`



   &gt; \`\`\`properties

   &gt; \#是否启动es

   &gt; needEs = true

   &gt;

   &gt; \#es地址

   &gt; esHost = localhost

   &gt;

   &gt; \#es端口

   &gt; esPort = 9300

   &gt; \`\`\`



5. 启动IDC



   请在ES启动完毕之后再启动IDC



\#\# 三、使用说明



1. 请在IDC启动完毕之后访问该应用首页，或者公司内网访问80测试环境上的帮助文档：



   &gt; \`\`\`properties

   &gt; \#本地应用

   &gt; http://127.0.0.1/idc/jsp/panel/welcome/welcome.jsp

   &gt;

   &gt; \#80应用

   &gt; http://10.12.1.80/idc/jsp/panel/welcome/welcome.jsp

   &gt; \`\`\`





2. 然后可在\*“帮助”\*功能中查看使用手册，随着版本迭代部分功能和页面可能出现调整，但整体使用保持一致

