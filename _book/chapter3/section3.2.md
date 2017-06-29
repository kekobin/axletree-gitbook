# 发布

在发布之前，需要在client下的fis-conf.js中配置发布的CDN域。  
然后使用如下命令发布，默认的发布路径为项目根路径下的pub目录:

```
axletree release prod
```

目录结构形式如下:

```
pub
├─axledemo
│  ├─css
│  │      index_ca07146.css
│  │      widget_a05f55f.css    # 组件样式的合并
│  ├─img
│  │      avatar_29f6668.png
│  │      header_f78d20c.png
│  ├─js
│    │  common_73668dc.js       # js/mod目录文件的合并
│    │  index_5ec2bdb.js
│    │  widget_28853dd.js       # 组件逻辑的合并
│    └─lib
│            mod_2b1d325.js
│
└─axledemoView
    │  index.html
    └─template
        ├─footer
        │      footer.tpl
        ├─header
        │      header.tpl
        └─list
                list.tpl
```

其中axledemo为静态资源，需要发布到上述配置的CDN域中。axledemoView为node UI视图文件，应该复制到server/views下(最好使用独立的发布server，如[axletree-server](https://github.com/kekobin/axletree-server))，然后将该server发布到node服务器上。