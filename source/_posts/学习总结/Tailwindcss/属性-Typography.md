---
title: 属性-Typography
date: 2024-01-26 14:35
tags: Tailwindcss
catetory: 学习总结
---

### Font Family

|`className`|`css`|
|---|---|
|`font-sans`|`font-family: ui-sans-serif, system-ui, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";`|
|`font-serif`|`font-family: ui-serif, Georgia, Cambria, "Times New Roman", Times, serif;`|
|`font-mono`|`font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;`|

也可以在配置中对字体进行自定义，可以是数组，也可以是由逗号分隔的字符串。
注意：字体名称中不应包含空格符，如果存在，需要将其用引号括起来，或使用转义字符：

```javascript
module.exports = {
  theme: {
    fontFamily: {
      'display': ['Oswald', ...],
      'body': ['"Open Sans"', ...],
      // 字符串形式
      'sans': 'Helvetica, Arial, sans-serif',
      // 使用引号
      'sans': ['"Exo 2"', ...],
      // 使用转义字符
      'sans': ['Exo\\ 2', ...],
    }
  }
}
```

### Font Size

|`className`|`css`|
|---|---|
|`text-xs`|`font-size: 0.75rem; line-height: 1rem;`|
|`text-sm`|`font-size: 0.875rem; line-height: 1.25rem;`|
|`text-base`|`font-size: 1rem; line-height: 1.5rem;`|
|`text-lg`|`font-size: 1.125rem; line-height: 1.75rem;`|
|`text-xl`|`font-size: 1.25rem; line-height: 1.75rem;`|
|`text-2xl`|`font-size: 1.5rem; line-height: 2rem;`|
|`text-3xl`|`font-size: 1.875rem; line-height: 2.25rem;`|
|`text-4xl`|`font-size: 2.25rem; line-height: 2.5rem;`|
|`text-5xl`|`font-size: 3rem; line-height: 1;`|
|`text-6xl`|`font-size: 3.75rem; line-height: 1;`|
|`text-7xl`|`font-size: 4.5rem; line-height: 1;`|
|`text-8xl`|`font-size: 6rem; line-height: 1;`|
|`text-9xl`|`font-size: 8rem; line-height: 1;`|

可以在配置中对尺寸进行自定义：

```javascript
module.exports = {
  theme: {
    fontSize: {
      // 仅设置字体大小
      sm: '0.8rem',
      base: '1rem',
      xl: '1.25rem',
      '2xl': '1.563rem',
      '3xl': '1.953rem',
      '4xl': '2.441rem',
      '5xl': '3.052rem',

      // 设置字体大小和行高：[fontSize, lineHeight]
      sm: ['14px', '20px'],
      base: ['16px', '24px'],
      lg: ['20px', '28px'],
      xl: ['24px', '32px'],
    }
  }
}
```

可以在使用中对字体大小自定义，也可以在设置字体大小时同时设置元素行高：

```html
<!-- 自定义字体大小 -->
<p class="text-[22px]"></p>

<!-- 设置字体大小时设置行高 -->
<p class="text-sm/[17px]"></p>
```

### Font Style

|`className`|`css`|说明|
|---|---|---|
|`italic`|`font-style: italic;`|斜体|
|`not-italic`|`font-style: normal;`|正常|

### Font Weight

|`className`|`css`|
|---|---|---|
|`font-thin`|`font-weight: 100;`|
|`font-extralight`|`font-weight: 200;`|
|`font-light`|`font-weight: 300;`|
|`font-normal`|`font-weight: 400;`|
|`font-medium`|`font-weight: 500;`|
|`font-semibold`|`font-weight: 600;`|
|`font-bold`|`font-weight: 700;`|
|`font-extrabold`|`font-weight: 800;`|
|`font-black`|`font-weight: 900;`|

可以在配置中自定义名称：

```javascript
module.exports = {
  theme: {
    fontWeight: {
      hairline: '100',
      extralight: '200',
      light: '300',
      normal: '400',
      medium: '500',
      semibold: '600',
      bold: '700',
      'extra-bold': '800',
      black: '900',
    }
  }
}
```

### Font Variant Numeric

控制数字、分数和序数标记的替代字形的使用。

