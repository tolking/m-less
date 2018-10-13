# m-less

[所有参数介绍](https://ououe.com/less)

```html
<div class="btn">btn</div>
```
#### less 内容
```less
.btn {
  .m(1rem);
  .btn(5rem, 2rem, 0.5rem, @c-blue);
  .box>.shadow;
  .font(1rem, @c-white);
}
```

## 简介
- 自用的less文件
- 包含常用属性简写、常用的 mixins、常用的 flex 类名、颜色及字体定义、清除浏览器默认样式
- 默认只对少数几个属性进行了浏览器前缀处理，使用 Autoprefixer 处理浏览器前缀兼容或者手动引入 -old 文件（查看下面说明）
[所有参数介绍](https://ououe.com/less)

## 目录结构
```
+- less
  +- alias-old.less 属性简写，浏览器前缀兼容
  +- alias.less 属性简写（默认）
  +- base.less 清除浏览器默认样式
  +- flex-old.less flex 类名，浏览器前缀兼容
  +- flex.less flex 类名（默认）
  +- mixins.less 输出 mixins 文件
  +- mixitem.less 常用属性值简写
  +- styles.less 输出文件
  +- svg.less 整理的简单 svg 图片（未来可能有较大变动）
  +- variable.less 变量文件
```

## 组件开发（以vue为例）
1. 在项目 main.js 中引入 styles.less
```js
import "./less/styles.less";
```

2. 在需要使用 mixins 的单文件引入 mixins.less
```html vue
<style lang="less" scoped>
/* 注意相对路径 */
@import url(../less/mixins);

/* 开始使用 */
</style>
```

## 静态页面开发
### 需要在本地服务器环境下进行

1. 在 html 的 header 里面引用 less 及相关配置
```html
<header>
  <link rel="stylesheet/less" type="text/css" href="./less/styles.less">
  <script>
    less = {
      env: "development",
      async: false,
      fileAsync: false,
      poll: 1000,
      functions: {},
      dumpLineNumbers: "comments",
      relativeUrls: false,
      rootpath: "/"
    };
  </script>
  <script src="//cdnjs.cloudflare.com/ajax/libs/less.js/2.5.3/less.min.js"></script>
</header>
```

2. 生产时将 less 编译为 css
- node 使用 lessc styles.less styles.css 编译 less 为 css
- 屏蔽上面开发代码，引入 styles.css

## 手动引入 -old
1. 将 mixins.less 里面的 @import "alias"; 改为 @import "alias-old";
2. 将 styles.less 里面的 @import "flex"; 改为 @import "flex-old";