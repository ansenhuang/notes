# Eslint

当前使用的是规范是[JavaScript Standard Style](https://github.com/standard/standard/blob/master/docs/RULES-zhcn.md)。

而对于React和Vue工程，分别使用的规范是：

* plugin:react/recommended
* plugin:vue/essential

系统自定义规范：

```js
module.exports = {
  rules: {
    "no-var": 1,
    "no-alert": 1,
    "prefer-promise-reject-errors": 0,
    "no-unused-vars": config.dev ? 1 : 2,
    "no-debugger": config.dev ? 1 : 2,
    "no-console": [config.dev ? 1 : 2, {
      "allow": ["info", "warn", "error"]
    }]
  }
}
```

本地开发时，使用alert、debugger、console.log会发出警告，但不会阻止编译，方便进行调试；但是在生产环境时，会抛出错误，中断编译，需要开发者将这些代码移除，再重新编译。

当然，如果必须要使用到这些，可以通过注释来屏蔽掉eslint检测，示例：

```js
/* disable-eslint no-console */
console.log(999)
```

但是我们不建议这么做，还是希望可以遵循一下代码规范。
