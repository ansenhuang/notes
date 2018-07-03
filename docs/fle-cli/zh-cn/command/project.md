# 创建工程

执行命令：

```bash
$ fle init <project>
```

然后根据实际情况选择工程配置，样板工程有：

* react：使用react框架搭建多页面工程
* vue：使用vue框架搭建多页面工程
* app：原生JS搭建多页面工程，也可以自行添加框架
* lib：编译JS库，导出ES6模块（tree-shaking）或者commonjs等
* node：NodeJS项目工程，支持ES6写法

最后生成一个项目工程，其中`fle.json`是整个工程的配置文件。

补充说明：

* 文件引用别名： `@ => src`
