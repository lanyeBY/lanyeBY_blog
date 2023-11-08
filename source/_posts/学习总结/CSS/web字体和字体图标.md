---
title: 为页面增加新web字体
date: 2018-05-09 11:05
tags: CSS
catetory: 学习总结
---

常见字体类型有：
- "`woff`": Web开放字体格式（目前得到较多浏览器支持）
- "`ttf`": `trueType` 字体

在线字体和字体图标下载网址：
[iconfont](http://iconfont.cn)
注意：从上面下载下来的文件默认是zip文件，但需要自己增加后缀名

步骤如下：
1. 使用 `@font-face` 声明字体：

```css
@font-face {
  font-family: "字体名";
  src: url('webfont.eot');/* IE9 */
  src: url('webfont.eot?#iefix') format('embedded-opentyoe'),	/* IE6~8 */
       url('webfont.woff') format('woff'),	/* Chrome、firefox */
       url('webfont.ttf') format('ttf'),	/* chrome、firefox、opera、safari、Android、ios */
       url('webfont.svg#webfont') format('svg');	/* ios */
}
```

2. 使用 `font-family` 定义使用自定义字体。自定义的字体名要加双引号。可为字体加上对应的样式。

```css
element {
  /* 这里最好再加一个浏览器一般会有的字体，以防止浏览器不能够识别自定义字体 */
  font-family: "自定义字体", sans-serif;
}
```

**字体图标**：既是一个字体也是一个图标，可以对其修改颜色、大小；每一个键盘对应不同的字体图标。
由于直接使用的时候缺少直观性，可以通过自定义类，并对其构建虚函数 `::before` 或 `::after`，具体代码如下：

```css
.smile {
  content: "\e641";	/* 下载下来直接调用时的语句一般前面还会有一些特殊符号"&“、"#"之类，但在style样式设置中，只需要将这些特殊符号去掉并用"\"代替 */
  color: red;
  font-size: 50px;
}
```
