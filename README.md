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
除了颜色外，其它一致使用小写字母
``` html
<!-- bad -->
<TITLE>合康医生</TITLE>

<!-- good -->
<title>合康医生</title>
```
``` css
head{color:#DBDBDB};
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
```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```
 


