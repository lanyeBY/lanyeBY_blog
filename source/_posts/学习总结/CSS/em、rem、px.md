---
title: em、rem、px
date: 2019-08-12 14:36
tags: CSS
catetory: 学习总结
---

#### em
`em` 是最常见的相对长度单位，这是排版中使用的一种度量方式，基准值是当前元素的字号大小。 在CSS中，`1em` 表示当前元素的字号大小，实际值取决于在哪个元素上应用。

```css
.box {
  font-size: 16px;
  padding: 1em;
}
```

如上代码所示，则就会生成一个 `padding = 16px` 的元素。
但我们也会遇到给元素的 `font-size` 属性也使用 `em` 去赋值。这个时候就要看该元素继承其父元素的 `font-size` 是多少了。看下面的例子。

```html
<div class="box">
  <div class="sub-box"></div>
</div>
```

```css
.box {
  font-size: 16px;
}
.sub-box {
  font-size: 1.2em;
  padding: 1.2em;
}
```
上述代码执行，会生成一个 `font-size = 16 * 1.2 = 19.2px`、`padding = 19.2 * 1.2 = 23.04px` 的 `div.sub-box` 元素。

相同的数值但是不相同的结果。

原因是除了作用在字体大小的 `css` 数值属性，所有的属性的 `em` 结果值都是基于当前元素的字体大小来计算的。

牢记这一点，`em` 的长度单位，其最后生成的长度是基于当前元素的字号大小生成的。

#### rem

根节点是文档里所有其他元素的祖先。它有一个特别的伪类（pseudo-class）选择器（`:root`），在样式表里可以用这个选择器表示。使用带类名的类型选择器html，或者直接用标签选择器，效果是一样的。
`rem` 是根 `em`（root em）的缩写。`rem` 是和根元素关联的，不依赖当前元素。

```html
<div class="box">
  <div class="sub-box"></div>
</div>
```

```css
:root {
  font-size: 0.875em;
}
.box {
  font-size: 16px;
}
.sub-box {
  font-size: 1rem;
  padding: 1.2em;
}
```

浏览器默认字号为 `16px`，对根节点伪类选择器定义字号，进而修改当前页面的默认字号为 `14px`。
上述代码执行，会生成一个 `font-size = 14 * 1 = 14px`、`padding = 14 * 1.2 = 16.8px`的 `div.sub-box` 元素。

对 `font-size` 使用 `rem` ，对 `border` 使用 `px` ，对其他的度量方式如 `padding`、`margin`、`border-radius` 等使用 `em` 。

然而在必要时，需要声明容器的 宽度 的话，我更喜欢使用百分比。
