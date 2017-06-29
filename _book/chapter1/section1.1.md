# 命令行

axletree整个框架只有两个命令，就完成了项目的创建、编译和发布整个流程。

##init
axletree init project初始化一个axletree项目，包括前端的基础构建及样例文件，和服务端的基础框架代码。

##release
axletree release命令功能比较强大，能够对前端代码进行编译和发布，以及监听和热更新等。   

因为 axletree 实际上是扩展自 fis3 ，因此也继承了fis3 release的所有参数，但需要指出的是:axletree项目中，开发阶段不要使用--dest指定发布目录，因为该阶段前端的目录文件会自动更新到服务端相关的目录中，一旦更改，将不能正常运行。

- 监听文件修改，对修改文件进行增量编译并发布

```
axletree release debug --watch
```
- 监听文件修改，并自动刷新页面

>自动刷新页面需要下载 livereload 插件

```
axletree release debug --live
```

上述命令也可以缩写并组合(推荐):

```
axletree release debug -wL
```
