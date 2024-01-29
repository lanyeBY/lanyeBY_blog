---
title: 属性-Flexbox&Grid
date: 2024-01-20 11:03
tags: Tailwindcss
catetory: 学习总结
---

### Flex Basis

|`className`|`css`|
|---|---|
|`basis-0`|`flex-basis: 0px;`|
|`basis-{x}`|`flex-basis: {y}rem;`|
|`basis-auto`|`flex-basis: auto;`|
|`basis-px`|`flex-basis: 1px;`|
|`basis-1/2`|`flex-basis: 50%;`|
|`basis-{x}/3`|`flex-basis: {100/3*x}%;`|
|`basis-{x}/4`|`flex-basis: {100/4*x}%;`|
|`basis-{x}/5`|`flex-basis: {100/5*x}%;`|
|`basis-{x}/6`|`flex-basis: {100/6*x}%;`|
|`basis-{x}/12`|`flex-basis: {100/12*x}%;`|
|`basis-full`|`flex-basis: 100%;`|

### Flex Direction

|`className`|`css`|
|---|---|
|`flex-row`|`flex-direction: row;`|
|`flex-row-reverse`|`flex-direction: row-reverse;`|
|`flex-col`|`flex-direction: column;`|
|`flex-col-reverse`|`flex-direction: column-reverse;`|

### Flex Wrap

|`className`|`css`|
|---|---|
|`flex-wrap`|`flex-wrap: wrap;`|
|`flex-wrap-reverse`|`flex-wrap: wrap-reverse;`|
|`flex-nowrap`|`flex-wrap: nowrap;`|

### Flex

|`className`|`css`|
|---|---|
|`flex-1`|`flex: 1 1 0%;`|
|`flex-auto`|`flex: 1 1 auto;`|
|`flex-initial`|`flex: 0 1 auto;`|
|`flex-none`|`flex: none;`|

### Flex Grow

|`className`|`css`|
|---|---|
|`grow`|`flex-grow: 1;`|
|`grow-0`|`flex-grow: 0;`|

### Flex Shrink

|`className`|`css`|
|---|---|
|`shrink`|`flex-shrink: 1;`|
|`shrink-0`|`flex-shrink: 0;`|

### Order

|`className`|`css`|
|---|---|
|`order-{x}`|`order: {x};`|

### Grid Template Columns

|`className`|`css`|
|---|---|
|`grid-cols-{x}`|`grid-template-columns: repeat({x}, minmax(0, 1fr));`|
|`grid-cols-none`|`grid-template-columns: none;`|
|`grid-cols-subgrid`|`grid-template-columns: subgrid;`|

### Grid Column Start / End

|`className`|`css`|
|---|---|
|`col-auto`|`grid-column: auto;`|
|`col-span-{x}`|`grid-column: span {x} / span {x};`|
|`col-span-full`|`grid-column: 1 / -1;`|
|`col-start-{x}`|`grid-column-start: {x};`|
|`col-start-auto`|`grid-column-start: auto;`|
|`col-end-{x}`|`grid-column-end: {x};`|
|`col-end-auto`|`grid-column-end: auto;`|

### Grid Template Rows

|`className`|`css`|
|---|---|
|`grid-rows-{x}`|`grid-template-rows: repeat({x}, minmax(0, 1fr));`|
|`grid-rows-none`|`grid-template-rows: none;`|
|`grid-rows-subgrid`|`grid-template-rows: subgrid;`|

### Grid Row Start / End

|`className`|`css`|
|---|---|
|`row-auto`|`grid-row: auto;`|
|`row-span-{x}`|`grid-row: span {x} / span {x};`|
|`row-span-full`|`grid-row: 1 / -1;`|
|`row-start-{x}`|`grid-row-start: {x};`|
|`row-start-auto`|`grid-row-start: auto;`|
|`row-end-{x}`|`grid-row-end: {x};`|
|`row-end-auto`|`grid-row-end: auto;`|

### Grid Auto Flow

|`className`|`css`|
|---|---|
|`grid-flow-row`|`grid-auto-flow: row;`|
|`grid-flow-col`|`grid-auto-flow: column;`|
|`grid-flow-dense`|`grid-auto-flow: dense;`|
|`grid-flow-row-dense`|`grid-auto-flow: row dense;`|
|`grid-flow-col-dense`|`grid-auto-flow: column dense;`|

### Grid Auto Columns

|`className`|`css`|
|---|---|
|`auto-cols-auto`|`grid-auto-columns: auto;`|
|`auto-cols-min`|`grid-auto-columns: min-content;`|
|`auto-cols-max`|`grid-auto-columns: max-content;`|
|`auto-cols-fr`|`grid-auto-columns: minmax(0, 1fr);`|

