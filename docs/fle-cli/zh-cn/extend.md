# 扩展配置

假如系统默认的配置还不能满足需求的话，可以自定义一些扩展配置。

添加webpack扩展文件，系统会检索并合并到默认配置中：

* webpack.dev.config.js
* webpack.build.config.js
* webpack.lib.config.js

添加自定义babel处理和eslint规则：

* .babelrc
* .eslintrc

补充说明：

* 以上文件均置于工程根目录才会生效
