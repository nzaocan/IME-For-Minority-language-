# IME For Minority Language
`小语种输入法`，支持梵文、巴利文、西夏文、藏文、婆罗米文等。
支持平台：windows7，8，10以及UWP。

本文仅仅是对项目的介绍，`小语种输入法`为私有项目，所有权归企业。

因此仓库没有代码，也没有任何项目文件。

`小语种输入法`由作者独立设计和完成（包含视觉和交互设计）


进程同步-`TCP SOCKET`
----
在项目中由于GUI和TSF框架是分离的，因此需要它们之间需要同步，作者使用了windows socket实现了进程同步。

自然语言处理
-
NLP-拼写错误纠正-`最小编辑距离`
-
拼写错误纠正基于`最小编辑距离`算法实现，算法定义如下图，使用该算法，可以得到和用户输入相关的候选项供用户选择。

<img width="150" height="150" src="https://github.com/nzaocan/IME-For-Minority-language-/blob/master/minDistance.png"/>

NLP-候选列表生成-`LRU Cache`
-------
LRU Cache 是操作系统中的一个算法，直译为最近最少使用算法，本文使用链表和哈希表（键值对）实现。

维护LRU Cache涉及大量的删除/查找操作，因此选用了删除/查找时间为o(1)的链表/哈希表。

视觉/交互设计
----------
使用XAML重写了窗体样式和诸多控件样式，以使APP在Windows7和windows10视觉体验一致。 

![hello](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/hello.png)

![mainpage](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/mainpage.png)

![](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/MouseCoverCandidatewindow.png)

![](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/login.png)

![](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/checkUpdate.png)

![](https://github.com/nzaocan/IME-For-Minority-language-/blob/master/install.png)
