---
title: 全网最全的next主题yml配置文件翻译解析
abbrlink: eca4cdb6
date: 2023-11-30 17:29:11
tags: [next,hexo,配置文件,主题,博客,博客搭建,博客配置]
---

以下文件内容全部是我自己翻译的，原文地址为：[https://iprogramme.github.io/MyBlog/](https://iprogramme.github.io/MyBlog/)

```yml
# ---------------------------------------------------------------
# 主题核心配置设置
# See: https://theme-next.org/docs/theme-settings/
# ---------------------------------------------------------------

# 如果为false，则将“_data/next.yml”中的配置合并到默认配置中（重写）。
# 如果为true，将通过`_data/next.yml`中的选项完全覆盖默认配置(重写)。仅适用于NexT设置。
# 如果为true，则默认NexT `_config.yml`中的所有配置都必须复制到`NexT.yml'中。如果您知道自己在做什么，请使用。
# 如果您想在不编辑默认配置的情况下，通过`NexT.yml`注释NexT `_config.yml'中的一些选项，这将非常有用。
override: false

# 控制台提醒（如果发布了新版本）。
reminder: false

# 允许缓存内容生成。在NexT v6.0.0中引入。
cache:
  enable: true

# 在hexo generate 后删除不必要的文件。
minify: false

# 定义自定义文件路径。
# 在站点目录“source/_data”中创建自定义文件，并在下面取消对所需文件的注释。
custom_file_path:
  #head: source/_data/head.swig
  #header: source/_data/header.swig
  #sidebar: source/_data/sidebar.swig
  #postMeta: source/_data/post-meta.swig
  #postBodyEnd: source/_data/post-body-end.swig
  #footer: source/_data/footer.swig
  #bodyEnd: source/_data/body-end.swig
  #variable: source/_data/variables.styl
  #mixin: source/_data/mixins.styl
  #style: source/_data/styles.styl


# ---------------------------------------------------------------
# 站点信息设置
# See: https://theme-next.org/docs/getting-started/
# ---------------------------------------------------------------

favicon:
  small: /images/favicon-16x16-next.png
  medium: /images/favicon-32x32-next.png
  apple_touch_icon: /images/apple-touch-icon-next.png
  safari_pinned_tab: /images/logo.svg
  #android_manifest: /images/manifest.json
  #ms_browserconfig: /images/browserconfig.xml

# 在页脚中显示多语言切换器
language_switcher: false

footer:
  # 指定网站的设置日期。如果未定义，则使用当前年份
  since: 2018

  # 年份和版权信息之间的图标。
  icon:
    # Icon名称来自 Font Awesome. See: https://fontawesome.com/icons
    name: fa fa-heart
    # 如果要设置图标的动画，请将其设置为true
    animated: true
    # 使用十六进制代码更改图标的颜色。
    color: "#ff0000"

  # 由Hexo和NexT提供动力
  copyright:

  # 由Hexo和NexT提供动力
  powered: false

  # 中国用户的备案 ICP 和公安信息。 See: https://beian.miit.gov.cn, http://www.beian.gov.cn
  beian:
    enable: true
    icp: zheshisha
    # 公安备案的数字部分。
    gongan_id: 123
    # 公安备案的完整编号。
    gongan_num: 456
    # 公安备案的图标。 See: http://www.beian.gov.cn/portal/download
    gongan_icon_url: http://www.beian.gov.cn/portal/download

# 知识共享4.0国际许可。
# See: https://creativecommons.org/share-your-work/licensing-types-examples
# license 的可用值: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero
# 如果您更喜欢 CC 许可证的翻译版本，可以设置 language 值，例如 deed.zh
# CC 许可证提供 39 种语言，您可以在 https://creativecommons.org 找到您需要的特定和正确的缩写。
creative_commons:
  license: by-nc-sa
  sidebar: false
  post: false
  language:


# ---------------------------------------------------------------
# 主题方案配置
# ---------------------------------------------------------------

# Schemes
# scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini

# 黑暗模式
darkmode: false


# ---------------------------------------------------------------
# 菜单设置
# see： 此文章所有翻译来自郭减
# 更多信息：https://github.com/iProgramme/MyBlog
# ---------------------------------------------------------------

# Usage: `Key: /link/ || icon`
# key是菜单项的名称。如果此项目的翻译可用，则将加载翻译后的文本，否则将使用key名称。key名称区分大小写。（指的是比如 about，中文下翻译的为 关于）
# 分隔符“||”之前的值是目标链接，分隔符“||”之后的值是Font Awesome icon的名称。
# 当在子目录中运行站点时（例如，yoursite.com/blog），请从链接值中删除前导斜杠（/archives -> archives）。
# 外部 url 应以 http:// 或 https:// 开头
menu:
  home: / || fa fa-home
  about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  #schedule: /schedule/ || fa fa-calendar
  # sitemap: /sitemap.xml || fa fa-sitemap
  # commonweal: /404/ || fa fa-heartbeat

# Enable / Disable menu icons / item badges.
menu_settings:
  icons: true
  badges: false


# ---------------------------------------------------------------
# 侧边栏设置
# See: https://theme-next.org/docs/theme-settings/sidebar
# ---------------------------------------------------------------

sidebar:
  # 侧边栏位置.
  position: left
  #position: right

  # 手动定义侧边栏宽度。如果有评论，将默认用于:
  # Muse | Mist: 320
  # Pisces | Gemini: 240
  # width: 300

  # 边栏显示（仅适用于Muse|Mist），可用值:
  #  - post    自动展开帖子。 默认值.
  #  - always  自动展开所有页面.
  #  - hide    仅当单击侧边栏切换图标时展开.
  #  - remove  完全删除侧边栏，包括侧边栏切换.
  display: post

  # 以像素为单位，侧边栏的padding.
  padding: 18
  # 边栏与顶部菜单栏的偏移量（以像素为单位）（仅适用于Pisces|Gemini）。
  offset: 12
  # 在窄视图上启用侧边栏 (only for Muse | Mist).
  onmobile: false

# 侧边栏头像
avatar:
  # 替换默认图像并在此处设置url.
  url: #/images/avatar.gif
  # 如果为true，图像将在圆圈中显示.
  rounded: true
  # 如果为true, 鼠标放在图像上时会旋转.
  rotated: true

# Posts / Categories / Tags 放侧边栏.
site_state: true

# 社交链接
# 用法: `Key: permalink || icon`
# Key 是向最终用户显示的链接标签.
#  分隔符“||”之前的值是目标永久链接，分隔符“||”之后的值是 Font Awesome icon的名称。
social:
  GitHub: https://github.com/iProgramme || fab fa-github
  E-Mail: mailto:yubowen2003@gmail.com || fa fa-envelope
  #Weibo: https://weibo.com/yourname || fab fa-weibo
  Google: https://plus.google.com/yourname || fab fa-google
  #Twitter: https://twitter.com/yourname || fab fa-twitter
  #FB Page: https://www.facebook.com/yourname || fab fa-facebook
  #StackOverflow: https://stackoverflow.com/yourname || fab fa-stack-overflow
  #YouTube: https://youtube.com/yourname || fab fa-youtube
  #Instagram: https://instagram.com/yourname || fab fa-instagram
  #Skype: skype:yourname?call|chat || fab fa-skype

social_icons:
  enable: true
  icons_only: false
  transition: false

# 博客滚动
links_settings:
  icon: fa fa-link
  title: Links
  # Available values: block | inline
  layout: block

# links:
#   Title: http://yoursite.com

# 边栏中的目录
# Front-matter variable (unsupport wrap expand_all).
toc:
  enable: true
  # 自动将列表编号添加到 toc.
  number: true
  # 如果为true，则如果标题宽度大于侧边栏宽度，则所有单词都将放在下一行。
  wrap: false
  # 如果为true，则会显示帖子中所有级别的TOC，而不是其中激活的部分.
  expand_all: false
  # 生成的toc的最大航向深度.
  max_depth: 6

# 在侧边栏中打开指定聊天小部件的按钮.
# 首先，你需要启用聊天服务，如果你想激活它的侧边栏按钮。.
chat:
  enable: false
  #service: chatra
  #service: tidio
  icon: fa fa-comment # Icon name in Font Awesome, set false to disable icon.
  text: Chat # Button text, 你可以随意改变他.


# ---------------------------------------------------------------
# 回复设置
# See: https://theme-next.org/docs/theme-settings/posts
# ---------------------------------------------------------------

# 在主页自动提取描述作为前言文本.
excerpt_description: true

# 阅读更多按钮
# 如果为 true, 则在摘录部分显示“阅读更多”按钮.
read_more_btn: true

# 回复设置
post_meta:
  item_text: true
  created_at: true
  updated_at:
    enable: true
    another_day: true
  categories: true

# 文章字数显示设置
# 依赖: https://github.com/theme-next/hexo-symbols-count-time
symbols_count_time:
  separated_meta: true  # 是否换行显示 字数统计 及 阅读时长
  item_text_post: true  # 文章 字数统计 阅读时长 使用图标 还是 文本表示
  item_text_total: true # 博客底部统计 字数统计 阅读时长 使用图标 还是 文本表示
  awl: 4
  wpm: 275
post_wordcount:
  # 文本显示
  item_text: true
  # 文章字数统计
  wordcount: true
  # 阅读时长
  min2read: true
  # 站点总字数统计
  totalcount: false
  # 该post_wordcount的所有设置另起一行显示
  separated_meta: true
  
readingtime: true
# 使用图标而不是符号#来指示帖子底部的标签
tag_icon: false

# 打赏 (捐赠)
# Front-matter variable (unsupport animation).
reward_settings:
  # 如果为true，则默认情况下每篇文章都会显示奖励.
  enable: true
  animation: true
  comment: 原创的技术分享，请我喝杯奶茶吧

reward:
  wechatpay: /images/wechatpay.jpg
  alipay: /images/alipay.jpg
  #paypal: /images/paypal.png
  #bitcoin: /images/bitcoin.png

# 通过Telegram频道、Twitter等订阅.
# 用法: `Key: permalink || icon` (Font Awesome)
follow_me:
  #Twitter: https://twitter.com/username || fab fa-twitter
  #Telegram: https://t.me/channel_name || fab fa-telegram
  #WeChat: /images/wechat_channel.jpg || fab fa-weixin
  #RSS: /atom.xml || fa fa-rss

# 相关热门帖子
# 依赖: https://github.com/tea3/hexo-related-popular-posts
related_posts:
  enable: false
  title: # 自定义标头，保留为空以使用默认标头
  display_in_home: false
  params:
    maxCount: 5
    #PPMixingRate: 0.0
    #isDate: false
    #isImage: false
    #isExcerpt: false

# 闲着没事加点自己的链接防止盗文章咯
# see： https://iprogramme.github.io/MyBlog/
# 帖子设置
# 依赖: https://github.com/hexojs/hexo-deployer-git
post_edit:
  enable: false
  url: https://github.com/user-name/repo-name/tree/branch-name/subdirectory-name # Link for view source
  #url: https://github.com/user-name/repo-name/edit/branch-name/subdirectory-name # Link for fork & edit

# 在页脚中显示上一篇文章和下一篇文章（如果存在）
# 可选值: left | right | false
post_navigation: left


# ---------------------------------------------------------------
# 自定义页面设置
# See: https://theme-next.org/docs/theme-settings/custom-pages
# ---------------------------------------------------------------

# 标记页面的TagCloud设置.
tagcloud:
  # 以下所有值与默认值相同，请自行更改.
  min: 12 # 最小字体大小px
  max: 30 # 最大字体大小px
  start: "#ccc" # 开始颜色 (hex, rgba, hsla or color keywords)
  end: "#111" # 结束颜色 (hex, rgba, hsla or color keywords)
  amount: 200 # 标签数量，如果您有200个以上的标签，请更改它

# 谷歌日历
# 通过日历页面与他人分享您最近的日程安排.
calendar:
  calendar_id: <required> # 您的谷歌帐户电子邮件
  api_key: <required>
  orderBy: startTime
  offsetMax: 24 # Time Range
  offsetMin: 4 # Time Range
  showDeleted: false
  singleEvents: true
  maxResults: 250


# ---------------------------------------------------------------
# 其他主题设置
# ---------------------------------------------------------------

# 设置帖子/页面中的文本对齐方式.
text_align:
  # 可选值: start | end | left | right | center | justify | justify-all | match-parent
  desktop: justify
  mobile: justify

# 减少宽度较窄的设备上的padding / margin.
mobile_layout_economy: false

# Android Chrome 标题面板颜色 ($brand-bg / $headband-bg => $black-deep).
android_chrome_color: "#222"

# 自定义 Logo (不支持 scheme Mist)
custom_logo: #/uploads/custom-logo.jpg

codeblock:
  # 代码高亮主题
  # 可选值: normal | night | night eighties | night blue | night bright | solarized | solarized dark | galactic
  # See: https://github.com/chriskempson/tomorrow-theme
  highlight_theme: night bright
  # 在代码块上添加啊复制按钮
  copy_button:
    enable: true
    # 显示文本复制结果.
    show_result: true
    # 可选值: default | flat | mac
    style: mac

back2top:
  enable: true
  # 在侧边栏显示返回到顶部.
  sidebar: true
  # 在返回顶部按钮上显示页面滚动的百分比.
  scrollpercent: true

# 读取进度条
reading_progress:
  enable: true
  # 可选值: top | bottom
  position: top
  color: "#37c6c0"
  height: 10px

# 书签支持
bookmark:
  enable: false
  # 自定义的书签颜色.
  color: "#222"
  # 如果为 auto, 当关闭页面或者点击书签icon的时候存储阅读进度.
  # 如果为手动 manual, 只有单击书签图标才可保存.
  save: auto

# `Follow me on GitHub` banner 在右上角.
github_banner:
  enable: true
  permalink: https://github.com/iProgramme
  title: Follow me on GitHub


# ---------------------------------------------------------------
# 字体设置
# See: https://theme-next.org/docs/theme-settings/#Fonts-Customization
# 更多信息：https://iprogramme.github.io/MyBlog/posts/af303a63.html
# ---------------------------------------------------------------
# 在谷歌字体库查找字体 (https://www.google.com/fonts)
# 此处设置的所有字体都将具有以下样式:
#   light | light italic | normal | normal italic | bold | bold italic
# 请注意，设置过多的字体会导致网站运行缓慢！
# ---------------------------------------------------------------
# 了避免scheme Pisces / Gemini中标题和侧边栏之间的空格，建议`global` (and `title`)使用Web安全字体:
# Arial | Tahoma | Helvetica | Times New Roman | Courier New | Verdana | Georgia | Palatino | Garamond | Comic Sans MS | Trebuchet MS
# ---------------------------------------------------------------

font:
  enable: false

  # Uri of fonts host, e.g. https://fonts.googleapis.com (Default).
  host:

  # 字体配置:
  # `external: true` will load this font family from `host` above.
  # `family: Times New Roman`. Without any quotes.
  # `size: x.x`. Use `em` as unit. Default: 1 (16px)

  # 用于<body>内部所有元素的全局字体设置.
  global:
    external: true
    family: Lato
    size:

  # 网站标题的字体设置 (.site-title).
  title:
    external: true
    family:
    size:

  # 标题的字体设置 (<h1> to <h6>).
  headings:
    external: true
    family:
    size:

  # 帖子的字体设置 (.post-body).
  posts:
    external: true
    family:

  # 代码和代码块的字体设置.
  codes:
    external: true
    family:


# ---------------------------------------------------------------
# SEO 设置
# ---------------------------------------------------------------

# 禁用移动设备上的百度转换.
disable_baidu_transformation: false

# 如果 true, 网站小标题将添加到索引页.
# 记得在Hexo`_config.yml中设置你的网站小标题 (e.g. subtitle: Subtitle)
index_with_subtitle: true

# 使用Base64加密和解密自动添加外部URL.
exturl: false

# google 网站管理员工具验证.
# See: https://www.google.com/webmasters
google_site_verification:

# Bing 网站管理员工具验证.
# See: https://www.bing.com/webmaster
bing_site_verification:

# Yandex 网站管理员工具验证.
# See: https://webmaster.yandex.ru
yandex_site_verification:

# Baidu 网站管理员工具验证.
# See: https://ziyuan.baidu.com/site
baidu_site_verification:

# 启用baidu推送，使博客自动将url推送给baidu，这对SEO非常有帮助.
baidu_push: false


# ---------------------------------------------------------------
# 第三方插件和服务设置
# See: https://theme-next.org/docs/third-party-services/
# 更多 plugins: https://github.com/theme-next/awesome-next
# 您可能需要在“vendors”中安装依赖项或设置CDN URL
# 下面有两个不同的CDN提供商:
#   - jsDelivr (cdn.jsdelivr.net), works everywhere even in China （任何地方都可以工作，甚至是中国。啥意思啊，中国怎么了啊，我大中国怎么了！！）
#   - CDNJS (cdnjs.cloudflare.com), provided by cloudflare
# ---------------------------------------------------------------

# 数学公式渲染支持
math:
  # 默认值（true）将根据需要加载mathjax/katex脚本.
  # 也就是说，它只呈现那些在`mathjax: true` in Front-matter的页面.
  # 如果设置为 false, 将会加载 mathjax / katex srcipt 到每个页面！！.
  per_page: true

  # hexo-renderer-pandoc (or hexo-renderer-kramed) required for full MathJax support .
  mathjax:
    enable: false
    # See: https://mhchem.github.io/MathJax-mhchem/
    mhchem: false

  # hexo-renderer-markdown-it-plus (or hexo-renderer-markdown-it with markdown-it-katex plugin) required for full Katex support.
  katex:
    enable: false
    # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
    copy_tex: false

# 在您的网站上轻松实现快速Ajax导航.
# Dependencies: https://github.com/theme-next/theme-next-pjax
pjax: false

# FancyBox是一个为图像添加缩放功能的工具，它提供了一种漂亮而优雅的方式.
# 更多信息: https://fancyapps.com/fancybox
fancybox: true

# 用于缩放Medium等图像的JavaScript库.
# 不要同时启用 `fancybox` and `mediumzoom`.
# 更多信息: https://github.com/francoischalifour/medium-zoom
# see： https://iprogramme.github.io/MyBlog/posts/eca4cdb6.html
mediumzoom: false

# 用于懒加载图像的Vanilla JavaScript插件.
# 更多信息: https://github.com/ApoorvSaxena/lozad.js
lazyload: false

# Pangu 支持
# 更多信息: https://github.com/vinta/pangu.js
pangu: false

# Quicklink 支持
# 不要同时启用 `pjax` and `quicklink`.
# 更多信息: https://github.com/GoogleChromeLabs/quicklink
# Front-matter (unsupport home archive).
quicklink:
  enable: false

  # 主页和归档页面可以通过以下主页和归档选项进行控制.
  # 此配置项独立于 `enable`.
  home: false
  archive: false

  # 默认 (true) 将在加载事件触发后初始化Quicklink.
  delay: true
  # 自定义浏览器必须执行预取的时间（以毫秒为单位）.
  timeout: 3000
  # 默认值（true）将启用fetch()或回退到XHR.
  priority: true

  # 为了获得更大的灵活性，您可以添加一些模式（RegExp、Function或Array）来忽略.
  # See: https://github.com/GoogleChromeLabs/quicklink#custom-ignore-patterns
  ignores:


# ---------------------------------------------------------------
# 评论设置
# See: https://theme-next.org/docs/third-party-services/comments
# ---------------------------------------------------------------

# 多评论系统支持
comments:
  # 可选值: tabs | buttons
  style: tabs
  # 选择默认显示的评论系统.
  # 可选值: changyan | disqus | disqusjs | gitalk | livere | valine
  active:
  # 设置“true”表示记住访问者选择的评论系统.
  storage: true
  # 懒加载所有评论系统.
  lazyload: false
  # 改任何导航的文本或订单，以下是一些示例.
  nav:
    #disqus:
    #  text: Load Disqus
    #  order: -1
    #gitalk:
    #  order: -2

# Disqus
disqus:
  enable: false
  shortname:
  count: true
  #post_meta_order: 0

# DisqusJS
# Alternative Disqus - 用 Disqus API 渲染评论模块.
# Demo: https://suka.js.org/DisqusJS/
# 更多信息: https://github.com/SukkaW/DisqusJS
disqusjs:
  enable: false
  # API Endpoint of Disqus API (https://disqus.com/api/).
  # 如果您能够连接到Disqus api，请将api保留为空。否则，您需要一个反向代理.
  # For example:
  # api: https://disqus.skk.moe/disqus/
  api:
  apikey: # 从 https://disqus.com/api/applications/ 注册新应用
  shortname: # See: https://disqus.com/admin/settings/general/

# Changyan
changyan:
  enable: false
  appid:
  appkey:
  #post_meta_order: 0

# Valine
# 更多信息: https://valine.js.org, https://github.com/xCss/Valine, https://guojian2003.blogspot.com/2023/09/github-actionsnpmgithub-packagesgithub.html
valine:
  enable: false
  appid: # Your leancloud application appid
  appkey: # Your leancloud application appkey
  notify: false # Mail notifier
  verify: false # Verification code
  placeholder: Just go go # 评论框 placeholder
  avatar: mm # Gravatar style
  guest_info: nick,mail,link # Custom comment header
  pageSize: 10 # Pagination size
  language: # Language, available values: en, zh-cn
  visitor: false # Article reading statistic
  comment_count: true # 如果 false, 评论数只会在帖子页面展示，不会在主页展示
  recordIP: false # 是否记录评论者 IP
  serverURLs: # 启用自定义域名后，请在此处填写（默认情况下会自动检测到，无需填写）need to fill in)
  #post_meta_order: 0

# LiveRe 评论系统
# You can get your uid from https://livere.com/insight/myCode (General web site)
livere_uid: # <your_uid>

# Gitalk
# 更多信息: https://gitalk.github.io, https://github.com/gitalk/gitalk
gitalk:
  enable: false
  github_id: # GitHub repo owner
  repo: # Repository name to store issues
  client_id: # GitHub Application Client ID
  client_secret: # GitHub Application Client Secret
  admin_user: # GitHub repo owner and collaborators, only these guys can initialize gitHub issues
  distraction_free_mode: true # Facebook-like distraction free mode
  # Gitalk's display language depends on user's browser or system environment
  # 如果你想让每个访问你网站的人都看到统一的语言，你可以设置一个强制语言值
  # 可选值: en | es-ES | fr | ru | zh-CN | zh-TW
  language:


# ---------------------------------------------------------------
# 发布小工具和内容共享服务
# See: https://theme-next.org/docs/third-party-services/post-widgets
# ---------------------------------------------------------------

# 每篇文章的星级支持.
# To get your ID visit https://widgetpack.com
rating:
  enable: false
  id:     # <app_id>
  color:  fc6423

# AddThis Share. See: https://www.addthis.com
# Go to https://www.addthis.com/dashboard to customize your tools.
add_this_id:


# ---------------------------------------------------------------
# 统计和分析
# See: https://theme-next.org/docs/third-party-services/statistics-and-analytics
# ---------------------------------------------------------------

# Google 分析
google_analytics:
  tracking_id: # <app_id>
  # 默认情况下, NexT 将会加载一个额外的 gtag.js script 在你的网站中 site.
  # 如果您只需要页面查看功能，请将以下选项设置为true以获得更好的性能.
  only_pageview: false

# Baidu 分析
baidu_analytics: # <app_id>

# Growingio 分析
growingio_analytics: # <project_id>

# CNZZ 统计
cnzz_siteid:

# 每篇文章展示到访者数量.
# You can visit https://leancloud.cn to get AppID and AppKey.
# AppID and AppKey are recommended to be the same as valine's for counter compatibility.
# 不要同时启用 `valine.visitor` and `leancloud_visitors`.
leancloud_visitors:
  enable: false
  app_id: # <your app id>
  app_key: # <your app key>
  # Required for apps from CN region
  server_url: # <your server url>
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # 如果你不关心leancloud计数器的安全性，只想直接使用它
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: true

# 另一个显示每篇文章访问者数量的工具.
# Visit https://console.firebase.google.com/u/0/ to get apiKey and projectId.
# Visit https://firebase.google.com/docs/firestore/ to get more information about firestore. https://guojian2003.blogspot.com/2023/09/github-actionsreleasegithub.html
firestore:
  enable: false
  collection: articles # Required, a string collection name to access firestore database
  apiKey: # Required
  projectId: # Required

# Show Views / Visitors of the website / page with busuanzi.
# 更多信息: http://ibruce.info/2015/04/04/busuanzi
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: fa fa-user
  total_views: true
  total_views_icon: fa fa-eye
  post_views: true
  post_views_icon: fa fa-eye


# ---------------------------------------------------------------
# 搜索服务
# See: https://theme-next.org/docs/third-party-services/search-services
# ---------------------------------------------------------------

# Algolia Search
# 更多信息: https://www.algolia.com
algolia_search:
  enable: false
  hits:
    per_page: 10
  labels:
    input_placeholder: Search for Posts
    hits_empty: "We didn't find any results for the search: ${query}"
    hits_stats: "${hits} results found in ${time} ms"

# Local Search
# Dependencies: https://github.com/theme-next/hexo-generator-searchdb
local_search:
  enable: true
  # 如果 auto, 通过更改输入触发搜索.
  # 如果手动 manual, 通过回车键或者点击搜索按钮来搜索.
  trigger: auto
  # 显示每篇文章的前n个结果，通过设置为-1显示所有结果.
  top_n_per_article: 1
  # 将html字符串解压缩为可读字符串.
  unescape: false
  # 页面加载时预加载搜索数据.
  preload: false

# Swiftype Search API Key
swiftype_key:


# ---------------------------------------------------------------
# Chat 服务
# See: https://theme-next.org/docs/third-party-services/chat-services
# ---------------------------------------------------------------

# Chatra 支持
# See: https://chatra.io
# Dashboard: https://app.chatra.io/settings/general
chatra:
  enable: false
  async: true
  id: # Visit Dashboard to get your ChatraID
  #embed: # Unfinished experimental feature for developers. See: https://chatra.io/help/api/#injectto

# Tidio 支持
# See: https://www.tidiochat.com
# Dashboard: https://www.tidiochat.com/panel/dashboard
tidio:
  enable: false
  key: # Public Key, get it from dashboard. See: https://www.tidiochat.com/panel/settings/developer


# ---------------------------------------------------------------
# 标签设置
# See: https://theme-next.org/docs/tag-plugins/
# ---------------------------------------------------------------

# Note tag (bs-callout)
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0

# Tabs tag
tabs:
  transition:
    tabs: false
    labels: true

# PDF tag
# NexT将尝试本地加载pdf文件，如果失败，将使用pdf.js.
# 因此，如果您想使用pdf标签并使其可用于所有浏览器，则必须安装pdf.js的依赖项.
# See: https://github.com/theme-next/theme-next-pdf, https://guojian2003.blogspot.com/2023/09/github-actionspackagegithub.html
pdf:
  enable: false
  # Default height
  height: 500px

# Mermaid tag
mermaid:
  enable: false
  # Available themes: default | dark | forest | neutral
  theme: forest


# ---------------------------------------------------------------
# 动画设置
# ---------------------------------------------------------------

# 使用速度设置所有内容的动画.
# 更多信息: http://velocityjs.org
motion:
  enable: true
  async: false
  transition:
    # Transition variants:
    # fadeIn | flipXIn | flipYIn | flipBounceXIn | flipBounceYIn
    # swoopIn | whirlIn | shrinkIn | expandIn
    # bounceIn | bounceUpIn | bounceDownIn | bounceLeftIn | bounceRightIn
    # slideUpIn | slideDownIn | slideLeftIn | slideRightIn
    # slideUpBigIn | slideDownBigIn | slideLeftBigIn | slideRightBigIn
    # perspectiveUpIn | perspectiveDownIn | perspectiveLeftIn | perspectiveRightIn
    post_block: fadeIn
    post_header: slideDownIn
    post_body: slideDownIn
    coll_header: slideLeftIn
    # Only for Pisces | Gemini.
    sidebar: slideUpIn

# 页面加载过程中顶部的进度条.
# Dependencies: https://github.com/theme-next/theme-next-pace
# 更多信息: https://github.com/HubSpot/pace
pace:
  enable: false
  # Themes list:
  # big-counter | bounce | barber-shop | center-atom | center-circle | center-radar | center-simple
  # corner-indicator | fill-left | flat-top | flash | loading-bar | mac-osx | material | minimal
  theme: minimal

# JavaScript 3D library.
# Dependencies: https://github.com/theme-next/theme-next-three
# 这个实测感觉没效果不知道为啥，大家可以自己试试
three:
  enable: false
  three_waves: false
  canvas_lines: false
  canvas_sphere: false
  
# 这个是我自己设置的背景动画特效
# see: https://iprogramme.github.io/MyBlog/posts/af303a63.html
canvas_nest:
  enable: true
  color: '0,0,0'   # RGB颜色值
  opacity: 0.9        # 透明度，取值范围 [0, 1]
  zIndex: -1          # 元素堆叠顺序，负值表示在所有正常元素下
  
# Canvas-ribbon
# Dependencies: https://github.com/theme-next/theme-next-canvas-ribbon
# For more information: https://github.com/zproo/canvas-ribbon
# 这个也是有效的，但我郭减不喜欢哈哈哈哈
canvas_ribbon:
  enable: false
  size: 300 # The width of the ribbon
  alpha: 0.6 # The transparency of the ribbon
  zIndex: -1 # The display level of the ribbon


#! ---------------------------------------------------------------
#! 注意：不要编辑以下设置！
#! 注意：除非你清楚的知道你在做什么！
#! See: https://theme-next.org/docs/advanced-settings
#! See: https://guojian2003.blogspot.com/2023/09/github-actionsnpm.html
#! ---------------------------------------------------------------

# Script Vendors. 为要自定义的Vendors设置CDN地址.
# 请注意，您最好使用与内部版本相同的版本，以避免潜在的问题.
# 当您在网站上启用https时，请记住使用CDN文件的https协议.
vendors:
  # 内部路径前缀.
  _internal: lib

  # Internal version: 3.1.0
  # anime: //cdn.jsdelivr.net/npm/animejs@3.1.0/lib/anime.min.js
  anime:

  # Internal version: 5.13.0
  # fontawesome: //cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@5/css/all.min.css
  # fontawesome: //cdnjs.cloudflare.com/ajax/libs/font-awesome/5.13.0/css/all.min.css
  fontawesome:

  # MathJax
  # mathjax: //cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
  mathjax:

  # KaTeX
  # katex: //cdn.jsdelivr.net/npm/katex@0/dist/katex.min.css
  # katex: //cdnjs.cloudflare.com/ajax/libs/KaTeX/0.11.1/katex.min.css
  # copy_tex_js: //cdn.jsdelivr.net/npm/katex@0/dist/contrib/copy-tex.min.js
  # copy_tex_css: //cdn.jsdelivr.net/npm/katex@0/dist/contrib/copy-tex.min.css
  katex:
  copy_tex_js:
  copy_tex_css:

  # Internal version: 0.2.8
  # pjax: //cdn.jsdelivr.net/gh/theme-next/theme-next-pjax@0/pjax.min.js
  pjax:

  # FancyBox
  # jquery: //cdn.jsdelivr.net/npm/jquery@3/dist/jquery.min.js
  # fancybox: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.js
  # fancybox_css: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.css
  jquery:
  fancybox:
  fancybox_css:

  # Medium-zoom
  # mediumzoom: //cdn.jsdelivr.net/npm/medium-zoom@1/dist/medium-zoom.min.js
  mediumzoom:

  # Lazyload
  # lazyload: //cdn.jsdelivr.net/npm/lozad@1/dist/lozad.min.js
  # lazyload: //cdnjs.cloudflare.com/ajax/libs/lozad.js/1.14.0/lozad.min.js
  lazyload:

  # Pangu
  # pangu: //cdn.jsdelivr.net/npm/pangu@4/dist/browser/pangu.min.js
  # pangu: //cdnjs.cloudflare.com/ajax/libs/pangu/4.0.7/pangu.min.js
  pangu:

  # Quicklink
  # quicklink: //cdn.jsdelivr.net/npm/quicklink@1/dist/quicklink.umd.js
  quicklink:

  # DisqusJS
  # disqusjs_js: //cdn.jsdelivr.net/npm/disqusjs@1/dist/disqus.js
  # disqusjs_css: //cdn.jsdelivr.net/npm/disqusjs@1/dist/disqusjs.css
  disqusjs_js:
  disqusjs_css:

  # Valine
  # valine: //cdn.jsdelivr.net/npm/valine@1/dist/Valine.min.js
  # valine: //cdnjs.cloudflare.com/ajax/libs/valine/1.3.10/Valine.min.js
  valine:

  # Gitalk
  # gitalk_js: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js
  # gitalk_css: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.css
  gitalk_js:
  gitalk_css:

  # Algolia Search
  # algolia_search: //cdn.jsdelivr.net/npm/algoliasearch@4/dist/algoliasearch-lite.umd.js
  # instant_search: //cdn.jsdelivr.net/npm/instantsearch.js@4/dist/instantsearch.production.min.js
  algolia_search:
  instant_search:

  # Mermaid
  # mermaid: //cdn.jsdelivr.net/npm/mermaid@8/dist/mermaid.min.js
  # mermaid: //cdnjs.cloudflare.com/ajax/libs/mermaid/8.4.8/mermaid.min.js
  mermaid:

  # Internal version: 1.2.1
  # velocity: //cdn.jsdelivr.net/npm/velocity-animate@1/velocity.min.js
  # velocity: //cdnjs.cloudflare.com/ajax/libs/velocity/1.2.1/velocity.min.js
  # velocity_ui: //cdn.jsdelivr.net/npm/velocity-animate@1/velocity.ui.min.js
  # velocity_ui: //cdnjs.cloudflare.com/ajax/libs/velocity/1.2.1/velocity.ui.min.js
  velocity:
  velocity_ui:

  # Internal version: 1.0.2
  # pace: //cdn.jsdelivr.net/npm/pace-js@1/pace.min.js
  # pace: //cdnjs.cloudflare.com/ajax/libs/pace/1.0.2/pace.min.js
  # pace_css: //cdn.jsdelivr.net/npm/pace-js@1/themes/blue/pace-theme-minimal.css
  # pace_css: //cdnjs.cloudflare.com/ajax/libs/pace/1.0.2/themes/blue/pace-theme-minimal.min.css
  pace:
  pace_css:

  # Internal version: 1.0.0
  # three: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/three.min.js
  # three_waves: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/three-waves.min.js
  # canvas_lines: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/canvas_lines.min.js
  # canvas_sphere: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/canvas_sphere.min.js
  three:
  three_waves:
  canvas_lines:
  canvas_sphere:

  # Internal version: 1.0.0
  # canvas_ribbon: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-ribbon@1/canvas-ribbon.js
  canvas_ribbon:

# Assets
css: css
js: js
images: images

```