---
title: es6基础之Promise
date: 2018/11/10
updated: 2018/11/13
tags: [js,es6，前端,Promise]
categories: js
---

网上很多的教程，都讲的很详细，这里就不赘述了

我只是希望你能用最快的方式学会使用它

## Promise 含义

Promise 是异步编程的一种解决方案，它由社区最早提出和实现，ES6 将其写进了语言标准，统一了用法，原生提供了Promise对象，是一个可以直接用的js对象（前端和node中都可以直接使用）

前端离不开异步编程，在以前，我们用 ajax 进行数据交互的时候，经常碰到这种情况
1. 先调接口登陆.
2. 成功之后调接口获取登陆信息
3. 成功后调用左侧导航
4. 成功后调用某个页面的初始化数据，
5. 成功后，调用接口查询表格


### 为什么要使用 Promise
这个时候，我们的代码就像这样

```javascript
$.ajax({
    url:'/url1',
    success:function(){
        // ...
        $.ajax({
            url:'/url2',
            success:function(){
                // ...
                $.ajax({
                    url:'/url3',
                    success:function(){
                        // ...
                        $.ajax({
                            url:'/url4',
                            success:function(){
                                // ...
                            }
                        })
                    }
                })
            }
        })
    }
})
```

丑是丑了点，也稍微有点难懂，典型的金字塔代码，但代码没毛病，能跑起来就ok。但是！！！最大的问题在于，明天产品脑子一热，告诉你“那啥，你把第二步和第四步的顺序调换一下”，瞬间想炸啊有木有😂！！！即使提出来，也逃不出层层回调的坑爹掌心😂

自从有了 Promise 之后，代码就变得好看了很多

```javascript
new Promise((resolve)=>{
    $.ajax({
        url:'/url1',
        success:function(){
            // ...
            resolve()
        }
    })
}).then(()=>{
    return new Promise((resolve)=>{
        $.ajax({
            url:'/url2',
            success:function(){
                // ...
                resolve()
            }
        })
    })
}).then(()=>{
    return new Promise((resolve)=>{
        $.ajax({
            url:'/url3',
            success:function(){
                // ...
                resolve()
            }
        })
    })
})
```
于是，我们就可以不断的 `new` 和 `then` 下去，而如果需要更改顺序，我们只需要调换两个 `then` 的顺序就好

所以，为什么要使用 `Promise` ？因为可以提高代码的可读性和可维护性

### 如何使用

`Promise` 的使用其实很简单，其实跟回调函数差不多，很容易懂

`Promise` 中带一个参数 `resolve` ，当异步操作结束之后，调用该方法就好，在外面就可以 `then` 了
```javascript
new Promise((resolve)=>{
    setTimeout(()=>{
        console.log(123)
        resolve()
    },300)
}).then(()=>{
    console.log(456)
})
// 123
// 456
```

总结： 虽然说 `Promise` 用起来很简单，但最好能自己手动实现一个 `Promise` 函数，另外， `Promise` 的用处很多，后面将陆续介绍