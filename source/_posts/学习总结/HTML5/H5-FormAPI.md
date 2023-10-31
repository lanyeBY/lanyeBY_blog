---
title: H5-FormAPI
date: 2018-04-30 13:19
date: 2018-05-02 14:13
tags: HTML5
catetory: 学习总结
---
#### HTML5 Forms

浏览器 | 支持情况
---|---
Chrome | 5.0x版本开始部分支持，61及之后的版本完全支持
FireFox | 4.0版本直到现在的最新版本都只是部分支持
Internet Explorer | 10版本开始部分支持
Opera | 10.1到12.1版本完全支持，12.1版本之后部分支持
Safari | 4.0x版本开始部分支持

若浏览其不支持新的输入性控件，会把它们呈现在简单的文本输入框(平滑降级)。

#### 输入型控件目录

类型 | 用途
---|---
`tel` | 电话号码
`email` | 电子邮件地址文本框
`url` | 网页的URL
`search` | 用于搜索引擎，比如在站点顶部显示的搜索框
`range` | 特定值范围内的数值选择器，典型的显示方式是滑动条
`number` | 只能包含数值的文本框
`color` | 颜色选择器，基于调色盘或者取色板进行选择
`datetime` | 显示完整的日期和时间，包括时区
`datetime-local` | 显示日期和时间，不含时区
`time` | 不含时区的时间选择器和指示器
`date` | 日期选择器
`week` | 某年中的周选择器
`month` | 某年中的月选择器

特殊的类型能够得到专用的输入性控件。
尽管目前浏览器的支持情况有限，我们还是可以在Web应用程序中使用这些类型，因为浏览器会针对这些类型进行优化，或者干脆将其降级为普通文本输入框。<br>
设计 `range` 类型的目的是为了让用户在指定的数值范围中进行选择。通过创建 `range` 空间并为其指定 min 和 `max` 值，开发人员能够在页面上显示出一个数值范围选择器，用户只能选择指定范围内的数值。遗憾的是，浏览器没有在滑动条或数值选择器上显示刻度对应的数值大小。但解决这个问题也很简单，只需增加简单的脚本，如下示例：

```html
<script type="text/javascript">
  function showValue(newVal){
    document.getElementById("ageDisplay").innerHTML = newVal;
  }
</script>

<label for="age">Age</label>
<input id="age" type="range" min="18" max="120" value="18" onchange="showValue(this.value)">
<span id="ageDiaplay">18</span>
```

#### 新的表单特性和函数
不管浏览器是否支持新的表单特性，市面上的浏览器在不支持这些特性时，会直接忽略它们，而不是报错。
- `placeholder` 特性向用户显示描述性说明或者提示信息，具体的显示方式依浏览器自身而定。
- `autocomplate` 特性能够知晓是否应该保存输入值以备将来使用。有以下三种行为：`on` (该字段无需受到保护，值可以被保存和恢复) / `off` (该字段需要受到保护，值不可以被保存) / `unspecified` (包含form的默认设置。如果没有被包含在表单中或没有指定值，则行为与设置为on时相同)
- `autofocus` 特性可以指定某个表单元素获得输入焦点。每个页面上只允许出现一个 `autofocus` 特性。如果设置了多个 `autofocus` 特性，则相当于未指定此行为。使该特性生效不需要专门将其值设为 `true`。
- `list` 特性和 `datalist` 元素
  通过组合使用 `list` 特性和 `datalist` 元素，开发人员能够为某个输入型空间构造一张选值列表，其使用方法如下：
  1. 创建 `id` 特性值唯一的 `datelist` 元素，该元素可插入文档的任意位置。
  2. 添加若干 `option` 元素作为 `datalist` 元素的子元素，它们表示某空间推荐选值的全集。例如，`datalist` 元素若表示电子邮件列表，那么每个被选的 `e-mail` 地址都应该放入 `option` 元素中，代码如下：

      ```html
      <datalist id="contactList">
        <option value="609892858@qq.com" label="Lanye">
        <option value="450786602@qq.com" label="Lily">
      </datalist>
      ```

      其中 `value` 值表示的是选项，`label` 表示的是对该选项的描述，是辅助值。<br>
      需要注意的是，不同的浏览器对于这个值的表现不同：
      - 在谷歌浏览器 `Chrome` 中，`value` 和 `label` 能够发挥作用，将鼠标移到显示出来的文本框时右边会有一个向下的小箭头；
      - 但是在 `FireFox` 中并不支持 `value`，而是只使用 `label` 作为选项值，并且显示出来的文本框需要双击才能显示列表。

      另外，如果 list 特性所在的 input 的类型为 url 时，其 datalist 的选项值也必须是 **合法url**，即必须包含" `http://` "
  3. 将input元素的list特性值设为datalist元素的id值，可以实现二者的关联。

      ```html
        <input type="email" id="contacts" list="contactList">
      ```

