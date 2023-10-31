---
title: H5-CanvasAPI
date: 2018-04-26 21:17
tags: HTML5
catetory: 学习总结
---

### `canvas` 是什么
在网页上使用 `canvas` 元素时，它会创建一块矩形区域。默认情况下该矩形区域宽为 `300px`，高为 `150px`，但也可以自定义具体的大小或者设置 `canvas` 元素的其他特性。
在页面中加入了 `canvas` 元素后，我们便可以通过 **`JavaScript`** 来自由地控制它————可以在其中添加图片、线条以及文字，亦可以在里面绘图，甚至还可以加入高级动画。
### `canvas` 坐标
`canvas` 中的坐标是从左上角开始的，`x` 轴沿着水平方向(按像素)**向右**延伸，`y` 轴沿垂直方向**向下**延伸。
### 替代内容
访问页面的时候，如果浏览器不支持 `canvas` 元素，或者不支持 `HTML5 Canvas API` 中的某些特性，那么开发人员最好提供一份替代代码。一如，开发人员可以通过一张替代图片或者一些说明性的文字告诉访问者，使用最新的浏览器可以获得更佳的浏览效果。下面的代码展示了如何在 `canvas` 中指定替代文本，当浏览器不支持 `canvas` 的时候会显示这些替代内容。

```html
<canvas>
  Update your browser to enjoy canvas!
</canvas>
```

### 浏览器对 `HTML5 Canvas` 的支持

浏览器 | 支持情况
---|---
Chrome | 支持
Firefox | 支持
Internet Explorer | IE9及以上版本支持
Opera | 支持
Safari | 支持

