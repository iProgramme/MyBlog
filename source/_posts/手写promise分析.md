---
title: 手把手教你写promise，帮你分析promise的执行过程
date: 2018/11/20
updated: 2018/11/20
tags: [js,promise,es6]
categories: js
---

```javascript

function promise(fn){
    var that = this;
    var state = 'pending';
    var callbacks = []
    var value;
    function resolve(newValue){
        console.log(newValue);
        state = 'fulfilled';
        value = newValue
        console.log('-----------')
        setTimeout(function () { 
            callbacks.forEach(function (callback) {
                handle(callback);
            });
        }, 0);
    }
    function handle(obj = {}){
        console.log(state);
        if(state == 'pending'){
            callbacks.push(obj)
            return
        }
        if(!obj.onFulfilled) {
            obj.resolve(value);
            return;
        }
        var ret = obj.onFulfilled(value);  
        obj.resolve(ret) 
    }
    this.then = (onFulfilled)=>{
        console.log(2);
        return new promise((resolve)=>{
            console.log(3); 
            handle({
                onFulfilled:onFulfilled,
                resolve:resolve
            })
        })
    }
    fn(resolve)
    console.log(4);
}
new promise((res)=>{
    console.log(1);
    setTimeout(() => {
        res(111)
    }, 1000);
}).then((data)=>{
    return new promise((res)=>{
        console.log(6)
        setTimeout(() => {
            res(222)
        }, 1000);
    })
}).then((data)=>{
    console.log(5);
    setTimeout(() => {
        console.log(333);
    }, 1000);
})

```

分析代码的运行顺序

先假设所有的代码里面没有设立定时器

主线程打印顺序为 `1，4，2，3，4，2，3，4`

1. new promise()   -- 打印 1，打印 4
2. .then()  -- 打印 2
3. .then 里面的 new promise() -- 打印 3，打印 4
4. 第二个 .then -- 打印 2
5. 第二个 .then 里面的 new promise() -- 打印 3，打印 4

主流程走完

主流程解释：
1. new promise() 为 new 了一个对象，上面都是变量方法的初始化，真正的代码只有两行就是 `fn(resolve);console.log(4);` 所以先出 1，后出 4
2. .then()  打印 2，然后返回一个 new promise()
3. 上一步返回的 new promise() 运行，打印3（这个过程也就是执行了 handle 的过程），然后打印 4
4. 由于上一步返回的是一个新的 promise 对象，所以在外面可以直接再次 .then 而不会报错，那么这一次的 .then() 也就是上一个 promise 的then 而不是第一步里面的 new promise()