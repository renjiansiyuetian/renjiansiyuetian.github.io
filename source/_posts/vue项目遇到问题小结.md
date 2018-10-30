title: vue 项目遇到问题小结
author: wangHianHui
date: 2018-01-16
tags:
- vue
categories: ['vue']
---
### vue问题小结
1）引入全局的scss（一般在app.vue里引入），其中若涉及@mixin 与 @include，样式不起作用。
2）布局样式重置全局样式，无效，必须去掉scoped。
3）将ui框架组件集合在一起全局声明。
4）v-for 报错，解决方式: 加上属性:key=“item.id”便可。
5）兄弟组件之间调用函数：
> 在离开页面时执行并解除绑定
beforeDestroy: function () {
this.$off(‘updateProfile’, this.updateProfile())
}
在离开页面时，获取从哪来到哪去
beforeRouteLeave: function (to, from, next) {
if (to.name !== ‘BalanceHistory’) {
localStorage.removeItem(‘query’)
}
next()
},

6）watch里面 es6语法不能用（2017年时候）。
7）新的2.0循环
> 新数组语法
value in arr
(value, index) in arr
新对象语法
value in obj
(value, key) in obj
(value, key, index) in obj

8）vue循环过滤
> v-for=”val in arr | limitBy 2” 在2.0之后不能再用，
用computed代替：
computed: {
filteredItems: function () {
return this.items.slice(0, 10)
}
}
v-for=”val in filteredItems”

9）$set
> 在js中是这样 arr[id] = value, 这样便完成了可以通过下标设置值。
但是在vue中，这样虽然也可以，但是其后期值得变化更新是不会同步到dom上的，
所以，需用此代替:
this.$set(this.arr, id, value)。其中,this为vue对象。
官方文档是如此介绍：
vue-set设置对象的属性。如果对象是响应式的，确保属性被创建后也是响应式的，同时触发视图更新。这个方法主要用于避开 Vue 不能检测属性被添加的限制。

10）页面传值
> 赋值:this.$router.push({ name: ‘xx’, query: this.q })
接收：if(Object.keys(this.$route.query).length > 0) {
this.q = this.$route.query
}

11）vue中通过$ref操作dom
* 例如:
		<ul>
		  <li ref=“li”></li>
		  <li ref=“li”></li>
		  <li ref=“li”></li>
		</ul>
		则加class li样式时，则可以如此(注意li上的id是唯一的):
		changeItem (ob) {
		  this.$refs.li.forEach((item, index) => {
		    if (this.$refs.li[index].id === ob.target.id) {
		      this.$refs.li[index].className = 'li'
		    } else {
		      this.$refs.li[index].className = ''
		    }
		  })
		} 
12）在子组件中修改父组件的值
> 父组件中:
		<select-option class=”bottom” :banks=”banks” :currentBank.sync=“currentBank”></select-option>
注意父组件中的sync后带着的变量currentBank。
——————————————————————————————————————
子组件中:
在子组件里可以如此去修改currentBank的值:
		this.$emit(‘update:currentBank’, item)

13）mode为history，刷新失效
* mode: ‘history’,
可以使路由去掉#，但是会使本路由刷新(比如本路由的参数变化时，理想情况是本页面数据也变化)失效。
解决方法: 在对应的router-view上加key：		
		<router-view :key=“routeKey"></router-view>
		computed: {
		 routeKey () {
		  return `${this.$route.path}`
		 }
		},

14）页面数据不刷新
> 当你设置 vm.someData = ‘new value’ ，该组件不会立即重新渲染。可以在数据变化之后立即使用 Vue.nextTick(callback)。

15）组件
> Vue 组件的 API 来自三部分 - props, events 和 slots ：
Props 允许外部环境传递数据给组件
Events 允许组件触发外部环境的副作用
Slots 允许外部环境将额外的内容组合在组件中。

16）Vuex
> 1、在使用store时，尽量用commit来触发mutation达到改变state数据的目的。
2、通过在根实例中注册 store 选项，该 store 实例会注入到根组件下的所有子组件中，且子组件能通过 this.$store 访问到。
3、在组件中使用 this.$store.dispatch(‘xxx’) 分发 action。	

17) 数据渲染
> 初始化数据时，用mounted钩子，但不能保证实例已经插入到文档，所以在钩子函数里包含 Vue.nextTick():
mounted: function () {
this.$nextTick(function(){
//保证this.$el已经插入文档
})
}

18)其它vue问题小结（某位同学的）
https://segmentfault.com/a/1190000005832164
http://web.jobbole.com/93298/


