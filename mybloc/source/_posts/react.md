---
title: react
date: 2017-10-24 20:41:08
tags:
---

# 环境搭建

![](https://ws3.sinaimg.cn/large/006tNbRwgy1fktkzrl145j30rc0gqn3t.jpg)



-  ES6/NPM课前准备
   -  React新版本变化
   -  ES6基础语法
   -  使用Codepen免配置在线开发React
   -  Npm的安装配置说明（换源及cnpm）
   -  使用create-react-app本地开发React
-  React组件开发
   -  JSX入门
   -  组件类型
   -  组件数据props&state
   -  组件生命周期
   -  表单及事件处理
-  Redux数据处理
   -  理解状态管理
   -  Actions/actionCreator
   -  Reducers
   -  Store
   -  Middleware
   -  React-redux
-  React-router路由配置
   -  前端路由
   -  React-router新版本介绍（dom/native/common)
   -  Router/Route
   -  Link/NavLink
   -  match/withRouter
-  在JS中编写CSS样式
   -  什么是CSS in JS
   -  为什么要使用CSS in JS
   -  Webpack的使用及配置
   -  CSS Modules
   -  Sass
   -  PostCSS
   -  Radium
-  TodoList项目实战
   -  React应用设计思路
   -  组建开发（react）
   -  数据流处理（redux）
   -  路由开发(react-router)
   -  样式编写
   -  实战项目总结
-  React的优势
   -  相较于其他框架生态圈最完整成熟
   -  适用于开发大中型应用，便于团队协作
   -  很多知名大厂都在使用
   -  发展前景广阔，Web/原生App/VR/物联网
-  前置知识
   -  JavaScript基础（变量/对象/函数）
   -  ES6基础
   -  熟悉HTML
   -  基本掌握CSS



## 常见ES6语法

### 引入`import`

```javascript
//旧
 var React = require('react');
 var ReactDOM = require('react-dom');

//新
import React from 'react';
import ReactDOM from 'react-dom';
import hello, { hi } from './modules';
```



### 导出`export`

```javascript
export const hi = "hi"
export default function hello(){
  return 'hello'
}
```


### JSX声明 `const`

```javascript
//旧
var myDivElment = <div className="foo" />;
//新
const element = <h1>Hello, world!</h1>;
```

### 声明组件 `class`
![](https://ws3.sinaimg.cn/large/006tNbRwgy1fktl0zmnppj30vw0ecn53.jpg)


### `class`构造函数`super`关键字
![](https://ws1.sinaimg.cn/large/006tNbRwgy1fktl1mdrptj30hr0dpjvq.jpg)


### `this`绑定 `arrow functions`
![](https://ws4.sinaimg.cn/large/006tNbRwgy1fktmab4fwbj30my0dvwjt.jpg)

## npm的安装配置说明

-  Node.js的安装
-  ~~npm更换国内原~~
-  ~~cnpm安装~~
-  使用npm安装react
-  ~~yarn~~

```bash
$ npm --version
$ npm i -g npm
$ mkdir learn_react
$ cd learn_react
$ npm init -y                           # 初始化npm
$ npm install react react-dom --save    # 使用npm安装react
```



## React开发环境配置

-  ~~使用Codepen线上开发设置~~
-  ~~直接使用CDN~~
-  安装使用create-react-app命令行工具

### [Create a New App](https://reactjs.org/docs/installation.html#creating-a-new-application)

```bash
# 使用npm进行包安装
npm install -g create-react-app

# 通过命令行工具新建项目
create-react-app my-app

# 切入项目工作目录
cd my-app

# 测试运行
npm start
```

# React组件开发解析
