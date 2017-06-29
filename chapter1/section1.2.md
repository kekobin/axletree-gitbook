# 目录结构

axletree project会构建出client和server目录，其中，client是前端工程目录，包含整个前端的基础框架和样例文件，server是node层基于express的项目目录。

## client目录

```
client               # 前端代码 
│  apiConf.js        # 项目配置，包括路由、接口等
│  fis-conf.js       # FIS3编译配置
│  index.html   
├─img           
├─js            
│  │  index.js       # 逻辑入口
│  ├─lib             # 基础库(mod.js, jquery.js等)
│  │      mod.js     # 轻量级的模块加载器，类似requirejs
│  └─mod             # 模块化文件
│          app.js    # 模块化文件入口
├─sass          
└─widget             # 前端组件
    ├─footer
    ├─header
    └─list
```

## server目录

```
server
│  app.js           # 服务端入口
│  favicon.ico
│  package.json
├─config            # 配置文件，client/apiConf.js将编译到该目录
├─static            # 静态文件，client/静态资源将编译到该目录
└─views             # 视图文件，client/页面将编译到该目录
        error.html
        index.html
```