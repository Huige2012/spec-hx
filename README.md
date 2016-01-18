# hx前端编码规范 

1. 基本规则
2. html
3. css
4. javascript

[TOC] 

## 前言
此规范主要实现的目标：代码一致性和最佳实践。通过代码风格的一致性，降低维护代码的成本以及改善多人协作的效率。同时遵守最佳实践，确保页面性能得到最佳优化和高效的代码。
> **黄金定律: 不管有多少人共同参与同一项目，一定要确保每一行代码都像是同一个人编写的。**


## 基本规则：
### 结构、样式、行为分离
尽量确保文档和模板只包含 HTML 结构，样式都放到样式表里，行为都放到脚本里。
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
