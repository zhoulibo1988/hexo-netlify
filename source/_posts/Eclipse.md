---
title: Eclipse Java注释模板设置详解
categories: Eclipse
tags: [Eclipse]
---
Eclipse 是一个开放源代码的、基于Java的可扩展开发平台。就其本身而言，它只是一个框架和一组服务，用于通过插件组件构建开发环境。幸运的是，Eclipse 附带了一个标准的插件集，包括Java开发工具（Java Development Kit，JDK）

### 设置注释模板的入口
``` bash
Window->Preference->Java->Code Style->Code Template 然后展开Comments节点就是所有需设置注释的元素啦。现就每一个元素逐一介绍
```

### 文件(Files)注释标签
``` bash
/**   
* @Title: ${file_name} 
* @Package ${package_name} 
* @Description: ${todo}(用一句话描述该文件做什么) 
* @author A18ccms A18ccms_gmail_com   
* @date ${date} ${time} 
* @version V1.0   
*/
```

### 类型(Types)注释标签（类的注释）
``` bash
/** 
* @ClassName: ${type_name} 
* @Description: ${todo}(这里用一句话描述这个类的作用) 
* @author A18ccms a18ccms_gmail_com 
* @date ${date} ${time} 
* 
* ${tags} 
*/
```
### 字段(Fields)注释标签
```
/** 
* @Fields ${field} : ${todo}(用一句话描述这个变量表示什么) 
*/ 
构造函数标签：
/** 
* <p>Title: </p> 
* <p>Description: </p> 
* ${tags} 
*/
```

### 方法(Constructor & Methods)标签
```
/** 
* @Title: ${enclosing_method} 
* @Description: ${todo}(这里用一句话描述这个方法的作用) 
* @param ${tags}    设定文件 
* @return ${return_type}    返回类型 
* @throws 
*/
```
### 覆盖方法(Overriding Methods)标签
```
/* (非 Javadoc) 
* <p>Title: ${enclosing_method}</p> 
* <p>Description: </p> 
* ${tags} 
* ${see_to_overridden} 
*/
```
### 代表方法(Delegate Methods)标签
```
/** 
* ${tags} 
* ${see_to_target} 
*/ 
```

### getter方法标签
```
/** 
* @return ${bare_field_name} 
*/ 
```

### setter方法标签
```
/** 
* @return ${bare_field_name} 
*/ 
```
### END