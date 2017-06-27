title: css 基础经常使用
author: wangHianHui
date: 2017-06-27 15:05:11
tags:
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