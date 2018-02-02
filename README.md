# 安卓开发框架（MVP+主流框架+基类+工具类）

## 简介

使用**MVP模式**、**Retrofit**(网络请求)+**RxJava**(异步操作)、**GreenDAO**(数据库操作)、**Fresco**(图片加载)、**EventBus**(事件通信)、**ButterKnife**(资源绑定)、**基类**、**工具类**搭建的一个安卓开发框架。<br>
<br>
包含了开发中常用的模块，以便日后可在其基础上进行新项目的快速开发<br>
<br>
简单写了个豆瓣电影例子，演示以上各模块的使用（内含详细的代码注释），配合对应的文章能更好地理解（下方有传送门）<br>


## demo

>demo大致的流程如下：
>1. 使用Retrofit+Rxjava请求豆瓣电影API，获取“正在上映”和“即将上映”的电影数据。
>2. 将数据通过两个Fragment以列表的形式进行展示，其中图片的显示使用Fresco进行加载。
>3. 点击列表项，使用GreenDAO将该电影插入到本地数据库中，并且刷新Toolbar右侧收藏的数量。
>4. 点击toolbar右侧的收藏，进入收藏页面，使用GreenDAO从本地数据库中获取数据并进行展示。
>5. 点击列表项，则将该电影从本地数据库中移除并刷新列表展示，同时使用EventBus通知上个页面刷新Toolbar右侧的收藏数量。
>6. 以上过程中，使用ButterKnife进行视图绑定，按照MVP模式进行开发，穿插使用了各种基类、工具类。


**demo运行图:**

![demo演示效果1](https://github.com/LJYcoder/DevBase/blob/master/demo_run.gif)

![demo演示效果2](https://github.com/LJYcoder/DevBase/blob/master/demo_run2.gif)


### 包结构

项目代码整体分为5个包，如下图所示：

![包结构](http://img.blog.csdn.net/20171010094014110?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGp5X3Byb2dyYW1tZXI=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


其中，<br>
**app包**：存放全局性文件。如Application类，常量类等。<br>
**model包**：存放数据处理/模型相关的文件。如实体类，数据库相关文件，网络请求相关文件等。<br>
**presenter包**：存放业务逻辑服务相关的文件。<br>
**util包**：存放工具类。<br>
**view包**：存放视图相关的文件。如activity，fragment，adapter，自定义控件等。<br>

可以建多一个**other**包，用来存放Service，BroadcastReceiver，蓝牙，友盟等其他内容模块。<br>

