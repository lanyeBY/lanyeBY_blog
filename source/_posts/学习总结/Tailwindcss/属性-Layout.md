---
title: 属性-Layout
date: 2024-01-20 11:03
tags: Tailwindcss
catetory: 学习总结
---

### Aspect Ratio

可用于设置元素的长宽比，对应CSS属性：`aspect-ratio`。

以下是可选的值：

|`className`|`css`|
|---|---|
|`aspect-auto`|`aspect-ratio: auto;`|
|`aspect-square`|`aspect-ratio: 1 / 1;`|
|`aspect-video`|`aspect-ratio: 16 / 9;`|

也可以自定义长宽比值：

```html
<iframe class="w-full aspect-[4/3]" src="https://www.youtube.com/..."></iframe>
```

### Container

使元素的最大宽度适应于当前窗口的最小宽度（响应式配置）：

|`className`|尺寸|`css`|
|---|---|---|
|`container`|`DEFAULT`|`width: 100%;`|
||`sm` *（640px）*|`max-width: 640px;`|
||`md` *（768px）*|`max-width: 768px;`|
||`lg` *（1024px）*|`max-width: 1024px;`|
||`xl` *（1280px）*|`max-width: 1280px;`|
||`2xl` *（1536px）*|`max-width: 1536px;`|

注意，只能对容器的宽度作用，对内容没有进一步影响。如果需要对内容自动居中，可以配合使用 `mx-auto`：

```html
<div class="container mx-auto">
  <!-- ... -->
</div>
```

如果需要默认将容器的内容进行居中，也可以在配置中进行设置，从而对项目全局的 `container` 容器生效而不需要意义配置居中属性：

```javascript
module.exports = {
  theme: {
    container: {
      center: true,
    },
  },
}
```

还可以对容器进行统一的样式配置（如内间距的配置等）：

```javascript
// 统一配置内间距
module.exports = {
  theme: {
    container: {
      padding: '2rem',
    },
  },
}

// 也可以对各个尺寸下的内间距分开配置
module.exports = {
  theme: {
    container: {
      padding: {
        DEFAULT: '1rem',
        sm: '2rem',
        lg: '4rem',
        xl: '5rem',
        '2xl': '6rem',
      },
    },
  },
};
```

### Columns

栅栏结构，瀑布流结构，可以是元素内的内容根据需要的列数进行展示，列宽度会自动调整：

|`className`|`css`|
|---|---|
|`columns-1`|`columns: 1;`|
|...|...|
|`columns-8`|`columns: 8;`|

```html
<div class="columns-3 ...">
  <img class="w-full aspect-video ..." src="..." />
  <img class="w-full aspect-square ..." src="..." />
  <!-- ... -->
</div>
```

可以配合 `gap-x` 用来设置列之间的间隙：

```html
<div class="gap-8 columns-3 ...">
  <img class="w-full aspect-video ..." src="..." />
  <img class="w-full aspect-square ..." src="..." />
  <!-- ... -->
</div>
```

### Box Decoration Break

当元素跨多行、多列或多页时，元素的片段应如何呈现。

以下是可选的值：

|`className`|`css`|
|---|---|
|`box-decoration-clone`|`box-decoration-break: clone;`|
|`box-decoration-slice`|`box-decoration-break: slice;`|

### Box Sizing

定义浏览器应该如何计算一个元素的总宽度和总高度。

以下是可选的值：

|`className`|`css`|
|---|---|
|`box-border`|`box-sizing: border-box;`|
|`box-content`|`box-sizing: content-box;`|

### Display

设置元素布局，例如流式布局、内联布局、网格布局、弹性布局。

以下是可选的值：

|`className`|`css`|说明|
|---|---|---|
|`block`|`display: block;`|
|`inline-block`|`display: inline-block;`|
|`inline`|`display: inline;`|
|`flex`|`display: flex;`|
|`inline-flex`|`display: inline-flex;`|
|`table`|`display: table;`|
|`inline-table`|`display: inline-table;`|
|`table-caption`|`display: table-caption;`|类似于 `<caption>` 元素|
|`table-cell`|`display: table-cell;`|类似于 `<td>` 元素|
|`table-column`|`display: table-column;`|类似于 `<col>` 元素|
|`table-column-group`|`display: table-column-group;`|类似于 `<colgroup>` 元素|
|`table-footer-group`|`display: table-footer-group;`|类似于 `<tfoot>` 元素|
|`table-header-group`|`display: table-header-group;`|类似于 `<thead>` 元素|
|`table-row-group`|`display: table-row-group;`|类似于 `<tbody>` 元素|
|`table-row`|`display: table-row;`|类似于 `<tr>` 元素|
|`flow-root`|`display: flow-root;`|生成一个块级元素盒，并建立一个新的块级格式化上下文，定义格式化上下文的根元素|
|`grid`|`display: grid;`|类似块级元素并且根据网格模型布局它的内容|
|`inline-grid`|`display: inline-grid;`|
|`contents`|`display: contents;`|
|`list-item`|`display: list-item;`|为内容生成一个块级盒子和一个单独的列表元素内联盒子|
|`hidden`|`display: none;`|

### Floats

|`className`|`css`|
|---|---|
|`float-start`|`float: inline-start;`|
|`float-end`|`float: inline-end;`|
|`float-right`|`float: right;`|
|`float-left`|`float: left;`|
|`float-none`|`float: none;`|

### Clear

|`className`|`css`|
|---|---|
|`clear-start`|`clear: inline-start;`|
|`clear-end`|`clear: inline-end;`|
|`clear-right`|`clear: right;`|
|`clear-left`|`clear: left;`|
|`clear-both`|`clear: both;`|
|`clear-none`|`clear: none;`|

