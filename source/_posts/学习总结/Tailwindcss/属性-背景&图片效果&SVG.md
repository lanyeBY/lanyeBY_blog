---
title: 属性-背景&图片效果&SVG
date: 2024-01-26 17:08
tags: Tailwindcss
catetory: 学习总结
---

### Background Attachment

设置背景图像的位置是在视口内固定，或者随着包含它的区块滚动。

|`className`|`css`|说明|
|---|---|---|
|`bg-fixed`|`background-attachment: fixed;`|背景相对于视口固定，即使一个元素拥有滚动机制，背景也不会随着元素的内容滚动。|
|`bg-local`|`background-attachment: local;`|背景相对于元素的内容固定，如果一个元素拥有滚动机制，背景将会随着元素的内容滚动，并且背景的绘制区域和定位区域是相对于可滚动的区域而不是包含他们的边框。|
|`bg-scroll`|`background-attachment: scroll;`|背景相对于元素本身固定，而不是随着它的内容滚动。|

### Background Clip

设置元素的背景（背景图片或颜色）是否延伸到边框、内边距盒子、内容盒子下面。

|`className`|`css`|说明|
|---|---|---|
|`bg-clip-border`|`background-clip: border-box;`|背景延伸至边框外沿（但是在边框下层）|
|`bg-clip-padding`|`background-clip: padding-box;`|背景延伸至内边距（padding）外沿。不会绘制到边框处。|
|`bg-clip-content`|`background-clip: content-box;`|背景被裁剪至内容区（content box）外沿。|
|`bg-clip-text`|`background-clip: text;`|背景被裁剪成文字的前景色。|

### Background Color

|`className`|`css`|
|---|---|
|`bg-inherit`|`background-color: inherit;`|
|`bg-current`|`background-color: currentColor;`|
|`bg-transparent`|`background-color: transparent;`|
|`bg-black`|`background-color: #000;`|
|`bg-white`|`background-color: #fff;`|
|`bg-[#ff2f2f]`|`background-color: #ff2f2f;`|

可以在配置中增加自定义颜色：

```javascript
module.exports = {
  theme: {
    extend: {
      colors: {
        'regal-blue': '#243c5a',
      },
    }
  }
}
```

```html
<p class="bg-regal-blue">
  <!-- ... -->
</p>
```

### Background Origin

指定背景图片 `background-image` 属性的原点位置的背景相对区域

|`className`|`css`|说明|
|---|---|---|
|`bg-origin-border`|`background-origin: border-box;`|背景图片的摆放以 `border` 区域为参考|
|`bg-origin-padding`|`background-origin: padding-box;`|背景图片的摆放以 `padding` 区域为参考|
|`bg-origin-content`|`background-origin: content-box;`|背景图片的摆放以 `content` 区域为参考|

### Background Position

为背景图片设置初始位置。这个位置是相对于由 `background-origin` 定义的位置图层的。

|`className`|`css`|
|---|---|
|`bg-bottom`|`background-position: bottom;`|
|`bg-center`|`background-position: center;`|
|`bg-left`|`background-position: left;`|
|`bg-left-bottom`|`background-position: left bottom;`|
|`bg-left-top`|`background-position: left top;`|
|`bg-right`|`background-position: right;`|
|`bg-right-bottom`|`background-position: right bottom;`|
|`bg-right-top`|`background-position: right top;`|
|`bg-top`|`background-position: top;`|

### Background Repeat

|`className`|`css`|
|---|---|
|`bg-repeat`|`background-repeat: repeat;`|
|`bg-no-repeat`|`background-repeat: no-repeat;`|
|`bg-repeat-x`|`background-repeat: repeat-x;`|
|`bg-repeat-y`|`background-repeat: repeat-y;`|
|`bg-round`|`background-repeat: round;`|
|`bg-space`|`background-repeat: space;`|

### Background Size

|`className`|`css`|
|---|---|
|`bg-auto`|`background-size: auto;`|
|`bg-cover`|`background-size: cover;`|
|`bg-contain`|`background-size: contain;`|

### Background Image

|`className`|`css`|
|---|---|
|`bg-none`|`background-image: none;`|
|`bg-[url(...)]`|`background-image: url(...);`|

### Blur

将高斯模糊应用于输入图像。

|`className`|`css`|
|---|---|
|`blur-none`|`filter: blur(0);`|
|`blur-sm`|`filter: blur(4px);`|
|`blur`|`filter: blur(8px);`|
|`blur-md`|`filter: blur(12px);`|
|`blur-lg`|`filter: blur(16px);`|
|`blur-xl`|`filter: blur(24px);`|
|`blur-2xl`|`filter: blur(40px);`|
|`blur-3xl`|`filter: blur(64px);`|

### Brightness

将线性乘法器应用于输入图像，以调整其亮度。值为 `0%` 将创建全黑图像；值为 `100%` 会使输入保持不变，其他值是该效果的线性乘数。如果值大于 `100%` 将使图像更加明亮。

