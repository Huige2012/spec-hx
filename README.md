# hx前端编码规范 

1. [文件目录](#catolog)
2. 基本规则
3. html
4. css
5. javascript
6. 文件目录


## 前言

此规范主要实现的目标：代码一致性和最佳实践。通过代码风格的一致性，降低维护代码的成本以及改善多人协作的效率。同时遵守最佳实践，确保页面性能得到最佳优化和高效的代码。

> 黄金定律: 不管有多少人共同参与同一项目，一定要确保每一行代码都像是同一个人编写的。

<a name="catalog"></a>
## 文件目录
```
src/
   main/
      java/
      resources/
      webapp/
         images/
            platform/
               （pc-图片）
            wapapp/
               （wx-图片）
         scripts/
            platform/
               （pc-js）
            wapapp/
               （wx-js）
         styles/
            palotform/
               （pc-css）
            wapapp/
               （wx-css）
         WEB-INF/
            lib/
            page/
               platform/  
                  (pc-jsp)
               webapp/
                  （wx-jsp）
                  
```

页面文件都统一在`src/main/webapp/` 里面

目录如下：
- `images`             --图片
- `scripts`            --js文件
- `styles`             --样式文件
- `WEB-INF/page`       --页面文件

目前的项目有 `platform` 与 `wapapp`,对应 `pc端` 与 `微信端`

如：合康诊所PC端的页面就在`page/platform`里面，对应的js文件在`scripts/platform`里面，css与图片亦是如此。


- 文件命名统一用小写字母与中划线的组合，如 `people-detail.js` `hk-base.css`
- 插件统一放在 `scripts/tool` 里面 



## 基本规则：

### 结构、样式、行为分离

确保文档和模板只包含 HTML 结构，样式都放到样式表里，行为都放到脚本里。


### 缩进

统一两个空格缩进，不要使用 Tab 或者 Tab、空格混搭！

### 一律使用小写字母

一致使用小写字母

``` html
<!-- bad -->
<TITLE>合康医生</TITLE>

<!-- good -->
<title>合康医生</title>
```
### 注释

- HTML


``` html 
<!-- 模块注释 -->
<div class="article-list">
...
</div>

<!--
@name: 区块注释
@description: Style of top bar drop down menu.
@author: Ashu(Aaaaaashu@gmail.com)
-->
<div class="drop-down-menu">
...
</div>
```

- CSS （组件块和子组件块以及声明块之间使用一空行分隔，子组件块之间三空行分隔；）

``` css

/* ==========================================================================
   组件块
 ============================================================================ */

/* 子组件块
 ============================================================================ */
.selector {
  padding: 15px;
  margin-bottom: 15px;
}



/* 子组件块
 ============================================================================ */
.selector-secondary {
  display: block; /* 注释*/
}

.selector-three {
  display: span;
}
``` 

- javascript

``` javascript
// 单行注释
var val = 0;

/**
 * 多行注释（函数描述）
 *
 * @param {string} p1 参数1的说明
 * @param {string} p2 参数2的说明，比较长
 *     那就换行了.
 * @param {number=} p3 参数3的说明（可选）
 * @return {Object} 返回值描述
 */
function foo(p1, p2, p3) {
    var p3 = p3 || 10;
    return {
        p1: p1,
        p2: p2,
        p3: p3
    };
}

/**
 * @文件注释 用于告诉不熟悉这段代码的读者这个文件中包含哪些东西。 
 * 应该提供文件的大体内容, 它的作者, 依赖关系和兼容性信息
 * @author user@meizu.com (Firstname Lastname)
 * Copyright 2015 Meizu Inc. All Rights Reserved.
 */
 
```

## HTML

### class 与 id
- class 应以功能或内容命名，不以表现形式命名；
- class 与 id 单词字母小写，多个单词组成时，采用中划线-分隔；
- 使用唯一的 id 作为 Javascript hook, 同时避免创建无样式信息的 class，命名格式用'j-hook'形式

``` html
<!-- bad -->
<div class="j-hook left contentWrapper"></div>

<!-- good -->
<div class="sidebar content-wrapper"  id="j-hook"></div>
```

### 属性顺序

HTML 属性应该按照特定的顺序出现以保证易读性。
- class  
- id
- name
- data-xxx
- src, for, type, href
- title, alt
- aria-xxx, role

``` html
<a class="..." id="..." data-modal="toggle" href="###"></a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

### 引号

属性的定义，统一使用双引号。

``` 
<!-- bat -->
<span class=text  id='j-hook'>Google</span>

<!-- good -->
<span class="text"  id="j-hook">Google</span>
```

###布尔值属性

HTML5 规范中 disabled、checked、selected 等属性不用设置值。

``` html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

## CSS

###规范说明
- 用两个空格来代替制表符（tab） -- 这是唯一能保证在所有环境下获得一致展现的方法。
- 避免选择器嵌套层级过多，不能多于`3`级；
- 为选择器分组时，将单独的选择器单独放在一行。
- 为了代码的易读性，在每个声明块的左花括号前添加一个空格。
- 声明块的右花括号应当单独成行。
- 每条声明语句的 : 后应该插入一个空格。
- 为了获得更准确的错误报告，每条声明都应该独占一行。
- 所有声明语句都应当以分号结尾。最后一条声明语句后面的分号是可选的，但是，如果省略这个分号，你的代码可能更易出错.
- 不要在 rgb()、rgba()、hsl()、hsla() 或 rect() - - 值的内部的逗号后面插入空格。这样利于从多个属性值（既加逗号也加空格）中区分多个颜色值（只加逗号，不加空格）。
- 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）。
- 十六进制值应该全部小写，例如，#fff。在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。
- 使用简写形式的十六进制值，例如，用 #fff 代替 #ffffff。
- 为选择器中的属性添加双引号，例如，input[type="text"]。只有在某些情况下是可选的，但是，为了代码的一致性，建议都加上双引号。
- 避免为 0 值指定单位，例如，用 margin: 0; 代替 margin: 0px;。

``` css
/* bad */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* good */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

### 声明顺序

相关的属性声明应当归为一组，并按照下面的顺序排列：

1. Positioning
2. Box model
3. Typographic
4. Visual

``` css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

### 不要使用 @import

与 <link> 相比，@import 要慢很多，不光增加额外的请求数，还会导致不可预料的问题。

替代办法：

- 使用多个 元素；
- 通过 Sass 或 Less 类似的 CSS 预处理器将多个 CSS 文件编译为一个文件；
- 其他 CSS 文件合并工具；

### 媒体查询（Media query）的位置

将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。

``` css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (max-width: 768px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```

### 带前缀的属性

当使用特定厂商的带有前缀的属性时，通过缩进的方式，让每个属性的值在垂直方向对齐，这样便于多行编辑。
``` css
/* Prefixed properties */
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

## JavaScript

### 注释

#### 原则

> 如无必有，勿增注释； 如有必要，必须详细！

#### 单行注释

必须独占一行。// 后跟一个空格，缩进与下一行被注释说明的代码一致。

#### 多行注释

避免使用 /*...*/ 这样的多行注释。有多行注释内容时，使用多个单行注释。

#### 函数/方法注释

- 函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识。；
- 参数和返回值注释必须包含类型信息和说明；
- 当函数是内部函数，外部不可访问时，可以使用 @inner 标识；
``` javascript
/**
 * 函数描述
 *
 * @param {string} p1 参数1的说明
 * @param {string} p2 参数2的说明，比较长
 *     那就换行了.
 * @param {number=} p3 参数3的说明（可选）
 * @return {Object} 返回值描述
 */
function foo(p1, p2, p3) {
    var p3 = p3 || 10;
    return {
        p1: p1,
        p2: p2,
        p3: p3
    };
}
```

#### 文件注释

文件注释用于告诉不熟悉这段代码的读者这个文件中包含哪些东西。 应该提供文件的大体内容, 它的作者, 依赖关系和兼容性信息。如下:
``` javascript
/**
 * @fileoverview Description of file, its uses and information
 * about its dependencies.
 * @author user@meizu.com (Firstname Lastname)
 * Copyright 2009 Meizu Inc. All Rights Reserved.
 */
```
### 命名

**变量**, 使用 Camel 命名法。
``` javascript
var loadingModules = {};
```

***私有属性、变量和方法*** 以下划线 _ 开头。
``` javascript
var _privateMethod = {};
```

**常量**, 使用全部字母大写，单词间下划线分隔的命名方式。

``` javascript
var HTML_ENTITY = {};
```

**函数**, 使用 Camel 命名法。
函数的参数, 使用 Camel 命名法。

``` javascript
function stringFormat(source) {}

function hear(theBells) {}
```


- **类**, 使用 **Pascal** 命名法
- 类的 方法 / 属性, 使用 Camel 命名法

``` javascript
function TextNode(value, engine) {
    this.value = value;
    this.engine = engine;
}

TextNode.prototype.clone = function () {
    return this;
};
```

- **枚举变量** 使用 **Pascal** 命名法。
- **枚举的属性**， 使用全部字母大写，单词间下划线分隔的命名方式。
var TargetState = {
    READING: 1,
    READED: 2,
    APPLIED: 3,
    READY: 4
};



### 参考
- [编码规范](http://codeguide.bootcss.com/#css-syntax)
- [前端开发规范手册](http://zhibimo.com/read/Ashu/front-end-style-guide/index.html)





