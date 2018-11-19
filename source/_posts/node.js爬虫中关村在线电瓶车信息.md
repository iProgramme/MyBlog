---
title: node.js爬虫中关村在线电瓶车信息
date: 2018/11/11
updated: 2018/11/13
tags: [js,node.js,爬虫]
categories: 爬虫
---

### 背景
最近打算买一辆电瓶车来上下班，但又不知道哪个好，网上是各说纷纭啊，于是就想着，干脆用node.js自己写一个小爬虫，来爬一下中关村在线里面电瓶车的信息吧。

（以后完整代码请前往 www.yubowen2003.com 暂时还在建设中，欢迎大家提issue😂 。）

### 简介
该demo采用node.js作为爬虫，为方便，有些地方使用es6语法，如有不懂，欢迎咨询😊

### 步骤
- 第一步，引入需要的库

```javascript
var cheerio = require('cheerio');
var fetch = require('node-fetch');

// cheerio 是一个类似浏览器端的jQuery，用来解析HTML的
// fetch 用来发送请求
```

- 第二步，设置初始的爬取的入口(我身处杭州，所以地区选了杭州的🤣)

```javascript
// 初始url
var url = "http://detail.zol.com.cn/convenienttravel/hangzhou/#list_merchant_loc"
// 由于每个a标签下是相对路径，故需要一个根地址来拼接，如下
var urlRoot = "http://detail.zol.com.cn" 
// 存放所有url，之所以用set，是为了防止有相同的而重复爬去
var urls = new Set()
// 存储所有数据
var data = [] 
```
至此，我们的准备部分结束了😅，接下来，开始表演了

- 分析网页，思考爬取的方式

![](https://user-gold-cdn.xitu.io/2018/11/9/166f73fbf48b2e8c?w=2558&h=1466&f=png&s=1941192)

每行4款，每页是48款，一共16页

思路：

1. 获取当前页48个链接。
2. 分别并点进去，拿到该电瓶车信息（名称和价格，其他信息获取方式一样，自行改就好😂）并存储。
3. 回到当前页，点击“下一页”
4. 获取下一页的信息
5. 重复步骤 1 - 4

具体实现方式，以下有注释

```javascript
// 这是得到每个页面的48个链接，并开始发送请求

function ad(arg){
    // 参数 arg 先不管
    // 本地化一下需要爬取的链接
    let url2 = arg || url;
    // 请求第一页该网页，拿到数据之后，复制给 app
    var app = await fetch(url2).then(res=>res.text())
    // 然后假装用jQuery解析了
    var $ = cheerio.load(app)
    // 获取当前页所有电瓶车的a标签
    var ele = $("#J_PicMode a.pic")
    // 存放已经爬取过的url，防止重复爬取
    var old_urls = []
    var urlapp = []
    //拿到所有a标签地址之后，存在数组里面，等会儿要开始爬的
    for (let i = 0; i < ele.length; i++) {
        old_urls.push(fetch(urlRoot+$(ele[i]).attr('href')).then(res=>res.text()))
    }
    // 用把URL一块丢给promise处理
    urlapp = await Promise.all(old_urls)
    // 处理完成之后，循环加入jQuery😂
    for (let i = 0; i < urlapp.length; i++) {
        let $2 = cheerio.load(urlapp[i],{decodeEntities: false})
        data.push({
            name:$2(".product-model__name").text(),
            price:$2(".price-type").text()
        })
    }
    // 至此，一页的数据就爬完了
    // console.log(data);
    
    // 然后开始爬取下一页
    var nextURL = $(".next").attr('href')
    // 判断当前页是不是最后一页
    if (nextURL){
        let next = await fetch(urlRoot+nextURL).then(res=>res.text())
        // 获取下一页的标签，拿到地址，走你
        ad(urlRoot+nextURL)
    }
    return data
}
ad()
```
完整代码如下

```javascript
var cheerio = require('cheerio');
var fetch = require('node-fetch');
var url = "http://detail.zol.com.cn/convenienttravel/hangzhou/#list_merchant_loc"
var urlRoot = "http://detail.zol.com.cn"
// var url = "http://localhost:3222/app1"
var urls = new Set()
var data = [] 
async function ad(arg){
    let url2 = arg || url;
    var app = await fetch(url2).then(res=>res.text())
    var $ = cheerio.load(app)
    var ele = $("#J_PicMode a.pic")
    var old_urls = []
    var urlapp = []
    for (let i = 0; i < ele.length; i++) {
        old_urls.push(fetch(urlRoot+$(ele[i]).attr('href')).then(res=>res.text()))
    }
    urlapp = await Promise.all(old_urls)
    for (let i = 0; i < urlapp.length; i++) {
        let $2 = cheerio.load(urlapp[i],{decodeEntities: false})
        data.push({
            name:$2(".product-model__name").text(),
            price:$2(".price-type").text()
        })
    }
    
    var nextURL = $(".next").attr('href')
    if (nextURL){
        let next = await fetch(urlRoot+nextURL).then(res=>res.text())
        ad(urlRoot+nextURL)
    }
    return data
}
ad()

```