### Grid Auto Rows

|`className`|`css`|
|---|---|
|`auto-rows-auto`|`grid-auto-rows: auto;`|
|`auto-rows-min`|`grid-auto-rows: min-content;`|
|`auto-rows-max`|`grid-auto-rows: max-content;`|
|`auto-rows-fr`|`grid-auto-rows: minmax(0, 1fr);`|

### Gap

|`className`|`css`|
|---|---|
|`gap-0`|`gap: 0px;`|
|`gap-x-0`|`column-gap: 0px;`|
|`gap-y-0`|`row-gap: 0px;`|
|`gap-px`|`gap: 1px;`|
|`gap-x-px`|`column-gap: 1px;`|
|`gap-y-px`|`row-gap: 1px;`|
|`gap-{x}`|`gap: {y}rem;`|
|`gap-x-{x}`|`column-gap: {y}rem;`|
|`gap-y-{x}`|`row-gap: {y}rem;`|

### Justify Content

|`className`|`css`|
|---|---|
|`justify-normal`|`justify-content: normal;`|
|`justify-start`|`justify-content: flex-start;`|
|`justify-end`|`justify-content: flex-end;`|
|`justify-center`|`justify-content: center;`|
|`justify-between`|`justify-content: space-between;`|
|`justify-around`|`justify-content: space-around;`|
|`justify-evenly`|`justify-content: space-evenly;`|
|`justify-stretch`|`justify-content: stretch;`|

### Justify Items

|`className`|`css`|
|---|---|
|`justify-items-start`|`justify-items: start;`|
|`justify-items-end`|`justify-items: end;`|
|`justify-items-center`|`justify-items: center;`|
|`justify-items-stretch`|`justify-items: stretch;`|

### Justify Self

|`className`|`css`|
|---|---|
|`justify-self-auto`|`justify-self: auto;`|
|`justify-self-start`|`justify-self: start;`|
|`justify-self-end`|`justify-self: end;`|
|`justify-self-center`|`justify-self: center;`|
|`justify-self-stretch`|`justify-self: stretch;`|

### Justify Self

|`className`|`css`|
|---|---|
|`content-normal`|`align-content: normal;`|
|`content-center`|`align-content: center;`|
|`content-start`|`align-content: flex-start;`|
|`content-end`|`align-content: flex-end;`|
|`content-between`|`align-content: space-between;`|
|`content-around`|`align-content: space-around;`|
|`content-evenly`|`align-content: space-evenly;`|
|`content-baseline`|`align-content: baseline;`|
|`content-stretch`|`align-content: stretch;`|

### Align Items

|`className`|`css`|
|---|---|
|`items-start`|`align-items: flex-start;`|
|`items-end`|`align-items: flex-end;`|
|`items-center`|`align-items: center;`|
|`items-baseline`|`align-items: baseline;`|
|`items-stretch`|`align-items: stretch;`|

### Align Self

|`className`|`css`|
|---|---|
|`self-auto`|`align-self: auto;`|
|`self-start`|`align-self: flex-start;`|
|`self-end`|`align-self: flex-end;`|
|`self-center`|`align-self: center;`|
|`self-baseline`|`align-self: baseline;`|
|`self-stretch`|`align-self: stretch;`|

### Place Content

`align-content` 和 `justify-content` 的简写。使用这两个属性的值可以用于任何的布局情况。

|`className`|`css`|
|---|---|
|`place-content-center`|`place-content: center;`|
|`place-content-start`|`place-content: start;`|
|`place-content-end`|`place-content: end;`|
|`place-content-between`|`place-content: space-between;`|
|`place-content-around`|`place-content: space-around;`|
|`place-content-evenly`|`place-content: space-evenly;`|
|`place-content-baseline`|`place-content: baseline;`|
|`place-content-stretch`|`place-content: stretch;`|

### Place Items

`align-items` 和 `justify-items` 的简写。在相关的布局（如 Grid 或 Flexbox）中可以同时沿着块级和内联方向对齐元素。如果未提供第二个值，则第一个值作为第二个值的默认值。

|`className`|`css`|
|---|---|
|`place-items-start`|`place-items: start;`|
|`place-items-end`|`place-items: end;`|
|`place-items-center`|`place-items: center;`|
|`place-items-baseline`|`place-items: baseline;`|
|`place-items-stretch`|`place-items: stretch;`|

### Place Self

`align-self` 和 `justify-self` 的简写。

|`className`|`css`|
|---|---|
|`place-self-auto`|`place-self: auto;`|
|`place-self-start`|`place-self: start;`|
|`place-self-end`|`place-self: end;`|
|`place-self-center`|`place-self: center;`|
|`place-self-stretch`|`place-self: stretch;`|