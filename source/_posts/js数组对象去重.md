---
title: js 数组对象去重
date: 2018/11/20
updated: 2018/11/20
tags:
  - js
  - es6
categories: js
abbrlink: ffa2c49f
---

在js中，我们经常会碰到这样的一个问题：给一个数组对象去重

如下

```javascript
var arr = [
    {id:123,name:'xxx',age:12},
    {id:124,name:'xxx',age:12},
    {id:125,name:'xxx',age:12},
    {id:126,name:'xxx',age:12},
    {id:127,name:'xxx',age:12},
    {id:128,name:'xxx',age:12},
    {id:129,name:'xxx',age:12},
    {id:121,name:'xxx',age:12},
    {id:122,name:'xxx',age:12},
    {id:123,name:'xxx',age:12},
    {id:124,name:'xxx',age:12},
    {id:125,name:'xxx1',age:12},
]
// 任务是将两个所有属性值相同的对象，只保留一个
```

我们知道，如果数组里面是简单数据类型，我们可以直接用 `es6` 的 `Set()` 就可以完成去重，那么对于数组中每一项都是对象的，如何去重才是最好的方式呢

按照正常思维，就是将数组每一项和后面的每一项的每一个属性值做对比，如果全部相同，那么就保留一个，我们很容易写出类似如下的代码：

```javascript
var add = [arr[0]]
for(var i = 0;i < arr.length;i++){
    var flag = true
    for(var j = 0;j < add.length; j++){
        var arrIstr = []
        var addIstr = []
        for(var key in arr[i]){
            arrIstr.push(arr[i][key])
            addIstr.push(add[j][key])
        }
        if(arrIstr.join('') == addIstr.join('')){
            flag = false
            break
        }
    }
    if(flag){
        add.push(arr[i])
    }
}
```

这么一大堆，层层的循环，无数的判断，分分钟想炸啊有木有，而且谁能明白，你这么一大堆的代码，目的仅仅是为了给一个数组对象去重😂

那么有什么其他的好一点的办法去重吗？有人会说了 ， ` es6 ` 啊，那么我们看看一般的 ` es6 ` 写法如何