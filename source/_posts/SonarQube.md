---
title: SonarQube 的安装、配置及 Maven 项目的使用
date: 2019-03-15 16:20:00
categories: SonarQube
tags: [SonarQube]
---
### SonarQube 的安装、配置及 Maven 项目的使用

- SonarQube 是一个用于管理源代码质量开放平台，它可以从多个维度检测代码质量，可以快速的定位代码中潜在的或者明显的 Bug、错误。它支持包括 Java、Python、Php、C/C++、C#、HTML、JavaScript、PL/SQL、Objective C 等二十多种编程语言的代码质量管理与检测。可作为我们日常开发中检测代码质量的重要工具。

#### 1.环境、软件准备
- 本次演示环境，我是在本地机器 Windows 上操作，以下是安装的软件及版本：
``` 
	SonarQube：version 6.5
	 Jdk：version 1.8.0_91
	 Maven：version 3.3.9
	 Mysql： version 5.7.15
```
- 注意：下边我们要演示 Maven 项目如何使用 SonarQube 分析，所以需要先安装 Maven、Jdk，SonarQube 安装我们使用 Mysql 作为数据存储，所以需要先安装 Mysql，这里 Maven、Jdk、Mysql 的安装忽略

#### 2.SonarQube 安装
- 命令：
```
	set global event_scheduler = 'on';
	#可以物理修改数据库配置
	#skip-grant-tables
	 加上:
	event_scheduler=ON
```
#### 3.SonarQube 安装
- SonarQube 安装很简单，只需去官网下载最新版 zip 安装包到本地，解压执行即可。我解压到本地后的目录 windows系统，解压目录结构如下
[![目录](https://github.com/zhoulibo1988/img/blob/master/s1.jpg?raw=true "目录")](https://github.com/zhoulibo1988/img/blob/master/s1.jpg?raw=true "目录")
- 这里简单说下每个目录作用：
- bin 
	用来启动 SonarQube 服务，这里已经提供好了不同系统启动 | 停止脚本了，目前提供了 - linux-x86-32、linux-x86-64、macosx-universal-64、windows-x86-32、windows-x86-64
- conf 
	用来存放配置文件，若需要修改配置，修改 sonar.properties 文件即可。
- data 
	用来存放数据，SonarQube默认使用 h2 数据库存储，同时支持其他如Mysql、Orace、Mssql、Postgresql数据库存储。
- extensions 
	用来存放插件 jar 包，以后我们需要安装插件就放在这里。
- lib 
	用来存放各种所依赖的 jar 包，包括上边各数据库驱动包 (默认已提供一个版本，如果版本不匹配，则在这里手动更新下)。
- logs
	用来存放各日志信息
- web 
	用来提供 SonarQube web 网页服务。

#### 4.启动服务
- 启动双击： StartSonar.bat
- 关闭：直接找到java进程关闭
- 访问地址：http://localhost:9000
- 登录账号：admin  密码：admin
#### 5.修改数据库
- SonarQube 默认服务端口为 9000，默认数据库为 h2，这些都是可以修改配置的，我们只需要修改/conf/sonar.properties文件即可。以修改配置 Mysql 数据库为例：
```
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar
sonar.jdbc.url=jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true&useConfigs=maxPerformance&useSSL=false
2、本地 Mysql 创建数据库 这里就不需要说怎么做了，我想大家都明白
```
- 修改完成后，重启服务即可，我们会发现SonarQube已经帮我们在本地 Mysql 数据库 sonar 中创建好了所需各表
#### 6.插件安装
- 安装两个很实用的插件，一个是 Chinese Pack（SonarQube的汉化包），一个是 Checkstyle（检测代码风格
- Chinese Pack 插件安装：
- SonarQube 网页的汉化包，安装完该插件后，Web 页面大部分都翻译成中文了，是不是一下子就简介明了啦！首先下载插件 sonar-l10n-zh，源码托管在 github 上，下载对应兼容版本的jar (注意：README上的兼容列表，我本地 SonarQube 版本6.5，所以下载插件对应版本是1.17。)
- 如图
[![s2](https://github.com/zhoulibo1988/img/blob/master/s2.jpg?raw=true "s2")](https://github.com/zhoulibo1988/img/blob/master/s2.jpg?raw=true "s2")
[![s3](https://github.com/zhoulibo1988/img/blob/master/s3.jpg?raw=true "s3")](https://github.com/zhoulibo1988/img/blob/master/s3.jpg?raw=true "s3")
- 汉化成功后如图
[![s4](https://github.com/zhoulibo1988/img/blob/master/s4.jpg?raw=true "s4")](https://github.com/zhoulibo1988/img/blob/master/s4.jpg?raw=true "s4")
- Checkstyle 插件安装:
```  上边 Chinese Pack 插件安装时通过直接将 jar 包放到插件目录完成安装，我们也可以在 SonarQube 网页上直接点击安装。admin 登录，点击 配置 -> 系统 -> 更新中心 -> Available -> Search，输入 CheckStyle，在搜素结果中找到 CheckStyle 插件点击 Install，等待下载完成后，按照页面提示点击 Restart 自动重启服务即可完成安装
```
[![s5](https://github.com/zhoulibo1988/img/blob/master/s5.jpg?raw=true "s5")](https://github.com/zhoulibo1988/img/blob/master/s5.jpg?raw=true "s5")

- 也可以去github上面去下载相对应的版本，我这里选择为 3.7
- 下载地址：https://github.com/checkstyle/sonar-checkstyle/releases/tag/3.7
- 如图：
[![s6](https://github.com/zhoulibo1988/img/blob/master/s6.jpg?raw=true "s6")](https://github.com/zhoulibo1988/img/blob/master/s6.jpg?raw=true "s6")

- SonarQube 支持分析的语言有很多，像Java、Python、Php、C/C++、C#、HTML、JavaScript、PL/SQL、Objective C等20+语言，当我们需要支持分析什么语言时，只需要去插件中心安装对应语言的插件即可，非常方便，可扩展性强。

#### 7.使用 SonarQube 分析 Maven 项目
- 下面我们以一个 Java Maven 项目 mavenDemo 为例，看下如何配置，以及 SonarQube 分析结果查看。注意：这里有个兼容性选择问题，如果 SonarQube >= 4.5，那么 maven-sonar-plugin >= 2.7，如果 SonarQube < 4.5，那么 maven-sonar-plugin = 2.6；如果 Maven >= 3.0，那么maven-sonar-plugin >= 3.1，如果 Maven < 3.0，那么 maven-sonar-plugin = 3.0.2。

- 我的maven版本是3.3.9 对应的文件是settings.xml 版本低一点的对应的文件可能是setting.xml
```
<profile>
		<id>sonar</id>
		<activation>
			<activeByDefault>true</activeByDefault>
		</activation>
		<properties>
		<!-- Example for MySQL-->
			<sonar.jdbc.url>
				jdbc:mysql://localhost:3306/sonar
			</sonar.jdbc.url>
			<sonar.jdbc.username>root</sonar.jdbc.username>
			<sonar.jdbc.password>zhoulibo1234567890</sonar.jdbc.password>
			<sonar.host.url>http://localhost:9000</sonar.host.url>
		</properties>
	</profile>
```
- 其中sonar.host.url 值就是 上文启动的sonar 服务器地址。
#### 8.对maven项目进行分析
- 在你的maven项目下面进行命令操作
```
mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar
```
- 出现: BUILD SUCCESS 标识之后 刷新界面查看 :
- 最终效果
[![s7](https://github.com/zhoulibo1988/img/blob/master/s7.jpg?raw=true"s7")](https://github.com/zhoulibo1988/img/blob/master/s7.jpg?raw=true "s7")















