---
title: Vue的双向数据绑定原理
date: 2020-09-13 14:25
tags: Vue
catetory: 学习总结
---

vue.js是采用 **数据劫持** 结合 **发布者-订阅者** 模式的方式，通过 `Object.defineProperty()` 来劫持各个属性的 `setter`、`getter`，在数据变动时发布消息给订阅者，触发响应的监听回调。
具体步骤：
1. 需要 `observe`的数据对象进行递归遍历，包括子属性对象的属性，都加上 `setter` 和 `getter`。
这样的话，给这个对象的某个值赋值，就会触发 `setter`，那么就能监听到了数据变化。<br>
2. `compile`` 解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图。
3. `Watcher` 订阅者是 `Observer` 和 `Compile` 之间通信的桥梁，主要做的事情是：
  (1) 在自身实例化时往属性订阅器(dep)里面添加自己
  (2) 自身必须有一个 `update()` 方法
  (3) 待属性变动 `dep.notice()` 通知时，能调用自身的 `update()` 方法，并触发 `Compile` 中绑定的回调，则功成身退
4. **MVVM** 作为数据绑定的入口，整合 `Observer`、`Compile` 和 `Watcher` 三者，通过 `Observer` 来监听自己的 `model` 数据变化，通过`Compil` 来解析编译模板指令，最终利用 `Watcher` 搭起 `Observer` 和 `Compile` 之间的通信桥梁，达到 **数据变化 --> 视图更新**；**视图交互变化(input) --> 数据model变更** 的双向绑定效果。