- `min` 和 `max` 特性可以将 `range` 输入框的数值范围限定在最低值和最高值之间。这两个特性可以只设置一个，也可以设置两个，也可以都不设置，输入型控件会根据设置的参数对值范围做出相应调整。
- `step` 特性能够制定输入递增或递减的粒度。例如将 `range` 控件的 `step` 特性设置为 `5`:

  ```html
    <input type="range" min="0" max="100" step="5" value="0">
  ```

  对于 `range` 控件，`step` 默认值为 `1`。为了配合 `step` 特性，`HTML5` 引入了 `stepUp` 和 `stepDown` 两个函数对其进行控制。两个函数的作用分别是根据 `step` 特性的值来增加或减少控件的值。
- `valueAsNumber` 函数的作用是完成控件值类型在文本与数值间的相互转换。它既是 `getter` 函数又是 `setter` 函数。作为 `getter` 函数调用时，`valueAsNumber `函数将文本类型转换成 `number` 类型，以方便计算。如果转换失败，则会返回 `NaN` 值。
  `valueAsNumber` 也可用于为输入型控件设置 `number` 值，但需要注意的是，输入的数值必须同时满足 `min`、`max` 和 `step` 要求，否则会抛出错误。
- `required` 特性表示该输入型控件为必填项，否则无法提交表单。`required` 特性时最简单的一种表单验证方式。

#### 表单验证
##### `ValidityState` 对象
该对象包含了对所有八种验证状态的引用以及最终验证结果。

```javascript
//获取对象
var valCheck = document.myForm.myInput.validity;

//调用方式
valCheck.valid;
```

上面的代码执行完毕，我们会得到一个布尔值，它表示表单控件是否已通过了所有的验证约束条件。如果所有八个约束条件都通过了，`valid` 特性就是 `true`，否则，只要有一项约束没通过，`valid` 标志都是 `false`。

`ValidityState` 对象是一个实时更新的对象。获得某表单元素的 `ValidityState` 对象后，当表单元素内容发生变化时，你可以通过它来获得更新后的检测结果。

任何表单元素都有八个可能的验证约束条件。下面一一介绍：

###### 1. `valueMissing`

**目的**：确保表单控件中的值已填写。
**用法**：在表单控件中将 `required` 特性设置为 `true`。

```html
<input type="text" name="myText" required>
```

**详细说明**：如果表单控件设置了 `required` 特性，那么在用户填写或者通过代码调用方式填值之前，控件会一直处于无效状态。例如，空的文本输入框无法通过必填检查，除非在其中输入任意文本。输入值为空时， `valueMissing` 会返回 `true` 。

###### 2. `typeMismatch`

**目的**：保证控件值与预期类型相匹配(如 `number`、`email`、`URL` 等)。
**用法**：指定表单控件的 `type` 特性值。

```html
  <input type="email" name="myEmail">
```

