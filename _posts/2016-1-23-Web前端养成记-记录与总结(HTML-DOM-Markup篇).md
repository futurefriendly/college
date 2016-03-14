---
layout: post
date:   2016-01-23 20:30:00 +0800
category: school
tagline: "Supporting tagline"
tags : [summary,knowledge point]
author : 問津書院-原创 长春
---


## Web前端养成记—记录与总结(HTML DOM Markup篇)






### HTML DOM Markup 是啥?

- HTML（HyperText Markup Language）：*超文本标记语言，也叫网页标记语言，就是指页面内可以包含**图片**、**链接**，甚至**音乐**、**程序**等非文字元素。*

- DOM（Document Object Model）：*既文档对象模型（Document Object Model，简称DOM）是[W3C（万维网联盟）](https://www.w3.org/)组织推荐的处理可扩展标志语言的标准编程接口。*

- HTML DOM：`HTML Document Object Model`**(HTML文档对象模型)**的缩写，`HTML DOM`则是专门适用于`HTML/XHTML`的**文档对象模型**。

- Markup：`标记`的意思

- 结合起来就是： **HTML文档的结构标记(标签)的语言**

### HTML DOM Markup 模块与层级结构划分

拿到设计师给的PSD设计稿后先别着急去实现页面，先理清页面的**层级结构**、**模块与布局**，切图前：划分**模块的层级**、**DOM的布局结构**后再通过代码还原设计稿

**DOM模块划分原则：**

**一级模块** > **二级模块** > **三级模块**...

一级一级往下类推的层级嵌套，合理的运用`HTML`标签。

![Web前端养成记]({{ site.baseurl }}/assets/images/160121/00.png)

![Web前端养成记]({{ site.baseurl }}/assets/images/160121/01.png)

这是一个顶部导航条，通过截图大致可理解为：一共有**三个子模块**包含在**一个大的容器**里，最后来进行模块的拆分。

**结构如下：**

- **外边主容器**：`div.head`

- **左侧logo区** ：`div.logo` + **中间导航部分**：`div.nav-wrap`  + **右侧登录口**：`div.head-login`

- 中间的导航部分又细分为：`div.nav`（**主导航部分**）+`div.nav-sns`（**社交导航部分**）*

**html结构如下：**

    <div class="head">
        <h1><a href="#x">logo text...</a></h1>
        <div class="nav-wrap">
            <ul class="nav">
            ...
            </ul>
            <ul class="nav-sns">
            ...
            </ul>
        </div>
        <ul class="head-login">
        ...
        </ul>
    </div>


---

### HTML Markup Semantic （HTML标签语义化）

#### 标签语义化是啥意思？

1. 用合理HTML标记以及其特有的属性去格式化文档内容，如段落使用`p`，标题使用`h1~h6`，无线列表使用`ol`，有序列表使用`ul`等等

2. HTML 标签除了div和span，标签都是有一定语义性

3. 对于读文档的人来说一眼可以看到重要与否

#### 为啥要进行语义化？

1. 一个结构良好，合理语义化的页面，更利于搜索引擎的抓取（SEO的优化）和开发人员的维护(可维护性更高，因为结构清晰，便于不同的[屏幕阅读器](http://baike.baidu.com/link?url=YzBTC0b4YiRqRqu2K75BdLKDLpPpk_o8x20D_sqWSqQQERpTd93WOx2noc69CuJetg0NTAfVLjmB6IdlE6_EP_)会根据标签的语义自动解析，呈现更容易阅读的内容形式（无障碍阅读）。

2. 搜索引擎会根据标签的语义确定上下文和权重问题

3. 便于后期的开发以及维护，团队合作效率提高

*注：关于HTML语义化可参考[W3C官网](http://www.w3.org/)标签的使用，用开发者工具禁掉它的CSS文件再看看效果。*


#### 合理的实现（Semantic Markup 语义化）

HTML语义：元素 + 属性 + 属性值 (+ 文档结构)

**使用合理的标签进行Semantic Markup（语义化标签）分类**

**文本级语义 (text-level semantics)**

- **标题**：`H1~H6`  
- **段落**：`p`  
- **强调**：`strong`、`em`  
- **联系信息**：`address`

**链接 (links)**

- **链接**：`a`

**图片(images)**

- **图片**：`img`

**顺序列表结构化**

- ol —> li

**非顺序列表结构化**

- ul —> li

**定义列表结构化**

- dl —> dt + dd

**tabular data表格**

- table > thead + tbody

- tr > th + td

**分组（Grouping）**

- div、span  
- div > **Block Elements（块级元素）**  
- span > **Inline Elements（行内元素）**

**导航结构化**

- div、span、ul、ol、dl、dt、dd、img、a

![Web前端养成记]({{ site.baseurl }}/assets/images/160121/00.png)

这是一个网站结构布局示意图：

![Web前端养成记]({{ site.baseurl }}/assets/images/160121/02.png)


**html 结构如下：**

     <div id="wrap">
         <h1>#wrap</h1>
         <div id="header">
             <h2>#header</h2>
         </div>
         <!-- // header -->
         <div id="container" class="clearfix">
             <h3>#container</h3>
             <div class="sub">
                 <h3>.sub</h3>
             </div>
             <!-- //sub -->
             <div id="content">
                 <h3>#content</h3>
             </div>
             <!-- //content -->
         </div>
         <!-- //container -->
         <div id="footer">
             <h3>#footer</h3>
         </div>
         <!-- //footer -->
     </div>
     <!-- //wrap -->

**标签语义化参考文档：**

1. *[Semantics in HTML 5](http://alistapart.com/article/semanticsinhtml5), A List Apart.*

2. *[Semantics - Dive Into HTML5](http://diveintohtml5.info/semantics.html), Dive Into HTML5.*


## 总结

**编写HTML 标记前先思考以下几个问题：**

- 标签嵌套是否合理：`block > inline-block > inline`

- 语法简单、是否强调语义

- 页面可访问性（如去掉样式，`结构是否完整`）

- 内容、结构、样式是否分离

- 页面的`SEO（搜索引擎优化）`

- 是否具有稳定性、可扩展灵活

- 进一步再通过*[W3C的验证](http://jigsaw.w3.org/css-validator/)*


---


### 关于我

一个前端爱好者，一个誓死不脱离低级趣味的人，一個庸俗的人，偶尔会装逼。

欢迎各路看官一起深（tan）入（xiao）交（feng）流（sheng）。

联系邮箱： *<moldy_bread@foxmail.com>*


### 特别鸣谢

在这里特别感谢下*[问津书院](http://futurefriendly.cn/college/)*的两位领导*[@校董大人](http://weibo.com/u/1277728572?topnav=1&wvr=6&topsug=1)* *[@院长大人](http://weibo.com/370557105?from=myfollow_all)*的极力帮助，对本人提出的问题进行耐心解答，并给出了不同的优秀解决方案，在两位大神的带领下涨了好多姿势。

本文PDF下载：[Web前端养成记—记录与总结(HTML DOM Markup篇)](http://pan.baidu.com/s/1pKe1gAR)