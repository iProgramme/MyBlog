---
title: 如何开启hexo下next主题的优化与特效
tags:
  - hexo
  - next
  - hexo-theme-next
categories:
  - hexo
abbrlink: af303a63
date: 2023-11-30 09:29:39
---

# 如何开启hexo下next主题的优化与特效

## 1. 确认已安装hexo

安装完的目录应该如下图

![](image-20221130092728749.png)

## 2. clone next 主题到本地

```bash
git clone https://github.com/theme-next/hexo-theme-next.git themes/next
```

在此注意：这里的地址是最新的，网上很多的教程的地址都是老的 next 地址

## 3. 安装依赖

```bash
npm install
```

## 4. 配置 hexo 主题

在 `_config.yml` 中配置 hexo 主题

```yml
theme: next
```

至此，可以 `hexo server` 来查看效果如下图

![](image-20221130092900864.png)

## 5. 配置 canvas_nest 效果

```javascript
// 找到文件 /themes/next/layout/layout.swig
// 在文件的body标签内的末尾添加

{% if theme.canvas_nest %}
<script type="text/javascript" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js"></script>
{% endif %}
```

```yml
# 找到文件 /themes/next/_config.yml
# 增加以下代码
canvas_nest:
  enable: true
```

重启 hexo 服务后如下图

![](image-20221130093101260.png)


## 6. 插入图片

```yml
# 找到文件 /themes/next/_config.yml
# 增加以下代码
post_asset_folder: true
marked:
  prependRoot: true
  postAsset: true
```

按照以下方式使用图片

```markdown
![image-20221130093101260](image-20221130093101260.png)
```

如果有需要的话请安装 hexo-renderer-marked 

```bash
npm install hexo-renderer-marked --save
```

## 7. 图片点击放大预览

```yml
# 找到文件 /themes/next/_config.yml
# 修改以下代码
fancybox: true
```

## 8. 图片懒加载

```yml
# 找到文件 /themes/next/_config.yml
# 增加以下代码
lazyload: true
```
## 9. 设置404页面

```yml
# 找到文件 /themes/next/_config.yml
# 增加以下代码
404:
  path: /404.html
  per_page: false
```
然后在 `404.html` 中写入如下代码

## 10. 添加站点访问人数和总访问量

```yml
# 找到文件 /themes/next/_config.yml
# 增加以下代码
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: fa fa-user
  total_views: true
  total_views_icon: fa fa-eye
  post_views: true
  post_views_icon: fa fa-eye
```

## 11. 添加字数统计及阅读时长

```yml
# 找到文件 /themes/next/_config.yml
# 增加以下代码
readingtime:
  enable: true
```

## 12. 添加评论

```yml
# 找到文件 /themes/next/_config.yml
# 增加以下代码
comment:
  enable: true
  type: gitalk
```

## 13. 增加打赏功能

```yml
# 找到文件 /themes/next/_config.yml
# 增加以下代码
reward:
  enable: true
  wechat: image-20221130092900864.png
  alipay: image-20221130092900864.png
```

## 14. 修改永久链接的默认格式

安装 hexo-abbrlink

```bash
npm install hexo-abbrlink --save
```

```yml
# 找到文件 /themes/next/_config.yml
# 修改以下代码
permalink: posts/:abbrlink.html
abbrlink:
  alg: crc32  # 算法：crc16(default) and crc32
  rep: hex    # 进制：dec(default) and hex
permalink_defaults: posts/:abbrlink.html
```