|`className`|`css`|说明|
|---|---|---|
|`normal-nums`|`font-variant-numeric: normal;`|
|`ordinal`|`font-variant-numeric: ordinal;`|将文本转换为序数表示方式，例如 1st、2nd、3rd 等|
|`slashed-zero`|`font-variant-numeric: slashed-zero;`|将零变为斜杠零，用于避免与大写字母 `O` 混淆|
|`lining-nums`|`font-variant-numeric: lining-nums;`|使用等宽数字|
|`oldstyle-nums`|`font-variant-numeric: oldstyle-nums;`|使用旧式数字|
|`proportional-nums`|`font-variant-numeric: proportional-nums;`|使用比例数字|
|`tabular-nums`|`font-variant-numeric: tabular-nums;`|使用具有统一/表格宽度(而不是成比例)的数字|
|`diagonal-fractions`|`font-variant-numeric: diagonal-fractions;`|使用对角分数实用工具将斜杠分隔的数字替换为普通对角分数|
|`stacked-fractions`|`font-variant-numeric: stacked-fractions;`|使用堆叠分数实用程序将以斜杠分隔的数字替换为常见的堆叠分数|

### Letter Spacing

字间距。

|`className`|`css`|
|---|---|
|`tracking-tighter`|`letter-spacing: -0.05em;`|
|`tracking-tight`|`letter-spacing: -0.025em;`|
|`tracking-normal`|`letter-spacing: 0em;`|
|`tracking-wide`|`letter-spacing: 0.025em;`|
|`tracking-wider`|`letter-spacing: 0.05em;`|
|`tracking-widest`|`letter-spacing: 0.1em;`|

### Line Clamp

对于多行文本展示，使用省略号展示超过规定行数的内容。

|`className`|`css`|
|---|---|
|`line-clamp-1`|`overflow: hidden; display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 1;`|
|`line-clamp-2`|`overflow: hidden; display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 2;`|
|`line-clamp-3`|`overflow: hidden; display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 3;`|
|`line-clamp-4`|`overflow: hidden; display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 4;`|
|`line-clamp-5`|`overflow: hidden; display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 5;`|
|`line-clamp-6`|`overflow: hidden; display: -webkit-box; -webkit-box-orient: vertical; -webkit-line-clamp: 6;`|
|`line-clamp-none`|`overflow: visible; display: block; -webkit-box-orient: horizontal; -webkit-line-clamp: none;`|

### Line Height

|`className`|`css`|
|---|---|
|`leading-{x}`|`line-height: {y}rem;`|
|`leading-none`|`line-height: 1;`|
|`leading-tight`|`line-height: 1.25;`|
|`leading-snug`|`line-height: 1.375;`|
|`leading-normal`|`line-height: 1.5;`|
|`leading-relaxed`|`line-height: 1.625;`|
|`leading-loose`|`line-height: 2;`|

### List Style Image

|`className`|`css`|
|---|---|
|`list-image-none`|`list-style-image: none;`|
|`list-image-[url(...)]`|`list-style-image: url(...);`|

可以在配置中增加名称：

```javascript
module.exports = {
  theme: {
    extend: {
      listStyleImage: {
        checkmark: 'url("/img/checkmark.png")',
      },
    }
  }
}
```

```html
<ul class="list-image-checkmark">
  <!-- ... -->
</ul>
```

### List Style Position

|`className`|`css`|
|---|---|
|`list-inside`|`list-style-position: inside;`|
|`list-outside`|`list-style-position: outside;`|

### List Style Type

|`className`|`css`|说明|
|---|---|---|
|`list-none`|`list-style-type: none;`|
|`list-disc`|`list-style-type: disc;`|点|
|`list-decimal`|`list-style-type: decimal;`|序号|

可以在配置中增加类型：

```javascript
module.exports = {
  theme: {
    listStyleType: {
      none: 'none',
      disc: 'disc',
      decimal: 'decimal',
      square: 'square',
      roman: 'upper-roman',
    }
  }
}
```

### Text Align

|`className`|`css`|
|---|---|
|`text-left`|`text-align: left;`|
|`text-center`|`text-align: center;`|
|`text-right`|`text-align: right;`|
|`text-justify`|`text-align: justify;`|
|`text-start`|`text-align: start;`|
|`text-end`|`text-align: end;`|

### Text Color

|`className`|`css`|
|---|---|
|`text-inherit`|`color: inherit;`|
|`text-current`|`color: currentColor;`|
|`text-transparent`|`color: transparent;`|
|`text-black`|`color: #000;`|
|`text-white`|`color: #fff;`|

设置颜色的透明度：

```html
<p class="text-black/[0.6]">The quick brown fox...</p>
```

设置具体颜色值：

```html
<p class="text-[#50d71e]">The quick brown fox...</p>
```

