---
title: this优先级
date: 
comments: true        # true false默认不写
#photos: https://w.wallhaven.cc/full/1p/wallhaven-1pd1o9.jpg
tags: this优先级
description: this优先级(显示绑定，隐式绑定，new绑定)及一些特殊绑定和面试题
categories: 
 - [前端,this]
---
<img src="/images/this背景.jpg"  />
<!--more-->

## this优先级

### 显示绑定高于隐式绑定

```javascript
var obj = {
  name: "obj",
  foo: function() {
    console.log(this)
  }
}

obj.foo() // obj

// 1.call/apply的显示绑定高于隐式绑定
obj.foo.apply('abc') // abc
obj.foo.call('abc') // abc

// 2.bind的优先级高于隐式绑定
var bar = obj.foo.bind("cba")
bar() // cba

// 3.更明显的比较
function foo() {
  console.log(this)
}

var obj = {
  name: "obj",
  foo: foo.bind("aaa")
}

obj.foo() // aaa
```

### new高于隐式绑定和显示绑定

```javascript
var obj = {
  name: "obj",
  foo: function() {
    console.log(this)
  }
}

// new的优先级高于隐式绑定
var f = new obj.foo() // foo
var bar = obj.foo.bind("aaa") // foo
var obj = new bar() // foo
```

### 总结

> <span style="color:#56c5ab" >new绑定 > 显示绑定(apply/call/bind) > 隐式绑定(obj.foo()) > 默认绑定(独立函数调用)</span>

## this特殊绑定

```javascript
function foo() {
  console.log(this)
}

foo.apply("abc")
foo.apply({})

// apply/call/bind: 当传入null/undefined时, 自动将this绑定成全局对象
foo.apply(null)
foo.apply(undefined)

var bar = foo.bind(null)
bar()
```

```javascript
var obj1 = {
  name: "obj1",
  foo: function() {
    console.log(this)
  }
}

var obj2 = {
  name: "obj2"
}; // 代码规范问题，不加分号会认为和最后一行是一个整体

// obj2.bar = obj1.foo
// obj2.bar()

(obj2.bar = obj1.foo)()
```

