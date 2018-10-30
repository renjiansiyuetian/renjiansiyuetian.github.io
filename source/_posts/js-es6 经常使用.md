title: js-es6 经常使用
author: wangHianHui
date: 2019-01-05
tags:  
- es6
categories: ['es6']
---

 对象解包
 > const {a, b} = obj
直接能用变量a、b

---
数组解包
> [...state.cart.added]

---

async ->await->Promise

---
es6 的\`\`
> 要用一堆的'+'号来连接文本与变量，而使用ES6的新特性模板字符串\`\`后，例如:
<Link to={\`/taco/${taco.name}\`}>{taco.name}</Link>

---
es6对象解构
> let cat = 'ken'
let dog = 'lili'
let zoo = {cat, dog} 等价于 {cat: cat, dog: dog}
相反可以写为:
let dog = {type: 'animal', many: 2}
let { type, many} = dog

---
… 的使用
> function animals(...types){
    console.log(types)
}
animals('cat', 'dog', 'fish') //["cat", "dog", "fish"]

---
es6 文件以及文件里的函数 引入引出
> //index.js
import animal from './content'
//content.js
export default 'A cat'

---
