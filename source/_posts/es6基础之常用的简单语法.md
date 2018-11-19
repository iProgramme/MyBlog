---
title: es6基础之常用的简单语法
date: 2018/11/08
updated: 2018/11/13
tags: [js,es6,前端]
categories: js
---

本文主要讲解 ES6 中 **简单** **常用** 的一些简单语法，不做过深介绍，深入介绍可异步阮一峰大神的 [ECMAScript 6 入门](http://es6.ruanyifeng.com/#docs/intro)
## let 和 const

es6新增了两个声明变量的命令分别为 `let` 和 `const`

### let

let声明变量，在声明的时候才定义

特点：只在当前代码块中有效（注意是“代码块”，而不是“作用域”）

#### 用处

为何要用 `let` ：当我们希望一个变量只在当前代码块有效，而不影响当前作用域的时候使用，例如以下两种情况
```javascript
for(let i = 0;i<100;i++){

}
// 我们希望 i 仅仅在for循环里面使用
// 而且仅仅在当前的for 循环里面使用
```

```javascript
for(let key in obj){

}
// 我们希望 key 仅仅在for循环里面使用
// 而且仅仅在当前的for 循环里面使用，如果使用 var，最终会留下一个变量 key 在内存中
```

#### 用法解析
```javascript
for (let i = 0; i < 10; i++) {
    // ...
}
console.log(i);
// i is not defined
```
i 是在 `for` 循环里面声明使用的，故无法在外面使用

```javascript
for (let i = 0; i < 3; i++) {
    let i = 'abc';
    console.log(i);
}
```
上面代码正确运行，输出了3次 `abc` ，这表明循环内部（花括号内部）的变量 `i` 与循环变量 `i` 不在同一个作用域，有各自单独的作用域。

#### 暂时性死区

```javascript
var a = 123;
if (true) {
    a = 'abc'; // ReferenceError
    let a;
}
// a is not defined
```

上面的代码中，按原有逻辑分析，`a` 开始为 `123` ，在 `if` 里面使用的时候，会到上一级去寻找 `a` 的定义和赋值的地方 ，于是能赋值成功才对。
但该赋值会报错，是因为 `let` 导致的

ES6 明确规定，如果区块中存在 `let` 或 `const` 声明变量，那么在一开始就在当前代码块形成了一个块级封闭作用域，凡是在声明之前就使用这些变量，都会报错

于是就产生了一个很有意思的问题

```javascript
typeof a12345
let a12345
typeof a123456
```
会发现 `a12345` 是报错，而一个没有声明的变量 `a123456` 却是 `undefined` 

### const

其实在一般使用的时候 const 和 let 区别不大

#### const特点

const 旨在定一个固定不变的变量

注意：这个“固定不变”指的是内存地址

举例：

```javascript
const num = 10;
num = 20 // 报错

const obj = {age:12}
obj.age = 14 // no problem
```

## 字符串模板

这个的用处真的是太大了

我曾见过这样的代码：

不知道你们看到这样的代码的时候，内心是不是很激动啊😂

在 ES6 里面，如果有些地方不得不用字符串拼接的时候，可以这么使用

```javascript
var a,b,c,d,e = 10;
var html = '';
for(let i = 0;i<20;i++){
    html+= `
    <div>
        <span>${a}</span>
        <span>${b}</span>
        <span>${c}</span>
        <span>${d}</span>
        <span>${e*i}</span>
    </div>
    `
}
$(".xxx").append(html)
```
在ES6中可以用 \`  \` 来包裹字符串，
1. 在其中可以肆无忌惮的使用单引号和双引号。
2. 变量或者表达式 用 `${}` 包裹起来

## 箭头函数

ES6 里面提供了函数的简写，也就是箭头函数

```javascript
var ad = ()=>{
    console.log(123)
}
```

### 用处

```javascript
var sum = 0;
[1,2,3].map((item)=>{sum+=item})
// sum 6

// 也可以简写为
[1,2,3].map( item =>{sum+=item})
```

如果需要 `return` ，可以直接省略后面的花括号

```javascript
var arr = [1,2,3].map( item => item * 2 )
// [2,4,6]
```

### 例子

这里有个有意思的小例子

注意的是，箭头函数里面 `this` 的作用域，是在定义的时候生效的，而不是在运行的时候生效，具体看阮一峰大神的[注意点](http://es6.ruanyifeng.com/#docs/function#%E4%BD%BF%E7%94%A8%E6%B3%A8%E6%84%8F%E7%82%B9)

```javascript
var obj2 = {
    location:'博文',
    add:function(){
        console.log(this.location)
    }
}
// obj2.add() == '博文'
var obj2 = {
    location:'博文',
    add:()=>{
        console.log(this.location)
    }
}
// obj2.add() != '博文'
```
上面代码里面 `obj2` 里面的 `this` 发现指向的是 `window` 对象


## 数组和对象

数组和对象里面，用到的比较多的就是迭代吧

以前我们复制一个数组或者对象的方法是以下这样

```javascript
var arr1 = [1,2,3].concat([])
var arr2 = [1,2,3].splice()
var arr3 = Object.assign([],[1,2,3])
var obj1 = Object.assign({},{age:1})
```

方法很多就不一一列举了

在ES6中就方便多了

```javascript
var arr = [1,2,3]
var arr1 = [...arr]

var obj0 = {age:123}
var obj1 = {name:'xxx'}
var obj2 = {...obj0,...obj1}
```
不过要注意的是，这些复制的都是浅拷贝

### 数组常用方法

以下四个方法，平时用的比较多的方法

#### map
.map 不改变原数组，生成一个新的数组
```javascript
var arr = [1,2,3,4]
var sum = arr.map( item => item*2)
```
#### reduce
.reduce 不改变原数组，第一个参数为计算后的值，也是最后返回的值，后面才是 `item` , `index`
```javascript
var arr = [1,2,3,4]
var arrSum = arr.reduce( (sum,item) => sum+item)
// arrSum == 10
```
#### filter
.map 不改变原数组，生成一个新的数组
```javascript
var arr = [1,2,3,4]
var arr = arr.reduce( item => item >= 3)
// [3,4]
```
他跟 `.map` 方法很像，一般要对数据进行处理就用 `.map` 方法，而仅仅是过滤数据就用 `.filter`
#### includes
`.includes` 判断数组是否存在某值
```javascript
var arr = ['a','s','d','f']
arr.includes('s') // true
arr.includes('s',3) // true
```
`includes` 第二个参数，查询的起始位置