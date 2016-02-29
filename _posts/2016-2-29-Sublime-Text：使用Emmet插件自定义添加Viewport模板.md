---
layout: post
date:   2016-02-29 19:40:00 +0800
category: school
tagline: "Supporting tagline"
tags : [Sublime Packages,emmet]
author : 問津書院 长春
---





**前言：**

`Emmet`，一个很成熟的并且非常适用于编写 HTML/XML 和 CSS 代码的前端开发人员大幅度提高开发效率的一个工具。

关于`Emmet`的使用语法网上已经有非常详细的教程，在此不做多阐述，有兴趣的同学可通过以下链接研究下。

今天来主要来说说如何给**Emmet**快捷自定义内容，比如我想要快捷键输入`html:web` 后按 **Tab**键出来的是自定义一套**Viewport** 模板。

> [Emmet 使用手册](http://www.w3cplus.com/tools/emmet-cheat-sheet.html)  
> [Emmet 插件使用教程（转载）](http://www.yunxiu.org/blog/article/5490.htm)




## 问题产生

**使用过`Emmet`插件的同学都知道在`Emmet`中快捷键输入 `html:5` 后按`Tab`的粗来h5的文档是长这样的：**

	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Document</title>
	</head>
	<body>

	</body>
	</html>

**但是在移动Web项目中的Viewport模板通常是长这样的：**

	<!DOCTYPE html>
	<html>
	<head>
	<meta charset="utf-8">
	<meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport">
	<meta content="yes" name="apple-mobile-web-app-capable">
	<meta content="black" name="apple-mobile-web-app-status-bar-style">
	<meta content="telephone=no" name="format-detection">
	<meta content="email=no" name="format-detection">
	<title>标题</title>
	<link rel="stylesheet" href="index.css">
	</head>

	<body>
	这里开始内容
	</body>

	</html>


**那么问题来了——**

> “我想要快捷键输入`html:5` 后按 **Tab**键出来的是移动Web项目的`Viewport`模板，该如何做呢？  
> 有的同学可能会说可以对着`<head>`中的`<meta>`标签部分进行一句一句的复制粘贴修改。  
> 但作为一个懒癌晚期患者来说，这样做太麻烦了，有没有更简单的方法? 答案是当然有。

<br />
<br />

---

<br />
<br />

好了废话不多说，下面进入正文部分。

## 首先安装 [*Emmet*](http://docs.emmet.io/)


**第1步：安装Package Control**

- 安装`Emmet`插件之前需给Sublime Text 安装包管理插件：[*Package Control*](https://sublime.wbond.net/Package%20Control.sublime-package)
- *(关于安装`Package Control`的方法网上有很多在此不做多介绍)*

**第2步：安装Emmet**

- 安装`Package Control`后快捷键入**Ctrl+Shift+P**  打开命令面板输入**PCIP** 进行模糊匹配`Package Control:Install Package`选中第一个进入（如下图所示）

![UserEmmet]({{ site.baseurl }}/assets/images/160229/01.png)

- 进入安装插件面板后输入插件名称**Emmet**(如下图所示)，选中第一个`Emmet`等待安装。

![UserEmmet]({{ site.baseurl }}/assets/images/160229/02.png)


**第2步：重启Sublime**

- 选中会看到编辑器的底部左下角`loading`进度条，安装完后，重启Sublime Text 编辑器即可。
- 重启Sublime后在`Perferences`-> `package settings`中看到有`Emmet`这一项，则表明安装成功。


## 进行配置`Emmet`文件

**好了，前戏都做完了，下面开始进入正戏部分：**

1、查找`Emmet` 默认配置文件`snippets.json`。

- 点击`package Settings` --> `Browse Packages...`进入插件包文件目录。
- 找到`Emmet\emmet` 文件下的 `snippets.json` 文件，把这个文件拖入Sublime中。


![UserEmmet]({{ site.baseurl }}/assets/images/160229/03.png)


**2、在这个文件中我们找到下面这句代码**(**我们要修改的就是这部分**)：

	"doc": "html>(head>meta[charset=UTF-8]+title{${1:Document}})+body)"


**3、添加自定义配置**

> 点击`package Settings` -> `Emmet` -> `Settings - User` 输入以下代码段(如下图所示)

![UserEmmet]({{ site.baseurl }}/assets/images/160229/04.png)

{
	"snippets": {
		"html": {
			"abbreviations": {
				"docweb":"html>(head>meta[charset=${charset}]+meta[content=\"width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no\" name=\"viewport\"]+meta[content=\"yes\" name=\"apple-mobile-web-app-capable\"]+meta[content=\"black\" name=\"apple-mobile-web-app-status-bar-style\"]+meta[content=\"telephone=no\" name=\"format-detection\"]+meta[content=\"email=no\" name=\"format-detection\"]+title{${1:Document}})+body",
				"html:web":"!!!+docweb"
			}
		}
	}
}


**4、最后验证结果**

- 首先启动Sublime Text 新建一个`HTML`文件。
- 通过上一步的配置，输入`html:web`（快捷键可根据个人喜好自行设定）后按`Tab` 键（如无意外的情况下会出现以下代码）。

	<!DOCTYPE html>
	<html>
	<head>
	    <meta charset="UTF-8">
	    <meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport">
	    <meta content="yes" name="apple-mobile-web-app-capable">
	    <meta content="black" name="apple-mobile-web-app-status-bar-style">
	    <meta content="telephone=no" name="format-detection">
	    <meta content="email=no" name="format-detection">
	    <title>Document</title>
	</head>
	<body>

	</body>
	</html>




## 总结

- 主要实现原理就是：`Emmet`提供了自定义的文件： `snippets.json` 我们通过自定义修改`Emmet` 配置文件的默认设置来达到我们想要目的，有兴趣的同学快去试试吧。
- 最后，感谢各位看官大人阅读，希望通过这篇博文能对您有所帮助，如需转载请著名原创作者及附上原文链接，谢谢。


## 关于本文

> 作者：@Br3ad

