# HTML 代码风格

## 基本语法

* 用两个空格来代替制表符（tab）， 这样能保证在所有环境下获得一致展现的方法。
* 嵌套元素应当缩进一次（即两个空格）。

## 统一符号

* 所有标签和属性名称一律小写，如果不这么做可能导致与 Angular 的不兼容。
* 属性值一律使用双引号。

```html
<!-- Bad -->
<h1 CLASS='hello-world'>Hello, world!</h1>
<P>这是一个相当美好的世界！</P>

<!-- Good -->
<h1 class="hello-world">Hello, world!</h1>
<p>这是一个相当美好的世界！</p>
```

不要省略可选的结束标签（closing tag）。
```html
<!-- Bad -->
<ul>
  <li>apple
  <li>banana
</ul>

<!-- Good -->
<ul>
  <li>apple</li>
  <li>banana</li>
</ul>
```
