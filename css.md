# CSS 和 Sass (SCSS) 代码风格

## 基本语法

* UTF-8 编码
* 用两个空格来代替制表符（tab）， 这样能保证在所有环境下获得一致展现。
* 删除行尾的空白符。

## 代码组织

* 以组件为单位组织代码段。
* 制定一致的注释规范。
* 使用一致的空白符将代码分隔成块，这样利于扫描较大的文档。
* 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动。

```css
/*
 * Component section heading
 */
 
.element { ... }
 
 
/*
 * Component section heading
 *
 * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
 */
 
.element { ... }
 
/* Contextual sub-component or modifer */
.element-heading { ... }
```

## 空白与格式

大括号与选择器之间留一空格，属性名的冒号后留一个空格，注释内外前后留空。

```css
/* 我是注释 */
div { /* 我是注释 */ }

span {
  color: red; /* 我是注释 */
}
```

规则之间始终有一个空行（双换行符）分隔。

```css
html {
  background: #fff;
}

body {
  margin: auto;
  width: 50%;
}
```

## 选择器和声明分离

每个选择器和属性声明总是使用新的一行，使报错可以精确到具体的规则上，便于排错。

```css
/* Bad */
a:focus, a:active {
  position: relative; top: 1px;
}

/* Good */
h1,
h2,
h3 {
  font-weight: normal;
  line-height: 1.2;
}
```
在只有一条样式时允许和选择器写到同一行。

```css
span { color: red; }
```

每条样式声明后面都加上那个分号，最后一条声明语句后面的分号是可选的，但是，如果省略这个分号，你的代码可能更易出错。

```css
/* Bad */
span {
  color: red;
  font-size: 12px
}

/* Good */
span {
  color: red;
  font-size: 12px;
}
```

## 0 和 单位

省略 0 值后面的单位。不要在 0 值后面使用单位，除非有值。

```css
/* Bad */
.main {
  padding-bottom: 0px;
  margin: 0em;
}

/* Good */
.main {
  padding-bottom: 0;
  margin: 0;
}
```

## 十六进制表示法

* 在可能的情况下，使用3个字符的十六进制表示法。
* 十六进制值应该全部小写，在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。

```css
/* Bad */
span { color: #FF33AA; }

/* Good */
span { color: #f3a; }
```

## 引号

* 属性选择器或属性值用双引号（""），而不是单引号（''）括起来。
* 为了代码的一致性，建议都加上双引号。
* URL值（url()）不要使用引号。

```css
/* Bad */
html {
  font-family: 'open sans', arial, sans-serif;
}

body:after {
  content: 'pause';
}

div {
  background-image: url('../img/sprite.png');
}

/* Good */
html {
  font-family: "open sans", arial, sans-serif;
}

body:after {
  content: "pause";
}

div {
  background-image: url(../img/sprite.png);
}
```

对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，box-shadow）。

```css
.block {
  box-shadow: 0 0 0 rgba(#000, 0.1),
              1px 1px 0 rgba(#000, 0.2),
              2px 2px 0 rgba(#000, 0.3),
              3px 3px 0 rgba(#000, 0.4),
              4px 4px 0 rgba(#000, 0.5);
}
```

不要在 rgb()、rgba()、hsl()、hsla() 或 rect() 值的内部的逗号后面插入空格。这样利于从多个属性值（既加逗号也加空格）中区分多个颜色值（只加逗号，不加空格）。

```css
.selector {
  background-color: rgba(0,0,0,.5);
}
```
对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）。

```css
.selector {
  background-color: rgba(0,0,0,.5);
}
```

## ID 和 Class（类） 名的分隔符

* 类名中的字母一律小写。
* 使用连字符（中划线）分隔ID和Class（类）名中的单词。为了增强理解性，在选择器中不要使用除了连字符（中划线）以外的任何字符（包括没有）来连接单词和缩写。

```css
/* Bad */
.demoimage {}
.errorStatus {}
.error_status {}

/* Good */
#video-id {}
.ads-sample {}
```

## class 命名

* class 名称中只能出现小写字符和破折号（dashe）（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，.btn 和 .btn-danger）。
* 避免过度任意的简写。.btn 代表 button，但是 .s 不能表达任何意思。
* class 名称应当尽可能短，并且意义明确。
* 使用有意义的名称。使用有组织的或目的明确的名称，不要使用表现形式（presentational）的名称。
* 基于最近的父 class 或基本（base） class 作为新 class 的前缀。
* 使用 .js-* class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。

