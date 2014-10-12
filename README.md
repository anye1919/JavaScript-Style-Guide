JavaScript 编码规范
===================

##js 文件命名

文件名应使用小写字符，用中划线 `-` 分隔单词，用点号 `.`连接版本号，如：`app-core-1.0.js`。

##js 文件引用

为了加快页面载入速度，尽量避免在 HTML 文件中直接编写 JavaScript 代码，因为这样会大大增加 HTML 文件的大小，
应在 `body` 标签最底下引入 `<script src="filename.js"></script>` 标签，`script` 标签的 `type` 属性是非必要的。

##变量方法命名

通常的命名形式：variableNamesLikeThis，methodNamesLikeThis，ClassNamesLikeThis，CONSTANTS_NAMES_LIKE_THIS。

- 文件或类中的 *私有* 属性，变量和方法名应该以下划线 `_` 开头；
- 方法的可选参数以 `opt_` 开头；
- getter 和 setter 方法命名成 `getFoo()`、`setFoo()` ，布尔类型的 getter 用 `isFoo()` 也可以；
- 为全局代码使用命名空间；

```JavaScript
var app = {};

app.init = function() {
  // do something...
};
```

##变量声明

- 声明变量必须加上 `var` 关键字，这样可以有效避免因局部变量和全局变量同名而产生的错误；
- 函数体中，多个局部变量集中在函数体的顶部声明，避免分散；
- 尽量减少声明全局变量；
- 避免使用 `new` 关键字声明数组或对象；

```JavaScript
/* Bad */
var arr = new Array;
var obj = new Object;

/* Good */
var arr = [];
var obj = {};
```

##括号

不要滥用括号，只在必要的时候使用它。  
对于一元操作符(`delete`, `typeof`, `void`)，或是在某些关键词(`return`, `throw`, `case`, `new`)之后，不要使用括号。

```JavaScript
/* Bad */
return (x == 'something' ? x : '');

/* Good */
return x == 'something' ? x : '';
```

##大括号

分号会被隐式插入到代码中，为了减少编译错误，务必在同一行插入大括号。

```JavaScript
/* Bad */
if (x) 
{
  // do something...
}

/* Good */
if (x) {
  // do something...
}
```

##分号

总是使用分号结束一句语句。

```JavaScript
/* Bad */
var a = 1
var b = 2

/* Good */
var a = 1;
var b = 2;
```
**函数表达式** 必须用分号结束，如果你不这么做，有时会出现意想不到的错误。

```JavaScript
/* Bad */
var myMethod = function() {
  // do something...
}    
(function() {
  // 一个匿名函数，在这里会被错误解析当作 myMethod 的参数调用导致报错
})();

/* Good */
var myMethod = function() {
  // do something...
};  
```

##空行

使用空行来划分一组逻辑上相关联的代码片段。

```JavaScript
doSomethingTo(x);
doSomethingElseTo(x);
andThen(x);

nowDoSomethingWith(y);

andNowWith(z);
```

##空格

- 数值操作符 `+`、`-`、`*`、`%` 两边留空；
- 赋值操作符 `==` 两边留一空格；
- for 循环条件中，分号后留一空格；
- 变量声明语句，数组值，对象值及函数参数值中的逗号后留一空格；
- 逗号和冒号后一定要跟空格；
- 函数名和左括号之间不要出现空格；

##缩进

为了保持代码在所有设备上显示一致，建议用两个空格代替 tab 键来缩进代码。

##数组和对象的初始化

如果初始值不是很长，就保持写在单行上。

```JavaScript
var arr = [1, 2, 3];  // No space after [ or before ]
var obj = {a: 1, b: 2, c: 3};  // No space after { or before }
```

初始值占用多行时，缩进2个空格。

```JavaScript
var inset = {
  top: 10,
  right: 20,
  bottom: 15,
  left: 12
};
```

比较长的标识符或者数值，不要为了让代码好看些而手工对齐。

```JavaScript
/* Bad */
var obj = {
  a          : 0,
  b          : 1,
  lengthyName: 2
};

/* Good */
var obj = {
  a: 0,
  b: 1,
  lengthyName: 2
};
```














##JavaScript 小技巧

###布尔表达式

下面的布尔表达式都返回 false
- null
- undefined
- '' 空字符串
- 0 数字0

而下面的都返回 true
- '0' 字符串0
- [] 空数组
- {} 空对象

```JavaScript
/* Bad */
if (x != null) {
	// do something...
}

/* Good */
if (x) {
	// do something...
}
```

###三元操作符 (?:)

```JavaScript
/* Bad */
if (val != 0) {
  return foo();
} else {
  return bar();
}

/* Good */
return val ? foo() : bar();
```

###&& 和 ||

```JavaScript
/* Bad */
if (node) {
  if (node.kids) {
    foo(node.kids[index]);
  }
}

/* Good */
if (node && node.kids) {
  foo(node.kids[index]);
}
```

```JavaScript
/* Bad */
function foo(opt_win) {
  var win;
  if (opt_win) {
    win = opt_win;
  } else {
    win = window;
  }
  // do something...
}

/* Good */
function foo(opt_win) {
  var win = opt_win || window;
  // do something...
}
```

###使用 join() 来拼接字符串

```JavaScript
/* Bad */
function listHtml(items) {
  var html = '<div class="foo">';
  for (var i = 0; i < items.length; ++i) {
    html += itemHtml(items[i]);
  }
  html += '</div>';
  return html;
}

/* Good */
function listHtml(items) {
  var html = [];
  for (var i = 0; i < items.length; ++i) {
    html[i] = itemHtml(items[i]);
  }
  return '<div class="foo">' + html.join('') + '</div>';
}
```

>由于赋值操作快于数组的 push()，所以尽量使用赋值操作。








##参考文档

- [Google JavaScript 规范](https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
- [浅谈 JavaScript 编程语言的编码规范](http://www.ibm.com/developerworks/cn/web/1008_wangdd_jscodingrule/)

