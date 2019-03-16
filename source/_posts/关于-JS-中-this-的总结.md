---
title: 关于 JS 中 this 的总结
date: 2019-03-16 08:23:13
tags:
---


1. 默认是全局对象, 严格模式下为 undefined

2. 普通函数的 this 在调用时确定

   1. 谁调用, 谁就是 this.
   2. 作为对象方法, 原型链方法, 对象的 getter/setter 方法时也是如此.
   3. 使用 bind call apply 可绑定 this. 替代调用时确定的规则.

3. 箭头函数的 this 继承自作用域链上层

   1. 本身没有 this, 也无法绑定 this.

4. new 构造函数, this 为正在构造的对象

   1. 构造函数默认返回 this, 返回对象时除外

5. dom 事件处理函数, this 为触发事件的元素.

6. on-event 内联函数, this 为绑定的元素.
