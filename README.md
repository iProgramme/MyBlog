## 介绍

### 技术
- hexo搭建
- NexT主题
- algolia站内搜索

访问地址见 http://yubowen2003.top/MyBlog


GitHub博客地址见 https://iprogramme.github.io/MyBlog/


### 开启cnpm 
cd ~/cnpmjs.org
docker-compose up

访问端口7002，发布端口7001

### 开启 verdaccio
pm2 start verdaccio

访问端口4873

-----

创建一个新的博客
hexo new "文章名字"


启动 Nginx 服务
```
sudo nginx
```

检查 Nginx 服务状态
```
sudo systemctl status nginx
```

停止 Nginx 服务
```
sudo nginx -s stop
```

重启 Nginx 服务
```
sudo systemctl restart nginx
```