```css
/* Bad example */
.t { ... }
.red { ... }
.header { ... }

/* Good example */
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

## 合理的避免使用ID

一般情况下 ID 不应该被应用于样式，ID 的样式不能被复用并且每个页面中你只能使用一次ID。

```css
/* Bad */
#content .title {
  font-size: 2em;
}

/* Good */
.content .title {
  font-size: 2em;
}
```

权重太高，不易维护，一个只包含一个 ID 选择器权重高于包含1000个class(类)名的选择器。

```css
/* 这个选择器权重高于下面的选择器 */
#content .title {
  color: red;
}

/* than this selector! */
html body div.content.news-content .title.content-title.important {
  color: blue;
}
```

## 不要使用 @import

与 <link> 标签相比，@import 指令要慢很多，不光增加了额外的请求次数，还会导致不可预料的问题，各种坑不解释。

```css
/* Bad */
@import url("more.css");

/* Good */
<link rel="stylesheet" href="core.css" />
```

## 带前缀的属性

当使用特定厂商的带有前缀的属性时，通过缩进的方式，让每个属性的值在垂直方向对齐，这样便于多行编辑。

```css
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

## 简写形式的属性声明

在需要显示地设置所有值的情况下，应当尽量限制使用简写形式的属性声明。常见的滥用简写属性声明的情况如下：

* padding
* margin
* font
* background
* border
* border-radius

```css
/* Bad example */
.element {
  margin: 0 0 10px;
  background: red;
  background: url("image.jpg");
  border-radius: 3px 3px 0 0;
}

/* Good example */
.element {
  margin-bottom: 10px;
  background-color: red;
  background-image: url("image.jpg");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```

## 选择器

* 对于通用元素使用 class ，这样利于渲染性能的优化。
* 对于经常出现的组件，避免使用属性选择器（例如，[class^="..."]）。浏览器的性能会受到这些因素的影响。
* 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3 。
* 只有在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。

```css
/* Bad example */
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }

/* Good example */
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```

## 选择器中避免标签名

当构建选择器时应该使用清晰， 准确和有语义的class(类)名，不要使用标签选择器，这样会更容易维护。

如果你只使用具有实际意义的class(类)名，并且不使用元素选择器，那么当你改变你的html标记，则不用改动你的CSS。

```css
/* Bad */
div.content > header.content-header > h2.title {
  font-size: 2em;
}

/* Good */
.content > .content-header > .title {
  font-size: 2em;
}
```

## 选择器嵌套 (SCSS)

在Sass中你可以嵌套选择器，这可以使代码变得更清洁和可读。嵌套所有的选择器，但尽量避免嵌套没有任何内容的选择器。

如果你需要指定一些子元素的样式属性，而父元素不需要指定样式属性，可以使用常规的CSS选择器链，这将防止您的脚本看起来过于复杂。

```css
/* Bad */
.content {
  display: block;
}
   
.content > .news-article > .title {
  font-size: 1.2em;
}

/* Bad */
.content {
  display: block;

  > .news-article {
    > .title {
      font-size: 1.2em;
    }
  }
}

/* Good */
.content {
  display: block;
   
  > .news-article > .title {
    font-size: 1.2em;
  }
}
```

## 嵌套中引入 空行 (SCSS)

嵌套选择器和CSS属性之间空一行。

```css
/* Bad */
.content {
  display: block;
  > .news-article {
    background-color: #eee;
    > .title {
      font-size: 1.2em;
    }
    > .article-footnote {
      font-size: 0.8em;
    }
  }
}

/* Good */
.content {
  display: block;

  > .news-article {
    background-color: #eee;

    > .title {
      font-size: 1.2em;
    }

    > .article-footnote {
      font-size: 0.8em;
    }
  }
}
```

## 上下文媒体查询(SCSS)

在Sass中，当你嵌套你的选择器时也可以使用上下文媒体查询，你可以在任何给定的嵌套层次中使用媒体查询，由此生成的CSS将被转换，这样的媒体查询将包裹选择器的形式呈现。

