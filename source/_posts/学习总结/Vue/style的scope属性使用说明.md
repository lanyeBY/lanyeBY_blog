---
title: style的scope属性使用说明
date: 2018-12-17 16:57
updated: 2020-08-27 16:55
tags: Vue
catetory: 学习总结
---

在 `vue` 组件中，为了使样式私有化（模块化），不对全局造成污染，可以在 `style` 标签上添加 `scoped` 属性以表示它的只属于当下的模块。

`scope` 使用私有化的工作原理如下说明：
> 首先，假设把这种组件叫做模块私有组件，其他的未加 `scoped` 的叫做模块一般组件。
  对于模块私有组件，vue通过在DOM结构以及css样式上加唯一不重复的标记，以保证唯一，达到样式私有化模块化的目的。例子见下：

##### 公共组件button组件
一个公共组件button，为了样式模块化，给其加上 `scoped` 属性

```html
<!-- button.vue -->
<template>
  <div class="button-warp">
    <button class="button">text</button>
  </div>
</template>

<style scoped>
  .button-warp {
    display: inline-block;
  }
  .button {
    padding: 5px 10px;
    font-size: 12px;
    border-radius: 2px;
  }
</style>
```

##### 浏览器渲染button组件
`button` 组件在浏览器渲染出的 `html` 部分和 `css` 部分分别为：

```html
<div data-v-2311c06a class="button-warp">
  <button data-v-2311c06a class="button">text</button>
</div>
```

```css
.button-warp[data-v-2311c06a] {
  display:inline-block;
}
.button[data-v-2311c06a] {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 2px;
}
```

`scoped` 的这一操作，虽然达到了组件样式模块化的目的，但是会造成一种后果：每个样式的权重加重了：理论上我们要去修改这个样式，需要更高的权重去覆盖这个样式。这是增加复杂度的其中一个维度。

使用了 `scoped` 属性之后，父组件的 `style` 样式将不会渗透到子组件中，然而子组件的根节点元素会同时被设置了 `scoped` 的父 `css` 样式和设置了 `scoped` 的子 `css` 样式影响，这么设计的目的是父组件可以对子组件根元素进行布局。 

如果想对设置了 `scoped` 的子组件里的元素进行控制可以使用'`>>>`'或者'`deep`'。
一些预处理程序例如 `sass` 不能解析 `>>>` 属性，这种情况下可以用 `deep`，它是 `>>>` 的别名，工作原理相同。