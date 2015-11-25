# HTML 代码风格

## 基本语法

* 用两个空格来代替制表符（tab）， 这样能保证在所有环境下获得一致展现。
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

不省略可选的自结束标签末尾斜杠，会影响到外部标记语言的解析。

```html
<svg width="200" height="200">
  <!-- 如果此处 rect 末尾没有斜杠会产生嵌套关系，使 circle 无法显示 -->
  <rect width="200" height="200" fill="#000" />
  <circle cx="100" cy="100" r="100" fill="#fff" />
</svg>
```

建议自结束标签包含属性时在结束的斜杆前面加空格。

```html
<input type="text" />
<hr/>
```

布尔型属性可以在声明时不赋值。

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

## 结构相关

编写 HTML 代码时，尽量避免多余的父元素。

```html
<!-- Bad -->
<span class="avatar">
  <img src="...">
</span>

<!-- Good -->
<img class="avatar" src="...">
```

严格遵守标签嵌套规则，禁止让标签出现在不正确的地方。

```html
<!-- Bad -->
<dl>
  <dt>...</dt>
  <ul>
    <li>...</li>
  </ul>
</dl>

<!-- Good -->
<dl>
  <dt>...</dt>
  <dd>
    <ul>
      <li>...</li>
    </ul>
  </dd>
</dl>
```

根据目的来合理使用HTML，这点对于HTML5而言尤为重要。

```html
<div>1. list 1</div>
<div>2. list 2</div>
<div>3. list 3</div>
```

## 引入 CSS 和 JavaScript 文件

根据 HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 type 属性，因为 text/css 和 text/javascript 分别是它们的默认值。

```html
<!-- External CSS -->
<link rel="stylesheet" href="filename.css">

<!-- In-document CSS -->
<style>
/* ... */
</style>

<!-- JavaScript -->
<script src="filename.js"></script>
```

## HTML5 doctype

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。

```html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```

## 语言属性

强烈建议为 html 根元素指定 lang 属性，从而为文档设置正确的语言。这将有助于语音合成工具确定其所应该采用的发音，有助于翻译工具确定其翻译时所应遵守的规则等等。

更加标准的 lang 属性写法 [http://zhi.hu/XyIa](http://zhi.hu/XyIa)

```html
<html lang="zh-cmn-Hans">
  <!-- ... -->
</html>
```

## 字符编码

通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（一般采用 UTF-8 编码）。

```html
<meta charset="UTF-8">
```

## 优先使用 IE 最新版本和 Chrome

IE 支持通过特定的 <meta> 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

360 使用Google Chrome Frame

```html
<meta name="renderer" content="webkit">
```

所有页面必须有 `<title>`，并尽可能地在不同页面使用不同的标题。

```html
<title>Page title</title>
```

## 属性顺序

HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。

* class
* id, name
* data-*
* src, for, type, href
* title, alt
* aria-*, role

class 用于标识高度可复用组件，因此应该排在首位。id 用于标识具体组件，应当谨慎使用（例如，页面内的书签），因此排在第二位。

```html
<a class="..." id="..." data-modal="toggle" href="#">
  Example
</a>

<input class="form-control" type="text" />

<img src="..." alt="..." />
```

## 尾随空格

尾随空格是不必要的，容易搞复杂diff文件。

```html
<!-- Bad -->
<p>What?_</p>

<!-- Good -->
<p>Yes please.</p>
```

## 为多媒体提供备选内容

* 给图片添加 alt 属性。
* 给无文字超连接添加 title 属性。
* 给可视听的替换型元素内添加描述。

```html
<img src="..." alt="这是一个美女">
<a href="..." title="这是一个链接"></a>
<audio>一段奇妙的音效</audio>
<canvas>一个奇妙的效果</canvas>
<iframe src="http://fitgrace.com">这是网站首页</iframe>
```

<a> 必须有 href 属性，如果用不到可以置为 href="JavaScript:"，href 不是可选属性，只是浏览器能解析而已。

```html
<!-- Bad -->
<a id="btn">修改密码</a>

<!-- Good -->
<a id="btn" href="javascripts:;">修改密码</a>
```

不使用 Level 0 的事件绑定，Level 0 的事件绑定是非规范的，而且容易发生冲突。

```html
<!-- Bad -->
<button id="btn" onclick="onBtnClick()">Add</button>

// jQuery 方案
$("#btn").click(function() {
  // ...
});
```
不要使用 `input（<input type="button"> 、 <input type="submit">）`来代替 button，给这类 input 只设置 height 属性的话，在 safari 和 chrome 下并不会出现意料中的样式。

```html
<!-- Bad -->
<input type="button" />
<input type="submit" />

<!-- Good -->
<button>这是一个按钮</button>
```

## 注释

根据需要解释代码，团队开发这个非常重要，尽管很多时候大家不愿意遵守，但确实非常重要！！
