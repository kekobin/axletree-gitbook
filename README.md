# 入门指引

## 简介

Axletree是一个专注于 Node.js UI 中间层的应用框架。它基于 express 开发，使用简单、灵活的ejs模版，并且封装了fis3用于前端工程的构建与开发。它将前端工程与Server端分离，使前端开发人员只需要关注前端领域的开发，降低项目开发的复杂度。

## 安装Axletree

```
npm install -g axletree
```

## 创建project

axletree project包含应用的前端与服务端构建，在开发阶段，能够将前端的变化自动更新到服务端运行，使开发阶段也能做到前后端分离。


```
axletree init project
# prompt: Enter your project name:  (axledemo)
```
## 开发调试

假如我们创建的工程名为axledemo，那么在该目录下将同时生成client和server目录，对应前后端代码的构建。

### 安装依赖

首先我们需要为 server 安装执行必须的依赖

```
# 进入server 目录
cd server
npm install
```
### 部署server

```
# windows下
npm run debug-win
# linux下
npm run debug
```

axletree server 的默认端口是 8085,此时如果我们访问 [http://127.0.0.1:8085](http://127.0.0.1:8085) 由于我们并未部署前端应用，我们只会得到一个 404 页面。因此下一步我们就需要部署前端应用。

### 部署client

由于部署 server 后会一直占用控制台，因此我们需要另外开启一个控制台去执行这一步。

```
# 进入client目录
cd client
axletree release debug
```
>注:开发阶段必须以debug调试模式启动，否则将不能正常部署.


此时我们访问 [http://localhost:8085/axledemo/index](http://localhost:8085/axledemo/index) 就会看到正常的页面了。

此外，如果我们在上面的命令中添加上--watch或者-w参数，那么在client目录下做的任何改动，都将自动更新到server端。然后刷新页面，也能够看到改动后的效果。

```
# 进入client目录
cd client
axletree release debug --watch
```

### 监听node(可选)

> 该步骤不是必须的，只是使用监听更有利于我们的开发。

正常情况下，对于log信息或者http请求等，nodejs会使用内置调试器将它们输出到控制台，但对于习惯使用浏览器javascript调试器的前端开发者来说，这种方式不免有点繁琐和复杂。

为此，axletree引入[node-inspector](https://github.com/node-inspector/node-inspector) 来做相似的处理。

另外开启一个控制台： 

```
# 进入server目录
npm run watcher
```

然后，访问 [http://127.0.0.1:8086/debug?port=5858](http://127.0.0.1:8086/debug?port=5858) 即可打开一个类似javascript调试器的页面来对node层进行监听。

之后，在ejs中使用console打印的任何log，或者node层发出的任何http接口请求都会在上述监听页面时时反馈出来。

### 入门demo
可下载案例demo快速入门[axletree-demo](https://github.com/kekobin/axletree-demo/tree/master).