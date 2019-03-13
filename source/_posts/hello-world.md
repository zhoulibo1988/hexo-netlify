---
title: Hexo 创建文章、标签、分类
categories: Hexo
tags: [Hexo]
---
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页

## 1:创建文章

### 在hexo下创建一个新的文章
``` bash
hexo new "文章名称"
```

生产后会提示你文件路径，一般在hexo/source/_posts下

### 文章基本设置
``` bash
title: CentOS7下Tomcat启动慢的原因及解决方案
date: 2017-12-02 21:01:24
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "云服务器" #分类
tags:   #标签
	- centOS
	- tomcat
```
## 2:创建标签
### 创建标签页面
``` bash
hexo new page tags
```
### 基本设置
```
title: tags
date: 2017-12-02 21:01:24
type: "tags"
``` bash
## 创建分类
### 创建分类页面
```
hexo new page categories
```
### 基本设置
``` bash
title: categories
date: 2017-12-02 21:01:24
type: "categories"
```

### END