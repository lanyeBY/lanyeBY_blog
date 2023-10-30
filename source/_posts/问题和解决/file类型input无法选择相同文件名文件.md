---
title: 关于file类型的input无法选择相同文件名文件的问题
date: 2023-10-30 11:08:55
tags: File
catetory: 问题和解决
---

`input` 标签的 `change` 事件监听的是所选择的的文件的文件名是否不相同。
如果相同的话事件对应的函数就不会触发。

目前遇到了一个项目是 `change` 事件触发然后进行文件上传，而因为这个问题，使得用户没有办法选择相同文件名（可能文件内容不相同）的文件进行上传。
于是就想到了在 `change` 事件触发之后上传文件的操作结束就把 `file` ，也就是 `input` 的 `value` 清空，如此一来就能保证 `change` 事件始终可以被触发。

但是在 `<input type="file" :value="fileName" @change="uploadFile"/>` 中却发现 `value` 绑定的值在选择了一个文件之后并没有改变，始终是初始值（我设置的为空字符串）。而使用 `v-model` 的时候则会出现提示 `type=“file”` 的情况下不能使用 `v-model` 。

上网搜索答案之后终于找到绑定 `value` 的方法：

```html
<input type="file" ref="clearFile" @change="uploadFile"/>

<!-- ... -->

<script>
  // ...
  uploadFile: function () {
    // ...
    this.$ref.clearFile.value = '';
    // ...
  }
  // ...
</script>
```
