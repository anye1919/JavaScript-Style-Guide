JavaScript 编码规范
===================

##JavaScript 文件引用

为了加快页面载入速度，尽量避免在 HTML 文件中直接编写 JavaScript 代码，因为这样会大大增加 HTML 文件的大小，
应在 `body` 标签最底下引入 `<script src="filename.js"></script>` 标签，`script` 标签的 `type` 属性是非必要的。

##变量

- 声明变量必须加上 `var` 关键字，这样可以有效避免因局部变量和全局变量同名而产生的错误；
- 尽量减少全局变量的使用；
- 常量的命名如：NAMES_LIKE_THIS；

##分号

- 总是使用分号结束一句语句；

```JavaScript
/* Bad */
var a = 1
var b = 2

/* Good */
var a = 1;
var b = 2;
```
如果你不这么做，有时会出现意想不到的错误。
```JavaScript
/* Bad */
var a = 1
var b = 2

/* Good */
var a = 1;
var b = 2;
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
















##参考文档

- [Google JavaScript 规范](https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
- [浅谈 JavaScript 编程语言的编码规范](http://www.ibm.com/developerworks/cn/web/1008_wangdd_jscodingrule/)

