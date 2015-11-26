## JavaScript 代码风格

### 基本设置

* UTF-8 编码
* 2 空格缩进

### 严格模式

建议打开严格模式，但不要依赖严格模式中语言特性的变化（仅当需要支持 IE8、IE9 时）

```js
'use strict';
```

### 引号

使用单引号，这样可以跟 HTML 的双引号更好的一起工作。

```js
/* Bad */
var foo = "bar";

/* Good */
var foo = 'bar';
```

### 分号

在语句（Statement）的结尾加分号

```js
/* Bad */
var foo = function() {
  ...
} // 没有分号

/* Good */
var foo = function() {
  ...
}; // 这里有分号
```
