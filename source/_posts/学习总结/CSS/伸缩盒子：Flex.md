---
title: 伸缩盒子：Flex
date: 2018-05-09 13:35
tags: CSS
catetory: 学习总结
---

在父元素中设置 `display: flex`，会使其内的每一个子元素自动变成伸缩项。
伸缩项的意思是，子元素的总宽度大于父元素的总宽度时，每一个子元素会进行一个平均收缩。可以通过设置相应的属性进行换行显示而不改变子元素宽度
伴随着伸缩盒子的有以下属性样式可以设置：

- `justify-content`: `flex-start` | `flex-end` | `center` | `space-between` | `space-around`
设置子元素的主轴方向上的排列方式
  - `flex-start`：让子元素从父容器的起始位置开始排列，无间隙，**默认值**
  - `flex-end`：让子元素从父容器的结束位置开始排列，无间隙
  - `space-between`：左右对齐父容器的开始和结束，中间平均分页，产生相同间距
  - `space-around`：将多余的空间平均分页在每一个子元素的两边 类似于 `margin：0 auto`
<br>

- `flex-wrap`:[`nowrap` | `wrap` | `wrap-reverse`]
控制子元素是否换行显示
  - `nowrap`：不换行，若子元素总宽度大于父元素，则子元素自动进行收缩，**默认值**
  - `wrap`：换行
  - `wrap-reverse`：翻转，原来是从上到下，翻转后就是从下到上排列
<br>

- `flex-derection`：[`row` | `column` | `row-reverse` | `column-reverse`]
设置子元素的排列方向，即设置主轴方向是水平方向还是垂直方向
  - `row`：水平方向从左到右排列子元素，**默认值**
  - `row-reverse`：水平方向从右到左排列子元素
  - `column`：垂直方向从上到下排列子元素
  - `column-reverse`：垂直方向从下到上排列子元素
<br>

- `flex-flow`：[`flex-wrap`] | [`flex-derection`];
两个属性结合在一起设置
<br>

- `flex-grow`：[`number`]
当子元素的总宽度小于父元素的总宽度时，可以设置子元素的宽度。注意，该属性应设置在子元素。**默认值为0**，即说明子元素不占据剩余空间。
设置当前元素应该占据剩余空间的比例值：当前空间的 `flex-grow` / 所有兄弟元素的 `flex-grow`。
  - `flex-grow`: 1;	/*占据( 1 / 所有兄弟元素的 `flex-grow` )*/
<br>

- `flex-shrink`：[`number`]
定义收缩比例，通过设置的值来计算收缩空间。需要设置在子元素。
设置当前元素应该占据不够空间的比例值的计算：当前空间的 `flex-shrink`/ 所有兄弟元素的`flex-shrink`。
  - `flex-shrink`: 1;	/*占据( 1 / 所有兄弟元素的 `flex-grow` )*/ **默认值**
  - `flex-shrink`: 0;	/*不收缩*/
<br>

- `flex`：[`flex-grow`] | [`flex-shrink`] | [`flex-basis`];
用来设置当前伸缩子项占据剩余空间的比例值。默认值为 `flex:0 1 auto `
<br>

- `align-items`：[`center` | `flex-start` | `flex-end` | `stretch` | `baseline`]
设置子元素（伸缩项）在侧轴方向上的对齐方式
  - `center`：设置在侧轴方向上居中对齐
  - `flex-start`：设置在侧轴方向上顶对齐
  - `flex-end`：设置在侧轴方向上底对齐
  - `stretch`：拉伸，让子元素在侧轴方向上进行拉伸，填充满整个侧轴方向 **默认值**
  - `baseline`：文本基线
<br>

- `align-self`：[`center` | `flex-start` | `flex-end` | `stretch` | `baseline`]
设置单个子元素在侧轴方向上的对齐方式