### Object Fit

指定可替换元素（例如：`<img>` 或 `<video>`）的内容应该如何适应到其使用高度和宽度确定的框。

|`className`|`css`|说明|
|---|---|---|
|`object-contain`|`object-fit: contain;`|被替换的内容将被缩放，以在填充元素的内容框时保持其宽高比。整个对象在填充盒子的同时保留其长宽比，因此如果宽高比与框的宽高比不匹配，该对象将被添加“黑边”|
|`object-cover`|`object-fit: cover;`|被替换的内容在保持其宽高比的同时填充元素的整个内容框。如果对象的宽高比与内容框不相匹配，该对象将被剪裁以适应内容框。|
|`object-fill`|`object-fit: fill;`|被替换的内容正好填充元素的内容框。整个对象将完全填充此框。如果对象的宽高比与内容框不相匹配，那么该对象将被拉伸以适应内容框。|
|`object-none`|`object-fit: none;`|被替换的内容将保持其原有的尺寸。|
|`object-scale-down`|`object-fit: scale-down;`|内容的尺寸与 none 或 contain 中的一个相同，取决于它们两个之间谁得到的对象尺寸会更小一些|

### Object Position

元素在其内容框中的位置。内容框中未被对象所覆盖的部分，则会显示该元素的背景。

|`className`|`css`|
|---|---|
|`object-bottom`|`object-position: bottom;`|
|`object-center`|`object-position: center;`|
|`object-left`|`object-position: left;`|
|`object-left-bottom`|`object-position: left bottom;`|
|`object-left-top`|`object-position: left top;`|
|`object-right`|`object-position: right;`|
|`object-right-bottom`|`object-position: right bottom;`|
|`object-right-top`|`object-position: right top;`|
|`object-top`|`object-position: top;`|

### Overflow

设置元素溢出时所需的行为。

|`className`|`css`|
|---|---|
|`overflow-auto`|`overflow: auto;`|
|`overflow-hidden`|`overflow: hidden;`|
|`overflow-clip`|`overflow: clip;`|
|`overflow-visible`|`overflow: visible;`|
|`overflow-scroll`|`overflow: scroll;`|
|`overflow-x-auto`|`overflow-x: auto;`|
|`overflow-y-auto`|`overflow-y: auto;`|
|`overflow-x-hidden`|`overflow-x: hidden;`|
|`overflow-y-hidden`|	`overflow-y: hidden;`|
|`overflow-x-clip`|	`overflow-x: clip;`|
|`overflow-y-clip`|	`overflow-y: clip;`|
|`overflow-x-visible`|	`overflow-x: visible;`|
|`overflow-y-visible`|	`overflow-y: visible;`|
|`overflow-x-scroll`|	`overflow-x: scroll;`|
|`overflow-y-scroll`|	`overflow-y: scroll;`|

### Overscroll Behavior

控制浏览器过度滚动（滚动到边界）时的表现。
默认情况下，当触及页面顶部或者底部时（或者是其他可滚动区域），移动端浏览器倾向于提供一种“触底”效果，甚至进行页面刷新。

可以分别对 `x` 和 `y` 轴上的值进行设置，下面是可选的值：

- `auto`：默认效果
- `contai`n：设置这个值后，默认的滚动边界行为不变（“触底”效果或者刷新），但是临近的滚动区域不会被滚动链影响到，比如对话框后方的页面不会滚动。
- `none`：临近滚动区域不受到滚动链影响，而且默认的滚动到边界的表现也被阻止。

|`className`|`css`|
|---|---|
|`overscroll-auto`|`overscroll-behavior: auto;`|
|`overscroll-contain`|`overscroll-behavior: contain;`|
|`overscroll-none`|`overscroll-behavior: none;`|
|`overscroll-y-auto`|`overscroll-behavior-y: auto;`|
|`overscroll-y-contain`|`overscroll-behavior-y: contain;`|
|`overscroll-y-none`|`overscroll-behavior-y: none;`|
|`overscroll-x-auto`|`overscroll-behavior-x: auto;`|
|`overscroll-x-contain`|`overscroll-behavior-x: contain;`|
|`overscroll-x-none`|`overscroll-behavior-x: none;`|

### Position

元素在文档中的定位方式。

|`className`|`css`|
|---|---|
|`static`|`position: static;`|
|`fixed`|`position: fixed;`|
|`absolute`|`position: absolute;`|
|`relative`|`position: relative;`|
|`sticky`|`position: sticky;`|

### Top / Right / Bottom / Left

|`className`|`css`|
|---|---|
|`inset-0`|`inset: 0px;`|
|`inset-x-0`|`left: 0px; right: 0px;`|
|`inset-y-0`|`top: 0px; bottom: 0px;`|
|`start-0`|`inset-inline-start: 0px;`|
|`end-0`|`inset-inline-end: 0px;`|
|`top-0`|`top: 0px;`|
|`right-0`|`right: 0px;`|

### Visibility

|`className`|`css`|
|---|---|
|`visible`|`visibility: visible;`|
|`invisible`|`visibility: invisible;`|
|`collapse`|`visibility: collapse;`|

### Z-index

|`className`|`css`|
|---|---|
|`z-0`|`z-index: 0`|
|`z-10`|`z-index: 10`|
|`z-20`|`z-index: 20`|
|`z-30`|`z-index: 30`|
|`z-40`|`z-index: 40`|
|`z-50`|`z-index: 50`|
|`z-auto`|`z-index: auto`|

