title: vue项目搭建
author: wangHianHui
date: 2017-11-01
tags:
- vue
categories: ['vue']
---

### 插件结合搭建vue项目
1) axios: https://github.com/superman66/vue-axios-github
2) 基于 vue + element-ui 的后台管理系统: https://github.com/bailicangdu/vue2-manage
3) 基于vue+vue-router+vuex+axios+webpack开发的个人Demo:https://github.com/hzzly/xyy-vue
4) 搭建vue2(用的gulp)： https://github.com/lzxb/vue2-demo
5) vue2.0的一些文章: https://github.com/WYseven/vue2-basic-demo
6) 搭建vue2.0很不错的文章：https://segmentfault.com/a/1190000007630677#articleHeader7 {(初级搭建是根据此文章搭建的)
> 后继：根据上述资料设置sass与axios:
npm install node-sass –save-dev
npm install sass-loader –save-dev
npm install axios —save
npm install vuex-router-sync —save
npm install eslint-friendly-formatter —save-dev
根据1）中axios配置http响应
配置 autoprefix即自动加上css前缀:
{
npm install postcss postcss-cssnext —save-dev
然后在vue-loader.conf.js里配置:
postcss: [require(‘postcss-cssnext’)()]

* 例如:
		module.exports = {
		  loaders: utils.cssLoaders({
		    sourceMap: isProduction
		      ? config.build.productionSourceMap
		      : config.dev.cssSourceMap,
		    extract: isProduction,
		    postcss: [require('postcss-cssnext')()]
		  }),
		  postcss:[require('postcss-px2rem')({'remUnit':37.5, 'baseDpr': 1})],
		  transformToRequire: {
		    video: 'src',
		    source: 'src',
		    img: 'src',
		    image: 'xlink:href'
		  }
		}
}
7) vuex-router-sync: Effortlessly keep vue-router and vuex store in sync。主要是把 vue-router 的状态放进 vuex 的 state 中，这样就可以通过改变 state 來进行路由的一些操作。
8) vue插件机制及模板渲染: https://github.com/Cyrilszq/Cyril-Blog/issues/2
9) postcss 与Autoprefixer的区别:
> ~ 两者都是基于 CSS 处理框架 postcss 的（postcss 就是 Autoprefixer 的作者把 Autoprefixer 从另一个 CSS 处理框架 rework 中迁移出来时搞的）。相比之下，Autoprefixer 更加具有实用价值，而 cssnext 实现的功能以后浏览器会怎么实现还存疑，感觉只能玩玩。
~ cssnext: CSS 的转译器（transpiler），根据目前仍处于草案阶段、未被浏览器实现的标准把代码转译成符合目前浏览器实现的 CSS。类似 ES6 的 Babel。转译时因为也要处理前缀问题，所以直接依赖了 Autoprefixer 来做这个部分
~ autoprefixer 只加前缀，cssnext 依赖 autoprefixer(core) ，并附带其他功能。		