```css
/* Bad */
.content-page {
  font-size: 1.2rem;
   
  > .main {
    background-color: whitesmoke;

    > .latest-news {
      padding: 1rem;

      > .news-article {
        padding: 1rem;

        > .title {
          font-size: 2rem;
        }
      }
    }

    > .content {
      margin-top: 2rem;
      padding: 1rem;
    }
  }

  > .page-footer {
    margin-top: 2rem;
    font-size: 1rem;
  }
}

@media screen and (min-width: 641px) {
  .content-page {
    font-size: 1rem;

    > .main > .latest-news > .news-article > .title {
      font-size: 3rem;
    }

    > .page-footer {
      font-size: 0.8rem;
    }
  }
}

/* Good */
.content-page {
  font-size: 1.2rem;

  @media screen and (min-width: 641px) {
    font-size: 1rem;
  }

  > .main {
    background-color: whitesmoke;

    > .latest-news {
      padding: 1rem;

      > .news-article {
        padding: 1rem;

        > .title {
          font-size: 2rem;

          @media screen and (min-width: 641px) {
            font-size: 3rem;
          }
        }
      }
    }

    > .content {
      margin-top: 2rem;
      padding: 1rem;
    }
  }

  > .page-footer {
    margin-top: 2rem;
    font-size: 1rem;

    @media screen and (min-width: 641px) {
      font-size: 0.8rem;
    }
  }
}
```

## 嵌套顺序和父级选择器(SCSS)

当使用Sass的嵌套功能的时候，要有一个明确的嵌套顺序，以下内容是一个SCSS块应具有的顺序。

1. 当前选择器的样式属性
2. 父级选择器的伪类选择器 (:first-letter, :hover, :active etc)
3. 伪类元素 (:before and :after)
4. 父级选择器的声明样式 (.selected, .active, .enlarged etc.)
5. 用Sass的上下文媒体查询
6. 子选择器作为最后的部分

```css
.product-teaser {
  // 1. Style attributes
  display: inline-block;
  padding: 1rem;
  background-color: whitesmoke;
  color: grey;

  // 2. Pseudo selectors with parent selector
  &:hover {
    color: black;
  }

  // 3. Pseudo elements with parent selector
  &:before {
    content: "";
    display: block;
    border-top: 1px solid grey;
  }

  &:after {
    content: "";
    display: block;
    border-top: 1px solid grey;
  }

  // 4. State classes with parent selector
  &.active {
    background-color: pink;
    color: red;

    // 4.2. Pseuso selector in state class selector
    &:hover {
      color: darkred;
    }
  }

  // 5. Contextual media queries
  @media screen and (max-width: 640px) {
    display: block;
    font-size: 2em;
  }

  // 6. Sub selectors
  > .content > .title {
    font-size: 1.2em;

    // 6.5. Contextual media queries in sub selector
    @media screen and (max-width: 640px) {
      letter-spacing: 0.2em;
      text-transform: uppercase;
    }
  }
}
```

## 声明顺序

为了保证更好的可读性和可扫描重要，相关的属性声明应当归为一组，并按照下面的顺序排列：

* Positioning
* Box model
* Typographic
* Visual

由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。

其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面。

下表中的顺序参考自 [Recess](http://twitter.github.com/recess)。

```css
position
top
right
bottom
left
z-index
display
float
width
height
max-width
max-height
min-width
min-height
padding
padding-top
padding-right
padding-bottom
padding-left
margin
margin-top
margin-right
margin-bottom
margin-left
margin-collapse
margin-top-collapse
margin-right-collapse
margin-bottom-collapse
margin-left-collapse
overflow
overflow-x
overflow-y
clip
clear
font
font-family
font-size
font-smoothing
osx-font-smoothing
font-style
font-weight
hyphens
src
line-height
letter-spacing
word-spacing
color
text-align
text-decoration
text-indent
text-overflow
text-rendering
text-size-adjust
text-shadow
text-transform
word-break
word-wrap
white-space
vertical-align
list-style
list-style-type
list-style-position
list-style-image
pointer-events
cursor
background
background-attachment
background-color
background-image
background-position
background-repeat
background-size
border
border-collapse
border-top
border-right
border-bottom
border-left
border-color
border-image
border-top-color
border-right-color
border-bottom-color
border-left-color
border-spacing
border-style
border-top-style
border-right-style
border-bottom-style
border-left-style
border-width
border-top-width
border-right-width
border-bottom-width
border-left-width
border-radius
border-top-right-radius
border-bottom-right-radius
border-bottom-left-radius
border-top-left-radius
border-radius-topright
border-radius-bottomright
border-radius-bottomleft
border-radius-topleft
content
quotes
outline
outline-offset
opacity
filter
visibility
size
zoom
transform
box-align
box-flex
box-orient
box-pack
box-shadow
box-sizing
table-layout
animation
animation-delay
animation-duration
animation-iteration-count
animation-name
animation-play-state
animation-timing-function
animation-fill-mode
transition
transition-delay
transition-duration
transition-property
transition-timing-function
background-clip
backface-visibility
resize
appearance
user-select
interpolation-mode
direction
marks
page
set-link-source
unicode-bidi
speak
```
