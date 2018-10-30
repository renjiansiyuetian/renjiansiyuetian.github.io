title: css 基础经常使用
author: wangHianHui
date: 2017-06-27 15:05:11
tags:
- css
categories: ['css']
---
1. 换行省略
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
2. 强制换行
        white-space: normal; //中英文都支持
        word-wrap: break-word; //支持英文
        word-break: break-all; //支持英文
3. 多行省略
        display: -webkit-box; 
        -webkit-box-orient: vertical; 
        -webkit-line-clamp: 3; 
        overflow: hidden;
        text-overflow: ellipsis;
4. 宽度已知，让高度与宽度1:1变化
        例如:
        .item-flex {
          width: 102px;
          .img-flex {
            height: 0px;
            padding-bottom: 100%;
          }}
    >采用的方法是利用了padding-top/padding-bottom属性,根据他的解释,`padding’如果是百分比的话,那这个百分比是相对于其父元素的宽度而言的。
    
**资料:来源<http://www.jianshu.com/p/56a3adebdb01/>**
- 
而作者使用到了另一个属性overflow,另外，在计算 Overflow 时，是将元素的内容区域（即 width / height 对应的区域）和 Padding 区域一起计算的。换句话说，即使将元素的 overflow 设置为 hidden，“溢出”到 Padding 区域的内容也会照常显示。**

- 这样就能使用padding-top/padding-bottom来代替height属性了.比如你想要让元素的按在4:3的比例显示,width设置成了30%,那么padding-top/padding-bottom只需要设置成为
40%就可以了.同时把height设为0.css代码如下:
      .img-3-4 {
        margin: 10px;
        padding-bottom: 30%;
        width: 40%;
        height: 0;
        background-color: #dbe0e4;
      }
5.在每一个item中的图片都能按照规定的比例显示.对于image标签来说,如果是自然的显示原图片的比例
      .img {
         display: block;
         max-width: 100%;
         height: auto;	
      }
      
6.flex布局:<http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html>

7.头部meta设置<http://blog.csdn.net/huang100qi/article/details/42596799>

8.vertical-align
- vertical-align对块状水平的元素是没有效果的。
- <https://segmentfault.com/a/1190000002668492>

      Vertical-align被用于垂直对齐inline元素，也就是display值为inline和inline-block的元素。
      vertical-align基线改变：
        a:普通inline-block的基线是文字内容的下边界；
        b:overflow不为visible的与设置了height的，基线都为margin-box的下边界。
        
9.contenteditable属性兼容所有浏览器

    <div contenteditable=“true">可以编辑里面的内容</div>  
    
10.左边定宽，右边自适应

  >首先，aside定宽 section不定宽度

    <aside>left</aside>
    <section>right</section>
- 左边设置左浮动，右边宽度仅设置100%
      .left{ float:left; } 
      .right{ width:100% }
- 父容器设置display:flex，right部分设置flex:1
      .father { display:flex } 
      .right {flex:1}	
- 设置左右浮动，右边的浮动width为calc(100vw-200px)
	  .left { float:left } 
      .right{ float:right; width:calc(100vw-200px) }
- 用负margin，页面结构：
      <div class=“container”>
          <section class=“right”>right</section>
      </div>
      <aside class=“left”>
          left
      </aside>
  设置样式：
      .container { float:left; width:100%; }
      .right{ margin-left:200px; }
      .left{ float:left; margin-left:-100%; }

11.box-sizing
      box-sizing:content-box/border-box/inherit 
      content-box——默认值，采用Standard box model 
      border-box——采用IE box model 
      inherit——继承父元素属性值

12.局部图片滑动 
* 在要滑动的list img之前，加上父亲元素outer和inner。将
outer设置为:
        .outer {
            position: relative;
            overflow: hidden;
            min-height: XX px;
        }
        .inner {
            position: absolute
            left: 0;
            right: 0;
            overflow-x: scroll;
            overflow-y: hidden;
        }

  然后 list img正常设置便可。

13.input date的兼容性问题
* Input date在pc端的兼容性还是比较差的，除了chrome支持以为，其它几乎都不能使用。但在移动端的兼容性还是可以的。故如若在移动端使用，还需要考虑其placeholder的兼容性，因为placeholder仅在pc端显示，在移动端是不支持的。
        解决方案：
        通过标签上某个属性的改变,从而仿placeholder，例如:
        //当有值时，设置其添加class空样式: has-value,没有值时便显示placeholder
        input[type="date"]:not(.has-value):before {
          color: grey;
          content: attr(placeholder);
        }
        // 清空placeholder的条件
        input[readonly]:before {
            content: '';
        }

14.JPEG、PNG、SVG
http://web.jobbole.com/91599/
> * JPEG适用于亮度与色彩压缩。
* PNG对于线条图，LOGO，图标和颜色较少的图像非常适合。
* SVG在线条艺术，LOGO，图标，插画和数据可视化方面用途广泛。

15.头部中部尾部布局
* 1)头尾fixed,中部absolute
        html,body{width:100%;height:100%;position:relative;}
        #body-container{width:100%;height:100%;position:absolute;left:0;top:0;}
        #header{position:fixed;left:0;top:0;width:100%;height:49px;}
        #content{position:absolute;left:0;right:0;top:49px;bottom:44px;overflow-y:auto;}
        #footer{position:fixed;left:0;;bottom:0;width:100%;height:44px;}
* 2)lex布局（仿照手机淘宝布局）
        *{margin:0;padding:0;}
        html,body{width:100%;height:100%;position:relative;}
        #body-container{width:100%;height:100%;display:flex;flex-direction:column;}
        #header{height:49px;flex:none;}
        #content{flex:1 1 auto;overflow-y:auto;}
        #footer{height:44px;flex:none;}

16.clearfix进化史
http://web.jobbole.com/85965/

17.宽比成比例的
        width: 100%;
        height: 0px;
        padding-bottom: 50%;
        display: inline;         

18.pre换行
        white-space:pre-wrap;
        word-wrap: break-word; 

19.video的坑
http://web.jobbole.com/93251/

        <video controls>
          source src="https://chimee.org/vod/2.webm">
          source src="https://chimee.org/vod/2.ogg">
          source src="https://chimee.org/vod/2.mp4">
          source src='https://chimee.org/x.myvideoext' type='video/mp4; codecs="mp4v.20.8, mp4a.40.2"'>
          p>当前环境不支持video标签。p>
        </video>

20.杂项
- AA:大转盘
http://www.daxueit.com/article/16703.html
- BB:移动端问题记录
http://blog.csdn.net/k513492640/article/details/73997607
- CC:前端踩坑大杂烩
http://www.cnblogs.com/fastmover/p/4873765.html
- DD:rem
https://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=2651552493&idx=1&sn=84144094bfcbbca5c3f78907f49d4787&chksm=8025ad2cb752243aa0d6975cbeaf95490810fe456f00f8562bde7aeb3366c0bbd9a4f516271f&scene=0&key=e4a4e74651de5963d522bfff8727ce52c074dbd253178438b52bd5b53a9a5a6d2b20704bf69eb40d56e6f71a42544927d99ef5ac2762df11bd170e348b6aa0b10e751f85db359075f67f7f014cfbf968&ascene=0&uin=MjY2MDUwNzgxOQ%3D%3D&devicetype=iMac+MacBookPro13%2C1+OSX+OSX+10.12.3+build(16D30)&version=12020810&nettype=WIFI&fontScale=100&pass_ticket=2dqCIt261iAAt7GpaL0SRS%2F4Mid9NkzIn3iVdaL5FsJG2e61K0rbo5lgjkV6lkfg
- EE: 利用视口单位实现适配
https://aotu.io/notes/2017/04/28/2017-4-28-CSS-viewport-units/              