# IME For Minority Language
`小语种输入法`，支持梵文、巴利文、西夏文、藏文、婆罗米文等。
支持平台：windows7，8，10以及UWP。

本文仅仅是对项目的介绍，`小语种输入法`为私有项目，所有权归企业。

因此仓库没有代码，也没有任何项目文件。

`小语种输入法`由作者独立设计和完成
<br/>
<br/>



### 支持Windows多平台 - `Text Service Framework（TSF）` ###

Windows输入法开发由于文档很少，组织也比较混乱，因此存在一定的开发难度。
本项目使用了TSF实现，花了不短时间研究TSF内部的逻辑结构。
<br/>
<br/>

### 进程同步-`TCP SOCKET` ###

在项目中为了自定义GUI，将GUI从TSF框架中分离了。

GUI和TSF处于不同的进程，因此需要它们之间需要同步，项目使用了windows socket实现了进程同步。

数据同步涉及到了：`阻塞与非阻塞模式`、`字符的编码`、`多进程的管理`。
<br/>
<br/>


### 自然语言处理 ###

#### NLP-拼写错误纠正-`最小编辑距离` ####

拼写错误纠正基于`最小编辑距离`算法实现，算法定义如下图，使用该算法，可以得到和用户输入相关的候选项供用户选择。

<img width="400" src="https://github.com/nzaocan/IME-For-Minority-language-/blob/master/minDistance.png"/>
<br/>


#### NLP-候选列表生成-`LRU Cache` ####

LRU Cache 是操作系统中的一个算法，直译为最近最少使用算法，本文使用链表和哈希表（键值对）实现。

维护LRU Cache涉及大量的删除/查找操作，因此选用了删除/查找时间为o(1)的链表/哈希表。
<br/>
<br/>



视觉/交互设计
----------
使用XAML重写了窗体样式和诸多控件样式，以使APP在Windows7和windows10视觉体验一致。 

![hello](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/hello.png)

![mainpage](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/mainpage.png)

![](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/MouseCoverCandidatewindow.png)

![](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/login.png)

![](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/checkUpdate.png)

![](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/install.png)