|`className`|`css`|
|---|---|
|`brightness-0`|`filter: brightness(0);`|
|`brightness-{x}`|`filter: brightness(x / 100);`|

### Contrast

调整输入图像的对比度。值是 `0%` 将使图像变灰；值是 `100%`，则无影响；若值超过 `100%` 将增强对比度。

|`className`|`css`|
|---|---|
|`contrast-0`|`filter: contrast(0);`|
|`contrast-{x}`|`filter: contrast(x / 100);`|

### Drop Shadow

使用 `<shadow>` 参数沿图像的轮廓生成阴影效果。阴影语法类似于 `<box-shadow>`，但不允许使用 `inset` 关键字以及 `spread` 参数。与所有 `filter` 属性值一样，任何在 `drop-shadow()` 后的滤镜同样会应用在阴影上。

|`className`|`css`|
|---|---|
|`drop-shadow-sm`|`filter: drop-shadow(0 1px 1px rgb(0 0 0 / 0.05));`|
|`drop-shadow`|`filter: drop-shadow(0 1px 2px rgb(0 0 0 / 0.1)) drop-shadow(0 1px 1px rgb(0 0 0 / 0.06));`|
|`drop-shadow-md`|`filter: drop-shadow(0 4px 3px rgb(0 0 0 / 0.07)) drop-shadow(0 2px 2px rgb(0 0 0 / 0.06));`|
|`drop-shadow-lg`|`filter: drop-shadow(0 10px 8px rgb(0 0 0 / 0.04)) drop-shadow(0 4px 3px rgb(0 0 0 / 0.1));`|
|`drop-shadow-xl`|`filter: drop-shadow(0 20px 13px rgb(0 0 0 / 0.03)) drop-shadow(0 8px 5px rgb(0 0 0 / 0.08));`|
|`drop-shadow-2xl`|`filter: drop-shadow(0 25px 25px rgb(0 0 0 / 0.15));`|
|`drop-shadow-none`|`filter: drop-shadow(0 0 #0000);`|

### Grayscale

将图像转换为灰度图。值为 `100%` 则完全转为灰度图像，若为初始值 `0%` 则图像无变化。值在 `0%` 到 `100%` 之间，则是该效果的线性乘数。

|`className`|`css`|
|---|---|
|`grayscale-0`|`filter: grayscale(0);`|
|`grayscale`|`filter: grayscale(100%);`|

### Hue Rotate

应用色相旋转。`<angle>` 值设定图像会被调整的色环角度值。值为 `0deg`，则图像无变化。

|`className`|`css`|
|---|---|
|`hue-rotate-0`|`filter: hue-rotate(0);`|
|`hue-rotate-{x}`|`filter: hue-rotate(xdeg);`|

### Invert

反转输入图像。值为 `100%` 则图像完全反转，值为 `0%` 则图像无变化。值在` 0%` 和 `100%` 之间，则是该效果的线性乘数。

|`className`|`css`|
|---|---|
|`invert-0`|`filter: invert(0);`|
|`invert`|`filter: invert(100%);`|

### Saturate

改变图像饱和度。值为 `0%` 则是完全不饱和，值为 `100%` 则图像无变化。超过 `100%` 则增加饱和度。

|`className`|`css`|
|---|---|
|`saturate-0`|`filter: saturate(0);`|
|`saturate-{x}`|`filter: saturate(x / 100);`|

### Sepia

将图像转换为深褐色。值为 `100%` 则完全是深褐色的，值为 `0%` 图像无变化。

|`className`|`css`|
|---|---|
|`sepia-0`|`filter: sepia(0);`|
|`sepia`|`filter: sepia(100%);`|

### Fill

定义给定图形元素（`SVG`）内部的颜色。

|`className`|`class`|
|---|---|
|`fill-none`|`fill: none;`|
|`fill-inherit`|`fill: inherit;`|
|`fill-current`|`fill: currentColor;`|
|`fill-transparent`|`fill: transparent;`|
|`fill-black`|`fill: #000;`|
|`fill-white`|`fill: #fff;`|
|`fill-[#ff2f2f]`|`fill: #ff2f2f;`|

### Stroke

定义给定图形元素（`SVG`）线条的颜色。

|`className`|`class`|
|---|---|
|`stroke-none`|`stroke: none;`|
|`stroke-inherit`|`stroke: inherit;`|
|`stroke-current`|`stroke: currentColor;`|
|`stroke-transparent`|`stroke: transparent;`|
|`stroke-black`|`stroke: #000;`|
|`stroke-white`|`stroke: #fff;`|
|`stroke-[#ff2f2f]`|`stroke: #ff2f2f;`|

### Stroke Width

定义给定图形元素（`SVG`）线条的宽度。

|`className`|`class`|
|---|---|
|`stroke-0`|`stroke-width: 0;`|
|`stroke-1`|`stroke-width: 1;`|
|`stroke-2`|`stroke-width: 2;`|