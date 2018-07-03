# 文件上传

开发者可以手动上传文件，在第一次上传前需要配置一下密钥信息（之后会缓存下来），执行以下命令设置密钥：

```bash
$ fle upload --init
```

然后根据提示输入信息，使用的是网易云NOS服务（[如何设置](https://www.163yun.com/help/documents/15677635979624448)），若没有密钥可以在这里[申请](https://www.163yun.com/product/nos)。

上传时将图片进行压缩优化（只处理png、jpg、jpeg格式的图片）：

```bash
$ fle upload --min
```

指定上传后文件链接的唯一标识，常用于设置文件发布的版本号，若没有指定则动态生成：

```bash
$ fle upload --unique [name]

# 示例
$ fle upload --unique react-16.0.0
```

注意事项：

* 暂不支持`.ico`图片上传，该类型会导致上传出错
