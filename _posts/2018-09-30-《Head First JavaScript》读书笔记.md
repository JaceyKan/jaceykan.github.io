---
layout: post
title: 《Head First JavaScript》读书笔记
subtitle: 
date: 2018-09-30
author: JaceyKan
header-img: img/post-bg-2015.jpg
catalog: true
tags: 
 - ReadingNotes
---


# 《Head First JavaScript》读书笔记
---

# Chapter10 函数

### 函数声明:
```javascript
function quack(num) {
  for (var i = 0; i < num; i++) {
    console.log("Quack!");
  }
}
quack(3);
```

### 函数表达式:
```javascript
var fly = function(num) {
  for (var i = 0; i < num; i++) {
    console.log("Flying!");
  }
};
fly(3);
```

### 函数声明 VS 函数表达式
1. 浏览器总是首先扫描代码，在其中查找函数声明。  
函数声明不返回指向函数的引用；   而是创建一个与函数同名的变量， 并将指向函数的引用赋给它
2. 找到函数声明时，浏览器创建相应的函数，并将得到的函数引用赋给与函数同名的变量
3. 处理所有的函数声明后，浏览器回到代码开头，开始按从头到尾的顺序执行代码。函数表达式随其他代码一起被处理    
函数表达式返回一个引用， 该引用指向函数表达式创建的函数。


结果为一个值的任何东西都是表达式  
函数表达式的结果是一个函数引用

函数声明是一条语句。
它包含一条隐藏的赋值语句，这条语句将函数引用赋给一个变量。

函数表达式不自动将函数引用赋给任何变量，你必须显式地这样做。

### 作为一等公民的函数的特征
* 将函数赋给变量
* 将函数传递给函数
* 从函数返回函数

# Chapter11 匿名函数、作用域和闭包

### 匿名（ anonymous）
指的是没有名称的函数。
通过使用匿名函数，可让代码更简洁精练，可读性更强，效率更高，甚至更易于维护
```javascript
setTimeout(function() {
	    alert("Time to take the cookies out of the oven");
	  }, 600000);
```

在需要函数引用的地方，都可使用函数表达式，因为其结果就是一个函数引用。  
如果需要将一个函数作为实参，可将实参指定为函数表达式。  
同样，如果需要从函数返回一个函数，也可返回一个函数表达式。  


可将函数声明放在任何地方，且可在任何地方调用它们。在代码的任何地方，函数声明创建的函数都是已定义的，这被称为 `提升（ hoisting）`

函数表达式显然不同，它创建的函数要等到它执行后才被定义。


### 嵌套函数
在代码顶层定义的函数与在函数中定义的函数之间的唯一差别在于，它们的作用域不同。

在代码顶层定义的函数是全局的，而在函数中定义的函数是局部的

### 词法作用域 
JavaScript的作用域规则完全基于代码的结构，而不是一些动态的运行阶段属性
词法作用域的**优点**: 总是可以通过查看代码来确定变量是在哪里定义的，进而确定它的值。

```javascript
var justAVar = "Oh, don't you worry about it, I'm GLOBAL";
function whereAreYou() {
  var justAVar = "Just an every day LOCAL";
  function inner() {
    return justAVar;
  }
  return inner;
}
var innerFunction = whereAreYou();
var result = innerFunction();
console.log(result);
```
所有的局部变量都存储在一个`环境（ environment）`中。  
**环境**:它存储了在局部作用域内定义的所有变量。
可将形参视为函数的局部变量，因此它们也包含在环境中。

当我们返回函数inner时， 返回的不仅仅是函数，还有与之相关联的环境。

```
var innerFunction = whereAreYou();
```
这条语句执行完毕后， 我们就有了变量innerFunction， 它指向whereAreYou返回的函数（ 及其环境）。
![](img/20180930-01.png)

```
var result = innerFunction();
```
调用innerFunction。 这将在相应的环境中执行它指向的函数的代码
![](img/20180930-02.png)

每个嵌套函数都有自己的小环境，其中包含它自己的变量。这样将形成一个环境链，从内到外依次为各个嵌套函数的环境。

在环境中查找变量时，你将从最近的环境着手，沿环境链不断往下查找，直到找到变量为止。如果在环境链中没有找到，再在全局环境中查找。

### 闭包： 指的是函数和引用环境
是极其强大的编程工具。

`局部变量`: 在函数体中定义的，包括所有的形参   
`自由变量`: 不是在本地定义的变量

`闭包` = 包含自由变量的函数 + 为所有这些自由变量提供了变量绑定的环境


### 使用闭包实现神奇的计数器
```
var count = 0;
function counter() {
  count = count + 1;
  return count;
}
console.log(counter());
```
问题是，使用全局变量count，协作开发代码时，大家常常会使用相同的变量名，进而导致冲突。


可以使用受保护的局部变量实现计数器。这样，计数器将不会与任何代码发生冲突，且只能通过调用相应的函数（也叫闭包）来增加计数器的值:
```
function makeCounter() {
  var count = 0;
  function counter() {
    count = count + 1;
    return count;
  }
  return counter;
}
var doCount = makeCoun
console.log(doCount())
```
在函数makeCounter中声明变量count。这样它就是局部变量， 而不是全局变量。  
这是一个闭包，在其环境中存储了变量count。  






