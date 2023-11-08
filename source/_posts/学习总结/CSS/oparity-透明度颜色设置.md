---
title: oparity：透明度颜色设置
date: 2018-04-30 16:07
update: 2020-09-13 15:15
tags: CSS
catetory: 学习总结
---

`rgba()` 可以只修改背景色透明度而不影响模块内置内容，如文本等的透明度。

但IE、Opera以及其他浏览器低版本也不支持，这个时候可以考虑使用 `oparity` 属性，并配合相关的css代码进行设置，也能达到相同的效果。详细代码见下：

```html
<style>
  div.div1 {
    position: relative;
    width: 200px;
    height: 200px;
  }
  div.div1 div {
    position: absolute;
    left: 0px;
    top: 0px;
  }
  div.div1 div.divbg {
    width: 100%;
    height: 100%;
    background: rgb(255,0,0);
    opacity: 0.5;
  }
</style>

<div class="div1">
  <div class="divbg"></div>
  <div class="text">这是一个div标签</div>
</div>
```

但是，`oparity` 属性只有IE6及以上版本才部分支持，到IE9版本才完全支持。
针对这类问题，可以使用IE浏览器的滤镜实现相同效果：

```css
  filter: alpha(opacity=50);
```

*补充*：设置一个元素的背景颜色，会填充元素的 `content`、`padding`、`border` 区域。
