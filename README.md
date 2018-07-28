# m-less

## 自用的less文件，结合webpack更好的使用
## 组件开发

1. 在项目 main.js 中引入 styles.less
```js
import "./less/styles.less";
```

2. 在需要使用 mixins 的地方引入 mixins.less
```css
@import "./less/mixins";
```

## 静态页面开发
### 需要在本地服务器环境下进行

1. 在 html 的 header 里面引用 less 及相关配置
```html
<header>
  <link rel="stylesheet/less" type="text/css" href="./less/styles.less" />
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
+ node 使用 lessc styles.less styles.css 编译 less 为 css
+ 屏蔽上面开发代码，引入 styles.css

## 简介

1. styles.less  样式入口文件（必须）
- 在项目中引入，或者引入其它less文件

2. mixins.less  Mixin入口文件（必须）
[具体的参数详解](https://ououe.com) 搭建中。。。。
- 里面整合了一些常用的样式混合
- 在需要使用的地方引用
```css
@import url("./less/mixins");

.test {
  .box>.radius(50%, 5rem);
}

// 编译后
.test {
  width: 5rem;
  height: 5rem;
  border-radius: 50%;
}
```

3. base.less  去除浏览器的默认样式（建议）
- 去除浏览器的默认样式，减小浏览器之间的差距

4. flex.less  弹性盒子样式（可选）
[具体的参数详解](https://ououe.com) 搭建中。。。。
- 收录一些我常用的弹性盒子样式
- flex仅支持 ie11 及以上版本浏览器，注意你的项目是否允许你使用
- 直接在需要的 class 里面加类名就行了
```html
<div class="flex-cc">
  <p>center center</p>
</div>
```

5. color.less  整体颜色（建议）
- 方便管理整体网站的配色
- 里面写整体网站的颜色信息
- 提供一些默认颜色
- 部分颜色是必须项，可以改颜色，去掉会报错
```css
@import url("./less/mixins");

.test {
  .font>.weight(800, 1rem, @c-text, @f-yahei);
}

// 编译后
.test {
  font-size: 1rem;
  color: #666;
  font-family: MicrosoftYaHei;
  font-weight: 800;
}
```

6. font.less  整体文字（可选）
- 方便管理网站整体的文字样式