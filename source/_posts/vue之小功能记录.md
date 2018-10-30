title: vue之小功能记录
author: wangHianHui
date: 2017-12-20
tags:
- vue
categories: ['vue']
---

### 一、滚动展示字
> 1）得知目前所有文字区域（包含隐藏起来的区域）的高度（clientHeight），减去展现出来的区域(以下以father称呼)高度，得文字的滚动区域（以下以scrollContent称呼）高度。
2) 将滚动区域scrollContent的设置为absolute，将展现出来的区域father设置为relative，通过计时器setInterval一定时间内挪动一定的距离便可。

* 参考代码如下：
		bind: (el) => {
		    Vue.nextTick(() => {
		    // bind 为自定义指令时的触发信号之一（ 只调用一次，指令第一次绑定到元素时调用，用这个钩子函数可以定义一个在绑定时执行一次的初始化动作）。nextTick()函数为该页面数据渲染完毕后执行，这样就可以得到真是的文字(后台返回)高度。
		          let scrollTop = el.clientHeight - 200 // 200为父亲高度，如此得滚动区域(scrollContent)高度
		          let tempTop = 0
		          function getInterval () {
		            el.intervalTime = setInterval(() => {
		              tempTop = -1 + tempTop // 1px为每次移动距离，如此计算为总的移动距离
		              if (-tempTop > scrollTop) {
		                el.style.top = 0 + 'px'
		                tempTop = 0
		              } else { // 执行条件为总的移动距离 小于 滚动区域(scrollContent)高度
		                el.style.top = tempTop + 'px'
		              }
		            }, 50)
		          }
		          el.addEventListener('touchstart', () => { // 监听关闭
		            window.clearInterval(el.intervalTime)
		            el.intervalTime = null
		          })
		          el.addEventListener('touchend', () => { // 监听再次开启
		            if (el.intervalTime !== null) {
		              return
		            }
		            getInterval()
		          })
		         // end
		        })
		      }    