在所有浏览器中，`IE9` 以下版本不支持 `HTML5 Canvas`。如果需要在Internet Explorer中使用 `canvas`，可以选择使用名为 [explorercanvas](http://code.google.com/p/explorercanvas) 的开源项目。使用 `explorercanvas` 时，需要先判断当前浏览器是否是IE，如果是则在页面中嵌入 `script` 标签来加载 `explorercanvas`。写法如下：

```html
<head>
<!--[if IE]><script src="excanvas.js"></script><![endif]-->
</head>
```

### 检测浏览器支持情况
下面的代码是检测浏览器支持情况的一种方法：

```javascript
try {
  document.createElement("canvas").getContext("2d");
  document.getElementById("support").innerHTML = "HTML5 Canvas is supported in your browser.";
} catch(e) {
  document.getElementById("support").innerHTML = "HTML5 Canvas is not supported in your browser.";
}
```

页面中预先放入了 `ID` 为 `support` 的元素，通过以适当的信息更新该元素的内容，可以反映出浏览器的支持情况。

### 在页面中加入 `canvas`
对于任何 `canvas` 对象来说，`ID` 特性都是特别重要的，因为对 `canvas` 元素的所有操作都是通过脚本代码控制的，没有 `ID` 的话，想要找到要操作的 `canvas` 元素会很难。
以下代码是在 `canvas` 画布中画出一条对角线：

```javascript
function drawDiagonal () {
  //取得canvas元素及其绘画上下文
  var canvas = document.getElementById('diagonal');
  var context = canvas.getContext('2d');
  
  //用绝对坐标来创建一条路径
  context.beginPath();
  context.moveTo(70,140);
  context.lineTo(140,70);
  
  //将这条线绘制到canvas上
  context.stroke();
}

window.addEventListener("load", drawDiagonal, true);
```

上面的代码中，首先通过引用特定的 `canvasID` 值来获取对 `canvas` 对象的访问权。接着定义一个 `context` 变量，调用 `canvas` 对象的 `getContext()` 方法，并传入希望使用的 `canvas` 类型。代码清单中通过传入“ `2d` ”来获取一个二维上下文。<br>
接下来，基于这个上下文执行画线的操作。在代码清单中，调用了三个方法———— `beginPath()`、`moveTo()` 和 `lineTo()`，传入了这条线的起点和终点的坐标。
方法 `moveTo()` 和 `lineTo()` 实际上并不画线，而是在结束 `canvas` 操作的时候，通过调用 `context.stroke()` 方法完成线条的绘制。<br>
从上面的代码中可以看出，`canvas` 中所有的操作都是通过上下文对象来完成的。在以后的 `canvas` 编程中也一样，因为所有涉及视觉输出效果的功能都只能用过上下文对象而不是画布对象来使用。
同时，对上下文的很多操作都不会立即反映到页面上。`beginPath()`、`moveTo()` 以及 `lineTo()` 这些函数都不会直接修改 `canvas` 的展示结果。`canvas` 中很多用于设置样式和外观的函数也同样不会直接修改显示结果。只有当对路径应用绘制(`stroke()`)或填充(`fill()`)方法时，结果才会显示出来。否则，只有在显示图像、显示文本或者绘制、填充和清除矩形框的时候，`canvas` 才会马上更新。
### 变换
#### `translate()`:
##### 语法

```javascript
translate(x, y);
```

`x`、`y`：平移变换之后的原点坐标<br>
在进行变换之前，需要保存尚未修改的 `context`：`context.save()`，这样即使进行了绘制和变换操作，也可以恢复到初始状态。如果不保存，那么在进行了平移和缩放等操作以后，其影响会带到后续的操作中。
### 路径
`beginPath()` 表示要开始绘制路径了。
不论开始绘制何种图形，第一个需要调用的就是 `beginPath()`。这个简单的函数不带任何参数，只用于通知 `canvas` 将要开始绘制一个新的图形了。对于 `canvas` 来说，`beginPath()` 函数最大的用处就是 `canvas` 需要据此来计算图形的内部和外部范围，以便完成后续的描边和填充。<br>
`closePath()` 函数的行为和 `lineTo()` 很像。
`closePath()` 会将路径的起始坐标自动作为目标坐标，然后进行连线。
`closePath()` 还会通过 `canvas` 当前绘制的图形已经闭合或者形成了完全封闭的区域，这对将来的填充和描边都非常有用。

## 带有长跑跑道的树林

```javascript
function createCanopyPath (context) {
  //绘制树冠
  context.beginPath();
  
  context.moveTo(-25, -50);
  context.lineTo(-10, -80);
  context.lineTo(-20, -80);
  context.lineTo(-5, -110);
  context.lineTo(-15, -110);

  //树的顶点
  context.lineTo(0, -140);

  context.lineTo(15, -110);
  context.lineTo(5, -110);
  context.lineTo(20, -80);
  context.lineTo(10, -80);
  context.lineTo(25, -50);

  //连接起点，闭合路径
  context.closePath();
}
function drawTrails () {
  var canvas = document.getElementById("diag");
  var context = canvas.getContext("2d");

  context.save();
  context.translate(130, 250);

  //创建表现树冠的路径
  createCanopyPath(context);

  //绘制当前路径
  context.stroke();
  context.restore();
}
```

### 描边样式

```javascript
//加宽线条
context.lineWidth = 4;

//让拐角变得更圆滑
context.lineJoin = "round";

//将颜色改成棕色
context.strokeStyle = "#663300";

//最后，绘制树冠
context.stroke();
```

### 填充样式

```javascript
//将填充色设置为绿色并填充树冠
context.fillStyle = "#339900";
context.fill();
```

由于我们是先描边后填充，因此填充会覆盖一部分描边路径。我们示例中的路径是 `4px` 宽，这个宽度是沿路径线居中对齐的，而填充是把路径轮廓内部所有像素全部天聪，所以会覆盖描边路径的一半。如果希望看到完整的描边路径，可以在绘制路径（调用 `context.stroke()` ）之前填充（调用 `context.fill()` ）。

### 填充矩形区域

```javascript
//将填充色设为棕色
context.fillStyle = "#663300";

//填充用作树干的矩形区域
context.fillRect(-5, -50, 10, 50);
```

调用 `fillRect` 并设置 `x`, `y` 两个位置参数和宽度、高度两个大小参数，随后，`Canvas` 会马上使用当前的样式进行填充。

### 绘制曲线

```javascript
//保存canvas的状态并绘制路径
context.save();

context.translate(-10, 350);
context.beginPath();

//第一条曲线向右上方弯曲
context.moveTo(0, 0);
context.quadraticCurveTo(170, -50, 260, -190);

//第二条向右下方弯曲
context.quadraticCurveTo(310, -250, 410, -250);

//使用棕色的粗线条来绘制路径
context.strokeStyle = "#663300";
context.lineWidth = 40;
context.stroke();

//恢复之前的canvas状态
context.restore();
```

`quadrticCurveTo()` 函数绘制曲线的起点是当前坐标，带有两组 `(x,y)` 参数。第二组是指曲线的终点。第一组代表控制点。所谓的控制点位于曲线的旁边(不是曲线之上)，其作用相当于对曲线产生一个拉力。

### 在canvas中插入图片
由于图片增加了 `canvas` 操作的复杂度：必须等到图片完全加载后才能对其进行操作。浏览器通常会在页面脚本执行的同时执行的同时异步加载图片。如果试图在图片未完全加载之前就将其呈现到 `canvas` 上，那么 `canvas` 将不会显示任何图片。<br>
为保证在呈现之前图片已完全加载，我们提供了回调，即仅当图像加载完成时才执行后续代码，代码如下所示：

```javascript
//插入替换树干的图片
var bark = new Image();
bark.src = "bark.jpg";

//图片加载完成后，将其显示在canvas上
bark.onload = function(){
  drawTrails();
  
  //将背景图案填充作为树干的矩形
  context.drawImage(bark, -5, -50, 10, 50);
}
```

在 `drawImage()` 函数中，除了图片本身外，还指定了`x`、`y`、`width` 和 `height` 参数。

### 渐变

```javascript
//创建用作树干纹理的三阶水平渐变
var trunkGradient = context.createLinearGradient(-5, -50, 5, -50);  // 注意这里后两个参数是结束点坐标而非渐变区宽高

//树干左侧边缘是一般程度的棕色
trunkGradient.addColorStop(0, "#663300");

//树干中间偏左的位置颜色要淡一些
trunkGradient.addColorStop(0.4, "#996600");

//树干右侧边缘的颜色要深一些
trunkGradient.addColorStop(1, "#552200");

//使用渐变色填充树干
context.fillStyle = trunkGradient;
context.fillRect(-5, -50, 10, 50);

//接下来，创建垂直渐变，以用作树冠在树干上的投影
var canopyShadow = context.createLinearGradient(0, -50, 0, 0);

//投影渐变的起点是透明度设为50%的黑色
canopyShadow.addColorStop(0, "rgba(0, 0, 0, 0.5)");

//方向垂直向下，渐变色在很短的距离内迅速变为完全透明
canopyShadow.addColorStop(0.2, "rgba(0, 0, 0, 0)");

//在树干上填充投影渐变
context.fillStyle = canopyShadow;
context.fillRect(-5, -50, 10, 50);
```

要设置显示哪种颜色，在渐变对象上使用 `addColorStop()` 函数即可。这个函数允许指定两个参数：颜色和偏移量。颜色参数是指开发人员希望在偏移位置描边或填充时所使用的颜色。偏移量是一个 `0.0` 到 `1.0` 之间的数值，代表沿着渐变线渐变的距离有多远。<br>
除了上面所使用的线性渐变以外，`HTML5 Canvas API` 还支持放射性渐变。所谓放射性渐变就是颜色会介于两个指定圆间的锥形区域平滑变化。放射性渐变和线性渐变使用的颜色终止点是一样的，不过参数有所不同：

```javascript
createRadiaGradient(x0, y0, r0, x1, y1, r1)
```

代码中，前三个参数代表以 `(x0,y0)` 为圆心，`r0` 为半径的圆；后三个参数代表以 `(x1,y1)` 为圆心，`r1` 为半径的另一个圆。

### 背景图

```javascript
//加载砾石背景
var gravel = new Image();
gravel.src = "gravel.jpg";
gravel.onload = function () {
  drawTrails();
}
//用背景图替代棕色粗线条
context.strokeStyle = context.createPattern(gravel, "repeat");
context.lineWidth = 20;
context.stroke();
```

我们这次先设置了 `context` 上的 `strokeStyle` 属性，把调用 `context.createPattern()` 的返回值赋给该属性。
`context.createPattern()` 的第二个参数是重复性标记，可选值有：`repeat`、`repeat-x`、`repeat-y`、`no-repeat`。

### 缩放 `canvas` 对象

```javascript
//在(130,250)的位置绘制第一棵树
context.save();
context.translate(130,250);
drawTree(context);
context.restore();

//在(260,500)的位置绘制第二棵树
context.save();
context.translate(260,500);

//将第二棵树的宽高分别放大至原来的2倍
context.scale(2,2);
drawTree(context);
context.restore();
```

`scale` 函数带有两个参数来分别代表在 `x`，`y` 两个维度的值。每个参数在 `canvas` 显示图像的时候，向其传递在本方向轴上图像要放大(或者缩小)的量。<br>
**注意**：示例中演示了为什么要在原点执行图形和路径的变换操作，执行完后在统一平移。理由就是缩放和旋转等变换操作都是针对原点进行的。
如果对一个不再原点的图形进行旋转变换，那么 `rotate` 变换函数会将图形绕着原点旋转而不是在原地旋转。与之类似，如果进行缩放操作时没有将图形放置到合适的坐标上，那么所有路径坐标都会被同时缩放。取决于缩放比例的大小，新的坐标可能会全部超出 `canvas` 范围..

### `Canvas` 变换
#### transform
允许缩放、旋转、移动并倾斜选中的图形
相当于由 `rotate()`、`scale()`、`translate()` 合并在一起。

##### 语法

```javascript
transform(a, b, c, d, e, f)
```

- `a`：水平缩放绘图
- `b`：水平倾斜绘图
- `c`：垂直倾斜绘图
- `d`：垂直缩放绘图
- `e`：水平移动绘图
- `f`：垂直移动绘图

```javascript
// 保存canvas的当前状态
context.save();

// X 值随着 Y 值的增加而增加，在Y轴方向，将阴影的高度压缩为原来的60%，借助拉伸变换，可以创建一棵用作阴影的倾斜的树
context.transform(1, 0, -0.5, 0.6, 0, 0);

// 使用透明度为 20% 的黑色填充树干
context.fillStyle = 'rgba(0, 0, 0, 0.2)';
context.fillRect(-5, -50, 10, 50);

// 使用已有的阴影效果重新绘制树
createCanopyPath(context);
context.fill();

// 恢复之前的canvas状态
context.restore();
```

注意，剪裁过的“阴影”树先被显示出来，这样一来，真正的树就会按照 `Z` 轴顺序(`canvas` 中对象的重叠顺序)显示在阴影的上面。(即先画阴影再画树)

### `Canvas` 文本
操作 `canvas` 文本的方式与操作其他路径对象的方式相同：可以描绘文本轮廓和填充文本内部；同时，所有能够应用于其他图形的变换和样式都能用于文本。
`Context` 对象的文本绘制功能由两个函数组成：

```javascript
fillText(text, x, y, maxwidth);
strokeText(text, x, y, maxwidth);
```
 
`maxwidth` 是可选的，用于限制字体的大小，它将文字强制收缩到指定尺寸。

属性 | 值 | 备注
---|---|---
font | CSS字体字符串 | 
textAlign | start、end、left、right、center | 默认是start
textBaseline | top、handing、middle、alphabetic、bottom | 默认是alphabetic


```javascript
// 在 canvas 上绘制标题文本
context.save();

// 字号为 60px，字体为 impact
context.font = '60px impact';

// 将文本填充为棕色
context.fillStyle = '#996600';
// 将文本设为居中对齐
context.textAlign = 'center';

// 在 canvas 顶部中央的位置以大字体的样式显示文本
context.fillText('Merry Christmas!', 200, 60, 400);
context.restore();
```

### 应用阴影

```javascript
// 设置文字阴影的颜色为黑色，透明度为 20%
context.shadowColor = 'rgba(0, 0, 0, 0.2)';

// 将阴影向右移动 15px，向上移动 10px
context.shadowOffsetX = 15;
context.shadowOffsetY = -10;

// 轻微模糊阴影
context.shadowBlur = 2;
```

最后效果图：
![image](https://images2015.cnblogs.com/blog/621698/201512/621698-20151205224501127-1073324950.png)