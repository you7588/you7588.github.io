---
title: Heroku 部署
date: 2017-09-04 18:23:22
categories: Heroku
description: 常用的Heroku部署步骤
tags: [Heroku, 常用]
---

### 首次
#### 创建Heroku App
``` bash
$ pwd                 #确认目前处于子目录里
$ heroku —version     #查看版本
$ heroku login        #登陆 heroku 账号
$ heroku create       #创建 heroku app
```

#### 修改Gemfile
``` bash
$ atom .              #打开atom
```
具体修改在最后


#### 保存档案
``` bash
$ bundle install
$ git add .
$ git commit -m "xxxx"
```

#### 推上Heroku

``` bash
$ git push heroku master
$ heroku run rake db:migrate
$ heroku open
```

### 往后
#### 直接执行

``` bash
$ git add .
$ git commit -m "xxxx"
$ git push heroku ch08:master    # 最新进度在 分支ch08 或 git push heroku master
$ heroku run rake db:migrate
$ heroku run rake db:seed
$ heroku open
```


### 修改Gemfile 档案

#### 1 迁移sqlite3 (把 sqlite3 粘贴到 `group :development, :test do` 里面。)

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fhajvk74s4j30va0i40vy.jpg)

![](https://ws2.sinaimg.cn/large/006tNbRwgy1fhajviw7vij318g086abt.jpg)

#### 2 加`'pg'`这个gem

![](https://ws1.sinaimg.cn/large/006tNbRwgy1fhajvi7affj30ls03g3yn.jpg)

#### 3 `command + s` 存档。
