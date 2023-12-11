---
title: 全网最全的hexo配置yml详解
abbrlink: ee857af2
date: 2023-12-06 16:21:04
tags:
---

该文章主要讲述了 hexo 的yml配置，包含每个字段的解释和作用，帮助你快速上手和配置hexo的各项信息和功能。

```yml
# Hexo 配置
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# 站点
title: 郭减
subtitle: '前端开发工程师，前端爱好者'
description: '前端开发工程师, 前端爱好者, 前端博客,javascript, nodejs, react, html, css, python, git,hexo, next'
keywords:
author: 郭减
language: zh-CN
timezone: ''

search:
  path: search.xml
  field: post
  format: html
  limit: 10000
local_search:
  enable: true
# URL
## 在这里设置你的站点. 比如, 如果你使用 GitHub Page,设置 url 为 https://iprogramme.github.io/MyBlog/  其中 iprogramme 是 username，MyBlog 是你的博客地址。
url: https://iprogramme.github.io/MyBlog/
root: /MyBlog/
# 永久链接格式，如果不填，则默认的是: :year/:month/:day/:title/
# 我这里使用了 abbrlink 插件，作用在于生成文章的永久链接，避免在更改文章标题时，SEO没有和评论全部消失等情况。
permalink: posts/:abbrlink.html
# 缩略链接配置
abbrlink:
  alg: crc32  # 算法：crc16(default) 和 crc32
  rep: hex    # 进制：dec(default) 和 hex
# 永久链接默认格式
permalink_defaults: posts/:abbrlink.html
# 美化链接设置
pretty_urls:
  trailing_index: false # 设置为 false 以从永久链接中移除结尾的 'index.html'
  trailing_html: false # 设置为 false 以从永久链接中移除结尾的 '.html'

# 目录设置
source_dir: source          # 源文件目录
public_dir: MyBlog          # 公共输出目录
tag_dir: tags               # 标签页目录
archive_dir: archives       # 存档目录
category_dir: categories    # 分类目录
code_dir: downloads/code    # 代码目录
i18n_dir: :lang             # 国际化目录
skip_render:               # 跳过渲染的文件列表

# 写作设置
new_post_name: :title.md    # 新文章的文件名格式
default_layout: post        # 默认布局
titlecase: false            # 将标题转换为 titlecase
external_link:
  enable: true              # 在新标签页中打开外部链接
  field: site               # 应用于整个站点
  exclude: ''               # 排除的链接字段
filename_case: 0            # 文件名大小写（0: 不变, 1: 小写, 2: 大写）
render_drafts: false        # 渲染草稿
post_asset_folder: true     # 启用文章资源文件夹
marked:
  prependRoot: true         # 将相对链接转换为绝对链接
  postAsset: true           # 允许在文章中嵌套文件
relative_link: false        # 使用相对链接
future: true                # 渲染未来的文章
highlight:
  enable: true              # 启用代码高亮
  line_number: true         # 显示行号
  auto_detect: false        # 自动检测代码语言
  tab_replace: ''           # 替换制表符的字符串
  wrap: true                # 是否包裹代码块
  hljs: false               # 使用 hljs 替代默认高亮引擎
prismjs:
  enable: false             # 启用 Prism.js
  preprocess: true          # 在渲染之前处理代码块
  line_number: true         # 显示行号
  tab_replace: ''           # 替换制表符的字符串
# 首页设置
index_generator:
  path: ''                  # 博客首页的根路径（默认 = ''）
  per_page: 10              # 每页显示的文章数量（0 = 禁用分页）
  order_by: -date           # 文章排序方式（默认按日期降序排列）

# 分类与标签
default_category: uncategorized  # 默认分类
category_map:               # 分类映射
tag_map:                    # 标签映射

# Metadata 元素
## https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
meta_generator: true        # 自动生成 meta 标签

# 日期/时间格式
## Hexo 使用 Moment.js 解析和显示日期
## 你可以根据 http://momentjs.com/docs/#/displaying/format/ 定制日期格式
date_format: YYYY-MM-DD     # 日期格式
time_format: HH:mm:ss       # 时间格式
updated_option: 'mtime'     # 文章更新时间选项（'mtime', 'date', 'empty'）

# 分页
## 将 per_page 设置为 0 以禁用分页
per_page: 10
pagination_dir: page

# 包含/排除文件
## include:/exclude: 选项仅适用于 'source/' 文件夹
include:                    # 包含的文件列表
exclude:                    # 排除的文件列表
ignore:                     # 忽略的文件列表

# 扩展
## 插件: https://hexo.io/plugins/
## 主题: https://hexo.io/themes/
theme: next                  # 使用的主题

# 部署
## 文档: https://hexo.io/docs/one-command-deployment
deploy:
  type: git                  # 部署类型
  repo: git@github.com:iProgramme/MyBlog.git  # 仓库地址
  branch: gh-pages           # 部署的分支

```