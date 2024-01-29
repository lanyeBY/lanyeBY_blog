---
title: 属性-Borders&Effects
date: 2024-01-26 16:00
tags: Tailwindcss
catetory: 学习总结
---

### Border Radius

|`className`|`css`|
|---|---|
|`rounded-none`|`border-radius: 0;`|
|`rounded`|`border-radius: 0.25rem;`|
|`rounded-full`|`border-radius: 9999px;`|
|`rounded-t-{x}px`|`border-top-left-radius: {x}px; border-top-right-radius: {x}px;`|
|`rounded-t-full`|`border-top-left-radius: 9999px; border-top-right-radius: 9999px;`|
|`rounded-r-{x}px`|`border-top-right-radius: {x}px; border-bottom-right-radius: {x}px;`|
|`rounded-r-full`|`border-top-right-radius: 9999px; border-bottom-right-radius: 9999px;`|
|`rounded-b-{x}px`|`border-bottom-left-radius: {x}px; border-bottom-right-radius: {x}px;`|
|`rounded-b-full`|`border-bottom-left-radius: 9999px; border-bottom-right-radius: 9999px;`|
|`rounded-l-{x}px`|`border-top-left-radius: {x}px; border-bottom-left-radius: {x}px;`|
|`rounded-l-full`|`border-top-left-radius: 9999px; border-bottom-left-radius: 9999px;`|
|`rounded-tl-{x}px`|`border-top-left-radius: {x}px;`|
|`rounded-tl-full`|`border-top-left-radius: 9999px;`|
|`rounded-tr-{x}px`|`border-top-right-radius: {x}px;`|
|`rounded-tr-full`|`border-top-right-radius: 9999px;`|
|`rounded-bl-{x}px`|`border-bottom-left-radius: {x}px;`|
|`rounded-bl-full`|`border-bottom-left-radius: 9999px;`|
|`rounded-br-{x}px`|`border-bottom-right-radius: {x}px;`|
|`rounded-br-full`|`border-bottom-right-radius: 9999px;`|

可以设置具体数值：

```html
<!-- 同时设置四个相同的 -->
<div class="rounded-[12px]"><!-- ... --></div>

<!-- 同时设置四个不同的 -->
<div class="rounded-[12px_16px_10px_14px]"><!-- ... --></div>
```

### Border Width

|`className`|`css`|
|---|---|
|`border-0`|`border-width: 0px;`|
|`border`|`border-width: 1px;`|
|`border-x`|`border-left-width: 1px; border-right-width: 1px;`|
|`border-y`|`border-top-width: 1px; border-bottom-width: 1px;`|
|`border-t`|`border-top-width: 1px;`|
|`border-r`|`border-right-width: 1px;`|
|`border-b`|`border-bottom-width: 1px;`|
|`border-l`|`border-left-width: 1px;`|

### Border Color

|`className`|`css`|
|---|---|
|`border-inherit`|`border-color: inherit;`|
|`border-current`|`border-color: currentColor;`|
|`border-transparent`|`border-color: transparent;`|
|`border-black`|`border-color: #000;`|
|`border-white`|`border-color: #fff;`|
|`border-[#ff2f2f]`|`border-color: #ff2f2f;`|
|`border-x-black`|`border-left-color: #000; border-right-color: #000;`|
|`border-y-black`|`border-top-color: #000; border-bottom-color: #000;`|
|`border-t-black`|`border-top-color: #000;`|
|`border-r-black`|`border-right-color: #000;`|
|`border-b-black`|`border-bottom-color: #000;`|
|`border-l-black`|`border-left-color: #000;`|

### Border Style

|`className`|`css`|
|---|---|
|`border-solid`|`border-style: solid;`|
|`border-dashed`|`border-style: dashed;`|
|`border-dotted`|`border-style: dotted;`|
|`border-double`|`border-style: double;`|
|`border-hidden`|`border-style: hidden;`|
|`border-none`|`border-style: none;`|

### Divide Width

对每个子元素都进行增加边框，视觉效果相当于分割线。

