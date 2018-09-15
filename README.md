# m-less

[所有参数介绍](https://less.ououe.com)  // 编辑、整理中 wait

## 自用的less文件
```html
<div class="btn">btn</div>
```
```less
.btn {
  .m(1rem);
  .btn(5rem, 2rem, 0.5rem, @c-blue);
  .box>.shadow;
  .font(1rem, @c-white);
}
```
#### 效果如下
<style>
.btn {
  margin: 1rem;
  position: relative;
  overflow: hidden;
  width: 5rem;
  height: 2rem;
  border-radius: 0.5rem;
  background-color: #0074D9;
  text-align: center;
  line-height: 2rem;
  cursor: pointer;
  -webkit-user-select: none;
  user-select: none;
  transition-property: all;
  transition-duration: 1s;
  transition-delay: 0s;
  box-shadow: 0 1px 6px rgba(17, 17, 17, 0.3);
  font-size: 1rem;
  color: #FFFFFF;
}
.btn:after {
  content: "";
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
  display: block;
  width: 5rem;
  height: 2rem;
  background: transparent 11% radial-gradient(circle, #ffffff 10%, transparent 11%);
  background-repeat: no-repeat no-repeat;
  background-position: 50% 50%;
  opacity: 0;
  transform: scale(10, 10);
  pointer-events: none;
  transition-property: all;
  transition-duration: 1s;
  transition-delay: 0s;
}
.btn:hover {
  background-color: #0066c0;
  transition-property: all;
  transition-duration: 1s;
  transition-delay: 0s;
}
.btn:active:after {
  opacity: 0.4;
  transform: scale(0, 0);
  transition-property: all;
  transition-duration: 0s;
  transition-delay: 0s;
}
</style>
<div class="btn">btn</div>

#### 编译后 css
```css
.btn {
  margin: 1rem;
  position: relative;
  overflow: hidden;
  width: 5rem;
  height: 2rem;
  border-radius: 0.5rem;
  background-color: #0074D9;
  text-align: center;
  line-height: 2rem;
  cursor: pointer;
  -webkit-user-select: none;
  user-select: none;
  transition-property: all;
  transition-duration: 1s;
  transition-delay: 0s;
  box-shadow: 0 1px 6px rgba(17, 17, 17, 0.3);
  font-size: 1rem;
  color: #FFFFFF;
}
.btn:after {
  content: "";
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
  display: block;
  width: 5rem;
  height: 2rem;
  background: transparent 11% radial-gradient(circle, #ffffff 10%, transparent 11%);
  background-repeat: no-repeat no-repeat;
  background-position: 50% 50%;
  opacity: 0;
  transform: scale(10, 10);
  pointer-events: none;
  transition-property: all;
  transition-duration: 1s;
  transition-delay: 0s;
}
.btn:hover {
  background-color: #0066c0;
  transition-property: all;
  transition-duration: 1s;
  transition-delay: 0s;
}
.btn:active:after {
  opacity: 0.4;
  transform: scale(0, 0);
  transition-property: all;
  transition-duration: 0s;
  transition-delay: 0s;
}
```

## 简介
### 结构包含 常用属性简写、常用的 mixins、常用的 flex 类名、颜色及字体定义、清除浏览器默认样式
### 默认只对少数几个属性进行了前缀处理，结合 postcss Autoprefixer 更好的处理前缀兼容
[所有参数介绍](https://less.ououe.com)  // 编辑、整理中 wait

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