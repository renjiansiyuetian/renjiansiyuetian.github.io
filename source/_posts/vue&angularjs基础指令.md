---
title: vue与angularjs基础指令
date: 2017-02-16 10:33:13
tags:  
- vue
- angular.js
categories: ['js框架杂烩']
---
学过angularjs的同学，上手vue应该会特别简单。vue从某些方面上来说，就是简版的angularjs。
## 基础性使用
<!-- more -->
### 基础指令相比较

|  vue  | angularjs | 作用 | 使用是否相同 | 不同点 |
| ------|:---------:| ----:|
| v-if     |   ng-if  |  条件渲染指令(满足条件才会渲染在html里)       | 相同 |                           无                                        |  
| v-show   | ng-show  |  条件渲染指令(始终会渲染在html里)             | 相同 |                           无                                        | 
| v-model  | ng-model |  双向数据绑定                                 | 相同 |                           无                                        | 
| v-else   |   无     |  必须跟在v-if或者v-show的后面                 | 不   |                     angularjs无ng-else                              | 
| v-for    |ng-repeat |  基于一个数组渲染一个列表                     | 相同 |                           无 			                           | 
| v-bind   | ng-bind  |  前者用于响应地更新html特性后者为单向数据绑定 | 不同 | 前者主要用于属性绑定，为真者绑定其值如:`<a v-bind:href="url"></a>`  |   
| v-on     | ng-click |  作用一样，用法不一样。v-on的用法与v-bind相似 | 不同 | 前者例子:`<button v-on:click="say('Hi')">Hi</button>`               | 
### 补充
 - v-bind和v-on
v-bind指令可以缩写为一个冒号，v-on指令可以缩写为@符号。
完整语法:
``` bash
<a href="javascripit:void(0)" v-bind:class="activeNumber === n + 1 ? 'active' : ''">{{ n + 1 }}</a>
```
缩写语法:
``` bash
<a href="javascripit:void(0)" :class="activeNumber=== n + 1 ? 'active' : ''">{{ n + 1 }}</a>
```
完整语法:
``` bash
<button v-on:click="greet">Greet</button>
```
缩写语法:
``` bash
<button @click="greet">Greet</button>
```