**详细说明**：特殊的表单控件类型不只是用来定制手机键盘，如果浏览器能够识别出来表单控件中的输入不符合对应的类型规则，比如 `email` 地址中没有 `@` 符号，或者 `number` 型控件的输入值不是有效的数字，那么浏览器就会把这个控件标记出来以提示类型不匹配。无论哪种出错情况，`typeMismatch` 将返回 `true`。

###### 3. `patternMismatch`

**目的**：根据表单控件上设置的格式规则验证输入是否为有效格式。
**用法**：在表单控件上设置 `pattern` 特性，井赋予适当的匹配规则。

```html
<input type="text" name="creditcardnumber" pattern="[0-9]{16}" title="A credit card number is 16 digits with no spaces or dashes">
```

**详细说明**：pattern 特性向开发人员提供了一种强大而灵活的方式来为表单的控件值设定正则表达式验证机制。当为控件设置了 `pattern` 特性后，只要输入控件的值不符合模式规则，`patternMismatch` 就会返回 `true` 值。从引导用户和技术参考两方面考虑，你应该在包含 `pattern` 特性的表 单控件中设置 `title` 特性以说明规则的作用。

###### 4. `tooLong`

**目的**：避免输入值包含过多字符。
**用法**：在表单控件上设置 `maxLength` 特性。

```html
<input type="text" name="limitedText" maxLength="140">
```

**详细说明**：如果输入值的长度超过 `maxLength`，`tooLong` 特性会返回 `true`。虽然表单控件通常会在用户输入时限制最大长度，但在有些情况下，如通过程序设置，还是会超出最大值。

###### 5. `rangeUnderflow`

**目的**：限制数值型控件的最小值。
**用法**：为表单控件设置 `min` 特性，并赋予允许的最小值。

```html
<input type="range" name="ageCheck" min="18">
```

**详细说明**：在需要做数值范围检查的表单控件中，数值很可能会暂时低于设置的下限。此时，`ValidityState` 的 `rangeUnderflow` 特性将返回 `true`。

###### 6. `rangeOverflow`

**目的**：限制数值型控件的最大值。
**用法**：为表单控件设置 `max` 特性，并赋予允许的最大值。

```html
<input type="range" name="kidAgeCheck" max="12">
```

**详细说明**：与 `rangeUnderflow` 类似，如果一个表单控件的值比 `max` 更大，特性将返回 `true`。

###### 7. `stepMismatch`

**目的**：确保输入值符合 `min`、`max` 及 `step` 即设置。
**用法**：为表单控件设置 `step` 特性，指定数值的增量。

```html
<input type="range" name="confidenceLevel" min="0" max="100" step="5">
```

**详细说明**：此约束条件用来保证数值符合 `min`、`max` 和 `step` 的要求。换句话说，当前值必须是最小值与 `step` 特性值的倍数之和。例如，范围从 `0` 到 `100`，`step` 特性值为 `5` ，此时就不允许出现 `17`，否则 `stepMismatch` 返回 `true` 值。

###### 8. `customError`

**目的**：处理应用代码明确设置及计算产生的错误。
**用法**：调用 `setCustomValidity(message)` 将表单控件置于 `customError` 状态。

```javascript
passwordConfirmationField.setCustomValidity("Password values do not match.");
```

**详细说明**：浏览器内置的验证机制不适用时，需要显示自定义验证错误信息。当输入值不符合语义规则时，应用程序代码应设置这些自定义验证消息。
  自定义验证消息的典型用例是验证控件中的值是否一致。只要定制了验证消息，控件就会处于无效状态，并且 `customError` 返回 `true`。要记住**最后要清除错误**！只需在控件上调用 `setCustomValidity("")` 即可。

##### `checkValidity` 函数
`checkValidity` 函数在任何时间对表单进行验证，无论是否有用户输入。

##### 验证反馈
所有未通过验证的表单都会接受到一个 `invalid` 事件。`invalid` 事件可以被忽略、观察、甚至取消。