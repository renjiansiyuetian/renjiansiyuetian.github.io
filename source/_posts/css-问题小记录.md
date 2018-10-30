title: css 问题小记录
author: wangHianHui
date: 2018-02-22 
tags:  
- css
categories: ['css']
---
解决h5页面在ios上卡顿:
> 在总的css控制里添加： *{
  -webkit-overflow-scrolling: touch;
  }

------------------------------
通过媒体查询可以为不同大小和尺寸的媒体定义不同的css，适应相应的设备的显示。
> 1. <head>里边<link rel=”stylesheet” type=”text/css” href=”xxx.css” media=”only screen and (max-device-width:480px)”>
2. CSS : @media only screen and (max-device-width:480px) {/css样式/}

------------------------------
伪类(:)的操作对象是文档树中已有的元素，而伪元素(::)则创建了一个文档数外的元素。

------------------------------
让页面里的字体变清晰，变细用CSS怎么做？
> -webkit-font-smoothing在window系统下没有起作用，但是在IOS设备上起作用-webkit-font-smoothing：antialiased是最佳的，灰度平滑。

------------------------------
position:fixed;在android下无效怎么处理?
> <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no"/>

------------------------------
png、jpg、gif 这些图片格式解释一下，分别什么时候用。有没有了解过webp？
> 1. png是便携式网络图片（Portable Network Graphics）是一种无损数据压缩位图文件格式.优点是：压缩比高，色彩好。 大多数地方都可以用。
2. jpg是一种针对相片使用的一种失真压缩方法，是一种破坏性的压缩，在色调及颜色平滑变化做的不错。在www上，被用来储存和传输照片的格式。
3. gif是一种位图文件格式，以8位色重现真色彩的图像。可以实现动画效果.
4. webp格式是谷歌在2010年推出的图片格式，压缩率只有jpg的2/3，大小比png小了45%。缺点是压缩的时间更久了，兼容性不好，目前谷歌和opera支持。

------------------------------
关于目前的仿原生开发
<!-- more -->
 ![2018年末总结的仿原生开发的问题](/img/native.jpg "2018年末总结的仿原生开发的问题")

 ------------------------------