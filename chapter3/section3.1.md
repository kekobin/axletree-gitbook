# 模版应用说明

## 基本使用

axletree中间层采用的是ejs模版，所以其用法比较简单:

```
<div id="container">
	<%- include 'widget/header/header.tpl'%>
</div>
```

或者
```
<div id="container">
	<%- include('widget/header/header.tpl', {'title':'hello world'}) %>
</div>
```

## 模版复用

由于ejs模版语法跟underscore的基本一致，所以复用使用的模版引擎推荐用underscore:

```
	__inline('lib/underscore')
```

引入underscore后，在js逻辑里面即可如下复用相同的模版了，如这里复用的header.tpl：

```
	var tpl = __inline('../widget/header/header.tpl');
	var compiled = _.template(tpl);
	var html = compiled({title: 'hello reuse'});
	$('#container').html(html)
```