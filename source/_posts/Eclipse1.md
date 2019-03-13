---
title: Eclipse快捷键 包括查找类、方法、变量
categories: Eclipse
tags: [Eclipse]
---
Eclipse 是一个开放源代码的、基于Java的可扩展开发平台。就其本身而言，它只是一个框架和一组服务，用于通过插件组件构建开发环境。幸运的是，Eclipse 附带了一个标准的插件集，包括Java开发工具（Java Development Kit，JDK）

### 搜索当前接口的实现类
``` bash
1. 【ALT +/】 
   此快捷键为用户编辑的好帮手，能为用户提供内容的辅助，不要为记不全方法和属性名称犯愁，当记不全类、方法和属性的名字时，多体验一下【ALT +/】快捷键带来的好处吧。
   ![avatar](https://github.com/zhoulibo1988/img/blob/master/ALT+.jpg?raw=true)
2. 【Ctrl+O】 
   显示类中方法和属性的大纲，能快速定位类的方法和属性，在查找Bug时非常有用。
3. 【Ctrl+/】 
   快速添加注释，能为光标所在行或所选定行快速添加注释或取消注释，在调试的时候可能总会需要注释一些东西或取消注释，现在好了，不需要每行进行重复的注释。
4. 【Ct rl+D】 
   删除当前行，这也是笔者的最爱之一，不用为删除一行而按那么多次的删除键。
5. 【Ct rl+M】 

   窗口最大化和还原，用户在窗口中进行操作时，总会觉得当前窗口小（尤其在编写代码时），现在好了，试试【Ct rl+M】快捷键。

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