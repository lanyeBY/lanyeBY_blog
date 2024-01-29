---
title: 属性-Tables
date: 2024-01-26 16:35
tags: Tailwindcss
catetory: 学习总结
---

### Border Collapse

决定表格的边框是分开的还是合并的。

|`className`|`class`|说明|
|---|---|---|
|`border-collapse`|`border-collapse: collapse;`|相邻的单元格共用同一条边框|
|`border-separate`|`border-collapse: separate;`|默认值。每个单元格拥有独立的边框|

### Border Spacing

指定相邻单元格边框之间的距离（只适用于 边框分离模式 ）。

|`className`|`class`|
|---|---|
|`border-spacing-0`|`border-spacing: 0px 0px;`|
|`border-spacing-px`|`border-spacing: 1px 1px;`|
|`border-spacing-x-0`|`border-spacing: 0px var(--tw-border-spacing-y);`|
|`border-spacing-x-px`|`border-spacing: 1px var(--tw-border-spacing-y);`|
|`border-spacing-y-0`|`border-spacing: var(--tw-border-spacing-x) 0px;`|
|`border-spacing-y-px`|`border-spacing: var(--tw-border-spacing-x) 1px;`|

### Table Layout

|`className`|`class`|说明|
|---|---|---|
|`table-auto`|`table-layout: auto;`|默认情况下，大多数浏览器使用自动表格布局算法。表格及其单元格的宽度会根据内容自动调整大小。
|`table-fixed`|`table-layout: fixed;`|表格和列的宽度是由 `table` 和 `col` 元素的宽度或第一行单元格的宽度来设置的。后续行中的单元格不会影响列的宽度。|

### Caption Side

将表格的标题（`<caption>`）放到规定的位置。

|`className`|`class`|
|---|---|
|`caption-top`|`caption-side: top;`|
|`caption-bottom`|`caption-side: bottom;`|