|`className`|`css`|
|---|---|
|`divide-x-0 > * + *`|`border-right-width: 0px; border-left-width: 0px;`|
|`divide-x-2 > * + *`|`border-right-width: 0px; border-left-width: 2px;`|
|`divide-x-4 > * + *`|`border-right-width: 0px; border-left-width: 4px;`|
|`divide-x-8 > * + *`|`border-right-width: 0px; border-left-width: 8px;`|
|`divide-x > * + *`|`border-right-width: 0px; border-left-width: 1px;`|
|`divide-y-0 > * + *`|`border-top-width: 0px; border-bottom-width: 0px;`|
|`divide-y-2 > * + *`|`border-top-width: 2px; border-bottom-width: 0px;`|
|`divide-y-4 > * + *`|`border-top-width: 4px; border-bottom-width: 0px;`|
|`divide-y-8 > * + *`|`border-top-width: 8px; border-bottom-width: 0px;`|
|`divide-y > * + *`|`border-top-width: 1px; border-bottom-width: 0px;`|
|`divide-y-reverse > * + *`|`--tw-divide-y-reverse: 1;`|
|`divide-x-reverse > * + *`|`--tw-divide-x-reverse: 1;`|

### Divide Color

|`className`|`css`|
|---|---|
|`divide-inherit > * + *`|`border-color: inherit;`|
|`divide-current > * + *`|`border-color: currentColor;`|
|`divide-transparent > * + *`|`border-color: transparent;`|
|`divide-black > * + *`|`border-color: #000;`|
|`divide-white > * + *`|`border-color: #fff;`|
|`divide-[#ff2f2f]`|`border-color: #ff2f2f;`|

### Divide Style

|`className`|`css`|
|---|---|
|`divide-solid`|`border-style: solid;`|
|`divide-dashed`|`border-style: dashed;`|
|`divide-dotted`|`border-style: dotted;`|
|`divide-double`|`border-style: double;`|
|`divide-none`|`border-style: none;`|

### Outline Width

|`className`|`css`|
|---|---|
|`outline-0`|`outline-width: 0px;`|
|`outline-{x}`|`outline-width: {x}px;`|

### Outline Color

|`className`|`css`|
|---|---|
|`outline-inherit`|`outline-color: inherit;`|
|`outline-current`|`outline-color: currentColor;`|
|`outline-transparent`|`outline-color: transparent;`|
|`outline-black`|`outline-color: #000;`|
|`outline-white`|`outline-color: #fff;`|
|`outline-[#ff2f2f]`|`outline-color: #ff2f2f;`|

### Outline Style

|`className`|`css`|
|---|---|
|`outline-none`|`outline: 2px solid transparent; outline-offset: 2px;`|
|`outline`|`outline-style: solid;`|
|`outline-dashed`|`outline-style: dashed;`|
|`outline-dotted`|`outline-style: dotted;`|
|`outline-double`|`outline-style: double;`|

### Outline Offset

|`className`|`css`|
|---|---|
|`outline-offset-0`|`outline-offset: 0px;`|
|`outline-offset-{x}`|`outline-offset: {x}px;`|

### Box Shadow

|`className`|`css`|
|---|---|
|`shadow-sm`|`box-shadow: 0 1px 2px 0 rgb(0 0 0 / 0.05);`|
|`shadow`|`box-shadow: 0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1);`|
|`shadow-md`|`box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);`|
|`shadow-lg`|`box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);`|
|`shadow-xl`|`box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);`|
|`shadow-2xl`|`box-shadow: 0 25px 50px -12px rgb(0 0 0 / 0.25);`|
|`shadow-inner`|`box-shadow: inset 0 2px 4px 0 rgb(0 0 0 / 0.05);`|
|`shadow-none`|`box-shadow: 0 0 #0000;`|

可以设置具体值：

```html
<div class="shadow-[0_35px_60px_-15px_rgba(0,0,0,0.3)]"><!-- ... --></div>
```

### Opacity

|`className`|`css`|
|---|---|
|`opacity-0`|`opacity: 0;`|
|`opacity-{x}`|`opacity: {x / 100};`|
|`opacity-1`|`opacity: 1;`|
