title: js项目小记录
author: wangHianHui
date: 2018-08-12 
tags:
- js
categories: ['js']
---
1、a标签上的，防止链接被随意修改而改变了跳转地址。
> rel="noreferrer" rel="noopener"  可合并为：
rel="noopener noreferrer" /// a标签上的，防止链接被随意修改而改变了跳转地址。
在跳转到第三方网站的时候，为了 SEO 权重，还建议带上 rel="nofollow”:
rel="noopener noreferrer nofollow”
{ 如果网站使用了 <a target="_blank">，那么新打开的标签页的性能将会影响到当前页面。此时如果新打开的页面中执行了一个非常庞大的 JavaScript 脚本，那么原始标签页也会受到影响，会出现卡顿的现象（当然不至于卡死）。
而如果在链接中加入了 noopener，则此时两个标签页将会互不干扰，使得原页面的性能不会受到新页面的影响。}

> 为了保护稍旧的“近代”浏览器或是很旧的“古代”浏览器甚至是“远古”浏览器，只有 noopener 属性还是远远不够的:
"use strict";
function openUrl(url) {
  var newTab = window.open();
  newTab.opener = null;
  newTab.location = url;
}