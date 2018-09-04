# IME For Minority Language
`小语种输入法`支持梵文、巴利文、西夏文、藏文、婆罗米文等。
支持平台：Windows7，8，10；UWP。

本文是对项目的简介，描述大致的轮廓和使用到的技术。

`小语种输入法`为私有项目，所有权归企业，因此仓库没有代码，也没有任何项目文件。

`小语种输入法`由作者独立设计和完成。
<br/>
<br/>
### 设计模式 - `MVVM & MVC` ###

项目逻辑上被划分为三块：
1. 远程服务 - 使用 HTTP/HTTPS,FTP与本地服务进行数据同步。
2. 本地服务 - 基于远程服务和本地数据，为输入法端提供计算服务。
3. 输入法端 - 使用 TCP 与本地服务进行状态同步。

设计模式和语言
1. 远程服务设计模式和语言 MVC JAVA
2. 本地服务设计模式和语言 MVVM C#
3. 输入法端语言          C++

基于WPF的特性，本地服务端选用了`MVVM`

`MVVM`View和View-Model之间具有松耦合的特性

因此，在项目中将GUI与业务逻辑进行了分离，降低了复杂度、同时也保证了质量。

<br/>
<br/>

### 支持Windows多平台 - `Text Service Framework（TSF）` ###

Windows输入法开发由于文档很少，组织也比较混乱，因此存在一定的开发难度。

在可查到的公开信息中，没有发现对TSF框架的内部逻辑细节描述的文档。

微软仅仅给出一个基于TSF框架实现的输入法样例，并且未作任何说明。

本项目修改基于TSF框架的输入法样例，并在其中嵌入计算和通信模块，完成了输入法端的工作。

<br/>
<br/>



### 进程同步-`TCP SOCKET` ###

TSF框架中内置了简单的GUI模块，但为了实现更复杂的GUI，并且绕开TSF框架中复杂的数据结构

设计了本地服务端，并且屏蔽了TSF中的GUI，所以本地服务端和输入法端需要做数据同步。

由于匿名管道用于亲子关系的进程同步，而命名管道在UWP技术中被禁用。

所以项目使用了windows socket作进程同步的基础，由于项目私密原因，在此不作具体说明。

进程同步涉及到的知识点有：`阻塞与非阻塞模式`、`字符的编码`、`多进程的管理`。

<br/>
<br/>


### 自然语言处理 ###

#### NLP-拼写错误纠正-`最小编辑距离` ####

拼写错误纠正基于`最小编辑距离`算法实现，算法定义如下图，本项目基于此算法，为用户给出纠正后的候选项。

<img width="400" src="https://github.com/nzaocan/IME-For-Minority-language-/blob/master/minDistance.png"/>
<br/>


#### NLP-候选列表生成-`LRU Cache`的应用 ####

LRU Cache 是操作系统中的一个概念，直译为最近最少使用缓存。

一般来说，用户的常用词汇是有限的，将用户输入和选择的候选项放入LRU Cache中，可以帮助用户快速的输入常用的词汇。

本文使用链表和哈希表（键值对）实现，维护LRU Cache涉及大量的删除/查找操作，因此选用了删除/查找时间为o(1)的链表/哈希表。

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
