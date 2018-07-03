# 页面配置

页面目录中，有一个`app.json`的配置文件，用于设置页面级别的配置，具体如下：

```json
{
  "title": "example",                   # 页面标题
  "keyswords": "",                      # 页面关键词（SEO）
  "description": "",                    # 页面描述（SEO）
  "icon": "/favicon.ico",               # 页面图标
  "template": "src/home/index.html",    # 页面模版，路径相对于工程根路径，其中以"/"开头的表示系统模版
  "filename": "html/home.html",         # 自定义编译后的模版文件名称，路径相对于dist
  "prejs": [],                          # 添加js链接在head中
  "js": [],                             # 添加js链接在body末尾
  "css": [],                            # 添加css链接在head中
  "entry": "index.js",                  # 自定义入口文件，默认"index.js"
  "minify": true,                       # 是否需要压缩模版文件
  "compiled": true                      # 是否需要编译该页面，若为false则构建时不会编译该页面
}
```

补充说明：

* 除以上配置项外，`html-webpack-plugin`的其它选项也都支持，[查看文档](https://github.com/jantimon/html-webpack-plugin#options)
* 还可以添加自定义选项，在模版中通过`htmlWebpackPlugin.options.xxx`来取值
