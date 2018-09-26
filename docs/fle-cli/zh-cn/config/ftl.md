# ftl项目配置

## 方式一：通过node进行本地调试

在页面的ftl模版中，配置需要的mock数据：

```js
<!-- 开发环境mock数据 -->
window.PG_CONFIG = {
  test: 'This is test data.'
};
```

然后访问node服务的页面。

## 方式二：node配合java进行本地调试

其原理就是通过java解析ftl模版并填充数据，然后页面使用node服务的资源（js、css、图片等）。

首先，在`fle.json`中配置：

```json
{
  ...
  "host": "dev.xxx.com",              # 配置host，共享登录状态
  "port: 5000,
  ...
  "proxy": {
    "/page/1": "http://dev.xxx.com",  # 配置页面代理，将其代理到java页面URL
  },
  ...
  "copyPath": "../template"           # 配置ftl文件的输出目录
```

然后，在`app.json`中指定ftl文件的具体路径：

```json
{
  ...
  "filename": "aaa/bbb.ftl",         # 相对于copyPath的路径
  ...
}
```

最后，我们就可以访问node页面`http://dev.xxx.com:5000/page/1`（该页面已经代理到java中了），支持热更新。
当然我们也可以不使用代理，直接访问java页面，但是由于端口不同，无法实现热更新，更改后需要手动刷新下页面。
