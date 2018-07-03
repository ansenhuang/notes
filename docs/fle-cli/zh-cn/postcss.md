# PostCSS

系统内置了多种postcss插件，提供css-modules功能（为每个样式名打上唯一标识），用于解决命名冲突和嵌套过深的问题。

css-modules作用于以`.module.css`结尾的文件，示例如下：

```css
.test {
  background-color: white;

  &-red {
    background-color: red;
  }
}
```

```js
import $style from './style.module.css'

console.log($style)
// {
//   test: 'xxx_test_xxx',
//   testRed: 'xxx_test-red_xxx'
// }
```

其中，键为我们定义的样式名，它的值为实际编译后的样式名，通过这样的方法，能够保证我们的样式名是唯一的，且处于顶层，无需嵌套。

对于Vue项目，我们可以这样来使用css-modules：

```vue
<style module>
.test {
  background-color: white;

  &-red {
    background-color: red;
  }
}
</style>
```

系统内置PostCSS插件一览：

* [postcss-import](https://www.npmjs.com/package/postcss-import)：支持css中通过`@import`引入
* [postcss-mixins](https://www.npmjs.com/package/postcss-mixins)：支持定义mixin函数
* [postcss-advanced-variables](https://www.npmjs.com/package/postcss-advanced-variables)：支持SASS中变量定义、条件判断和循环语句的写法
* [postcss-color-function](https://www.npmjs.com/package/postcss-color-function)：支持CSS颜色方法的使用
* [postcss-nested](https://www.npmjs.com/package/postcss-nested)：支持样式嵌套
* [postcss-extend](https://www.npmjs.com/package/postcss-extend)：支持样式扩展定义`@extend`
* [postcss-calc](https://www.npmjs.com/package/postcss-calc)：支持css中四则运算
* [postcss-plugin-px2rem](https://www.npmjs.com/package/postcss-plugin-px2rem)：将css单位进行转换
* [autoprefixer](https://www.npmjs.com/package/autoprefixer)：根据浏览器列表自动追加样式前缀

补充说明：

* fle中对`px`单位不会进行转换，会将`rpx`转换为`rem`，换算比率根据fle.json中的`remUnit`进行计算，默认：50rpx=1rem