### Text Decoration

|`className`|`css`|
|---|---|
|`underline`|`text-decoration-line: underline;`|
|`overline`|`text-decoration-line: overline;`|
|`line-through`|`text-decoration-line: line-through;`|
|`no-underline`|`text-decoration-line: none;`|

### Text Decoration Color

|`className`|`css`|
|---|---|
|`decoration-inherit`|`text-decoration-color: inherit;`|
|`decoration-current`|`text-decoration-color: currentColor;`|
|`decoration-transparent`|`text-decoration-color: transparent;`|
|`decoration-black`|`text-decoration-color: #000;`|
|`decoration-white`|`text-decoration-color: #fff;`|

设置划线颜色的透明度：

```html
<p class="decoration-black/[0.6]">The quick brown fox...</p>
```

设置划线的具体颜色值：

```html
<p class="decoration-[#50d71e]">The quick brown fox...</p>
```

### Text Decoration Style

|`className`|`css`|
|---|---|
|`decoration-solid`|`text-decoration-style: solid;`|
|`decoration-double`|`text-decoration-style: double;`|
|`decoration-dotted`|`text-decoration-style: dotted;`|
|`decoration-dashed`|`text-decoration-style: dashed;`|
|`decoration-wavy`|`text-decoration-style: wavy;`|

### Text Decoration Thickness

设置划线的宽度。

|`className`|`css`|说明|
|---|---|---|
|`decoration-auto`|`text-decoration-thickness: auto;`|
|`decoration-from-font`|`text-decoration-thickness: from-font;`|如果字体文件中包含了首选的厚度值，则使用字体文件的厚度值|
|`decoration-0`|`text-decoration-thickness: 0;`|
|`decoration-{x}`|`text-decoration-thickness: {x}px;`|

设置划线的具体宽度：

```html
<p class="decoration-[10px]">The quick brown fox...</p>
```

### Text Underline Offset

设置下划线的偏移量。

|`className`|`css`|
|---|---|
|`underline-offset-auto`|`text-underline-offset: auto;`|
|`underline-offset-0`|`text-underline-offset: 0;`|
|`underline-offset-{x}`|`text-underline-offset: {x}px;`|

### Text Transform

指定如何将元素的文本大写。它可以用于使文本显示为全大写或全小写，也可单独对每一个单词进行操作。

|`className`|`css`|说明|
|---|---|---|
|`uppercase`|`text-transform: uppercase;`|强制所有字符被转换为大写|
|`lowercase`|`text-transform: lowercase;`|强制所有字符被转换为小写|
|`capitalize`|`text-transform: capitalize;`|强制每个单词的首字母转换为大写。其他的字符保留不变（保留原始大小写）|
|`normal-case`|`text-transform: none;`|

### Text Overflow

|`className`|`css`|
|---|---|
|`truncate`|`overflow: hidden; text-overflow: ellipsis; white-space: nowrap;`|
|`text-ellipsis`|`text-overflow: ellipsis;`|
|`text-clip`|`text-overflow: clip;`|

### Text Indent

|`className`|`css`|
|---|---|
|`indent-0`|`text-indent: 0px;`|
|`indent-px`|`text-indent: 1px;`|
|`indent-{x}`|`text-indent: {y}rem;`|

### Vertical Align

|`className`|`css`|
|---|---|
|`align-baseline`|`vertical-align: baseline;`|
|`align-top`|`vertical-align: top;`|
|`align-middle`|`vertical-align: middle;`|
|`align-bottom`|`vertical-align: bottom;`|
|`align-text-top`|`vertical-align: text-top;`|
|`align-text-bottom`|`vertical-align: text-bottom;`|
|`align-sub`|`vertical-align: sub;`|
|`align-super`|`vertical-align: super;`|

### White Space

|`className`|`css`|
|---|---|
|`whitespace-normal`|`white-space: normal;`|
|`whitespace-nowrap`|`white-space: nowrap;`|
|`whitespace-pre`|`white-space: pre;`|
|`whitespace-pre-line`|`white-space: pre-line;`|
|`whitespace-pre-wrap`|`white-space: pre-wrap;`|
|`whitespace-break-spaces`|`white-space: break-spaces;`|

### Word Break

|`className`|`css`|
|---|---|
|`break-normal`|`overflow-wrap: normal; word-break: normal;`|
|`break-words`|`word-break: break-word;`|
|`break-all`|`word-break: break-all;`|
|`break-keep`|`word-break: keep-all;`|
