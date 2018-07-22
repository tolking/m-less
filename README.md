# m-less

### 自用的less文件，结合webpack更好的使用

1. index.less  样式入口文件（必须）
- 在项目中引入，或者引入其它less文件
- 还可以直接在index.less引入css文件
```less
@import "animate.css";
```
- 在其中可以定义html的font-size（默认 20px），来使用rem
- 写一些简单的公共样式也是不错的

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
  <p>我想水平垂直居中</p>
</div>
```

5. color.less  整体颜色（建议）
- 里面写整体网站的颜色信息
- 方便管理整体网站的配色
- @c-text 与 @c-line 是必须项，可以改颜色，去掉会报错
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