title: js常用小记录
author: wangHianHui
date: 2017-02-02 
tags:
- js
categories: ['js']
---
### 一: 自带的函数
1) split、splice、slice的区别:
http://blog.csdn.net/zpw91/article/details/53705462
* Split()
> Split是切割字符串的一种方法，该方法主要用于把一个字符串分割成字符串数组。
var s= ‘how do you do’;
var b = s.split(“ ”);//空格分割 how,do,you,do
* Splice () (会改变本尊数组)
> Splice ()方法向/从数组中添加/删除元素，然后返回被删除的元素组成的数组。用于数组对象。arr.splice(index, howmany, item1,…, itemX)
其中：
index
必需。整数，规定了添加/删除元素的位置，使用负数可从数组结尾处规定位置。
howmany
必需。要删除的元素的数量。如果设置为0，则不会删除元素。如果添加元素则这里应该设置为0.
itemX
可选。向数组添加的新项目。在添加的时候用。
* Slice()（不会改变本尊数组）
> slice()方法主要用于截取数组，并返回截取到的新数组。 数组和字符串对象均可以使用。 arr.slice(start, end)

2) scrollIntoView
> scrollIntoView(alignWithTop) 滚动浏览器窗口或容器元素，以便在当前视窗的可见范围看见当前元素。如果alignWithTop为true，或者省略它，窗口会尽可能滚动到自身顶部与元素顶部平齐。

3) Object.keys(对象) => 判断一个对象是否为空

4)enxtype几种方式:
> application/x-www-form-urlencoded (默认，正常的提交方式)
multipart/form-data(有上传文件时常用这种)
application/json (ajax常用这种格式)
text/xml
text/plain

5）文件上传，不经过form表单提交，可以借用h5的FormData。
* 例如:
		const config = { headers: { 'Content-Type': 'multipart/form-data' } }
		let fd = new FormData()
		fd.append('file', this.file) // this.file为上传的文件信息
		// fd传过去为data字段，如此post请求，便可以将文件传至后台接收
		this.api.postUploadAvatar(fd,  config)

6)文件上传时，本地显示:
> var src=window.URL.createObjectURL(blob)//这里传一个文件对象 例如：file.files[0]
img.src=src;

7) css解决ios scroll 不流利, js解决安卓端键盘遮挡
https://segmentfault.com/a/1190000008788147

8) requestAnimationFrame
> requestAnimationFrame与setTimeout和setInterval类似，都是通过递归调用同一个方法不断更新页面。

9）变量
// js核心 （提到变量）
http://web.jobbole.com/91737/
> 以前的作用域只有两种（如果非要加上eval()，那就是三个，即还有eval函数作用域）:全局作用域, 函数作用域（A）。
在还是A时，出现了一个术语，叫做“变量提升”。即var声明的变量，在作用域里执行时，会被置到最前面并赋值为undefined。如果此变量已赋值在某位置，只是在后面而已（例如: var x=2），则会再其位置处，将undefined的变量赋为其值（例如赋值为2）。
* es6出现后，有了let与const。let与var的区别:
1）let 的作用域只在其处于的块级内。
2）let没有所谓的“变量提升”(更精确来说，应该是提升了，不过就是不让你用，所以是为“暂时性死区”)。

10）杂项
* Rem
		// rem
		let html = document.querySelector('html')
		let width = html.getBoundingClientRect().width
		html.style.fontSize = width / 10 + 'px'
* 手机端禁止缩放
		// 禁用双指缩放
		document.documentElement.addEventListener('touchstart', function (event) {
		  if (event.touches.length > 1) {
		    event.preventDefault()
		  }
		}, false)
		// 禁用手指双击缩放
		let lastTouchEnd = 0
		document.documentElement.addEventListener('touchend', function (event) {
		  let now = Date.now()
		  if (now - lastTouchEnd <= 300) {
		    event.preventDefault()
		  }
		  lastTouchEnd = now
		}, false)
* 解决安卓端键盘遮挡:
		// input
		let u = navigator.userAgent
		let isAndroid = u.indexOf('Android') > -1 || u.indexOf('Adr') > -1 // android终端
		if (isAndroid) {
		  let beforeHeight = document.documentElement.clientHeight
		  window.addEventListener('resize', function () {
		    let afterHeight = document.documentElement.clientHeight
		    if ((beforeHeight - afterHeight) > 50) {
		    } else {
		      document.getElementById('scroll').style.top = 'initial'
		    }
		  })
		  window.addEventListener('focusin', function () {
		    document.getElementById('scroll').style.top = -50 + 'px'
		  })
		  window.addEventListener('focusout', function () {
		    document.getElementById('scroll').style.top = 'initial'
		  })
		 }
或者，简单点：
		if (/Android/gi.test(navigator.userAgent)) {
		  window.addEventListener('resize', function () {
		    if (document.activeElement.tagName === 'INPUT' || document.activeElement.tagName === 'TEXTAREA') {
		      window.setTimeout(function () {
		        // document.activeElement.scrollIntoViewIfNeeded()
		        document.activeElement.scrollIntoView(true)
		      }, 300)
		    }
		  })
		}

11) 关于for循环
1、![js(for-of)](/img/for-of.jpg "js(for-of)")
2、![js(for-key)](/img/for-key.jpg "js(for-key)")


