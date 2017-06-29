# 内置功能

axletree server采用的是ejs模版引擎，当模版存在前后端复用需求时，内置的功能函数Util提供了复用模版的函数Template，具体使用如下:

```
# Util.Template(项目名称, 模版路径)
<script type="text/template" id="listTpl">
  <%- Util.Template('axledemo', 'list/list.tpl') %>
</script>
```

> 注:此处的list.tpl位于client/widget/list/下，因为最终它将编译到server/views/template目录下，因此只需传递组件目录名+具体模版名.