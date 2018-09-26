# 项目配置

项目工程根路径下，有一个`fle.json`的配置文件，用于设置工程级别的配置，具体如下：

```json
{
  "boilerplate": "app",        # 项目样板名称，项目初始化时自动定义
  "business": "test",          # 业务名称，用于上传时固定URL前缀，便于缓存命中
  "eslint": true,              # 开启eslint代码检测，能够自动格式化部分不合法的代码
  "remUnit": 50,               # 应用REM适配时，css单位转换，50rpx=1rem
  "browsers": [                # 浏览器兼容性配置
    "last 4 versions",
    "ie >= 9",
    "IOS >= 7",
    "Android >= 4"
  ],
  "externals": {},             # webpack选项，对指定的文件不进行构建编译，转而使用全局变量，该配置作用于页面构建
  "libExternals": {},          # 同上，该配置用于模块编译，即lib样板项目

  # 开发环境配置 #

  "notify": true,              # 编译出错时，启用系统通知
  "host": "0.0.0.0",           # 自定义本地域名，示例中的域名可以支持IP访问
  "port": 5000,                # 本地开发服务器的端口，若端口被占用则自动更换
  "proxy": {},                 # 本地开发代理配置，方便接口调试
  "historyApiFallback": true,  # 使用前端路由（history），指定路径到对应的页面路径中
  "open": false,               # 开启服务器时是否自动打开浏览器
  "https": false,              # 是否启用https服务器

  # 生产环境配置 #

  "splitVendor": true,         # 分割代码块，默认分割npm模块
  "vendors": {},               # 自定义需要分割的代码块，每一个键将会分割出对应的代码块，值是一个字符串类型的正则表达式
  "splitCommon": true,         # 分割公共模块，即common目录下的代码，使用次数在3次及以上且大小超过30KB才会分割成独立的文件
  "inlineManifest": true,      # 将编译运行时的代码内联到页面模版中，利于缓存
  "publicPath": "/",           # 指定编译后的文件路径引用前缀

  # 新增 #
  "copyPath": "../template"    # 提供java模版（ftl）的自定义配置，可以在开发环境或生产环境将ftl文件打包到指定的目录，配合java服务进行本地测试
}
```

补充说明：

* [proxy配置文档](https://webpack.js.org/configuration/dev-server/#devserver-proxy)
* [historyApiFallback配置文档](https://webpack.js.org/configuration/dev-server/#devserver-historyapifallback)

示例:

```json
{
  "proxy": {
    "/test": {
      "target": "http://xxx.com",
      "changeOrigin": true,
      "secure": false
    },
    "/api/*": "http://localhost:9999"
  }
}
```
