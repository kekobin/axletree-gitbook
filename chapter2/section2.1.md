# 前端目录规范

axletree底层封装了FIS3，因此整个框架具备了FIS3大部分的功能和其工程构建的优势。

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

在前端开发目录中，需要说明的是:
- index.html等页面文件将会被编译到server的views文件夹下。
- fis-conf.js作为axletree的辅助打包配置，可以扩展基础配置，包括设置正式环境静态资源的cdn域等。(不推荐过多的自主配置，以免影响系统的默认配置).
- widget下组件的tpl将会被编译到server的views/template文件夹下，其静态资源(img、scss、js)将被编译到server下static对应的文件夹下。

## 资源定位
这一块完全应用FIS3强大的资源定位能力，只是axletree默认已经配置好了所有相关资源的定位配置，并且由于开发过程中静态资源需要编译到server端运行，所以跟常规的FIS3定位还是有些区别。

> 另外，当发布到正式环境时，Node UI层并不会涉及到静态资源的发布，因此打包出来的这些静态资源应该发布到独立的CDN等。

例如项目名为axledemo,打包后cdn域为http://www.cdn.com.

### html中定位资源

```
<!--源码：<img title="demo" src="img/demo.png"/>编译后-->
<img title="demo" src="http://www.cdn.com/axletree/img/demo_249de4.png"/>

<!--源码：<link rel="stylesheet" type="text/css" href="css/demo.css">编译后-->
<link rel="stylesheet" type="text/css" href="http://www.cdn.com/axletree/css/demo_2j34dd33.css">

<!--源码：<script type="text/javascript" src="js/demo.js"></script>编译后-->
<script type="text/javascript" src="http://www.cdn.com/axletree/js/demo_23dde32.js"></script>
```

## 模块化开发

axletree默认采用模块化方式开发，所以js/lib/mod.js是必备的。其他的库文件也无需手动引入，直接在逻辑入口index.js中通过FIS3的编译函数__inline() 进来嵌入即可(推荐), 如__inline('lib/jquery.js').  

axletree对于前端组件采用同名依赖模式，例如require('widget/list/list')时,axletree将自动检索该组件的样式文件并引入。与该功能相配合使用的是使用fis3-postpackager-loader插件，其功能是，将所有组件样式合并成widget.css插入到html中的
```
<!--STYLE_PLACEHOLDER-->
```
位置，将所有组件的逻辑合并成widget.js，以及模块化文件合并成common.js插入到html中具有data-loader属性script后的

```
<script type="text/javascript" src="/js/index.js" data-loader></script>
<!--RESOURCEMAP_PLACEHOLDER-->
```
位置.

所有这些繁琐的事都无需手动，axletree将自动完成并插入页面中。生成如下结果:
```
<link rel="stylesheet" type="text/css" href="/css/widget.css" />
```
以及
```
<script type="text/javascript" src="/js/widget.js"></script>
<script type="text/javascript" src="/js/common.js"></script>
```


