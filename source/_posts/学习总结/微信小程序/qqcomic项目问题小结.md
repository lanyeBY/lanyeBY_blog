---
title: qqcomic项目问题小结
date: 2018-07-13 16:20
tags: 微信小程序 项目问题
catetory: 学习总结
---

#### 1. 子组件接受父组件的数据有两种形式：

- 使用属性接收

*子组件中在js文件中设置属性接收*：

```json
  ...
  properties: {
      data: Object
  },
  ...
```

*子组件中在wxml文件中使用数据*：

```html
  <view class="video">
      <!-- video封面 -->
      <view class="video__cover">
          <image src="{{data.icon}}" class="cover__img" lazy-load mode="aspectFill" />
          <view class="hot_num">
              <icon class="icon_fire"></icon>
              <text class="text_hot_num">{{data.displayhot}}</text>
          </view>
      </view>
      <!-- video名字 -->
      <view class="video__name">{{data.name || ""}}</view>
      <!-- video更新情況 -->
      <view class="video__update">更新至{{data.update || ""}}话</view>
  </view>
```

- 在子组件中使用 `<slot></slot>` 标签用于父组件在引用子组件时插入需要的内容

*子组件的wxml文件中*：

```html
  <view class="wrapper">
    <view>这里是组件的内部节点</view>
    <slot></slot>
  </view>
```

*引用子组件的wxml文件中*：

```html
  <view>
    <component-tag-name>
      <!-- 这部分内容将被放置在组件 <slot> 的位置上 -->
      <view>这里是插入到组件slot中的内容</view>
    </component-tag-name>
  </view>
```

如果需要插入多个内容，需要在子组件的js文件中设置:

```javascript
  Component({
    options: {
      multipleSlots: true // 在组件定义时的选项中启用多slot支持
    },
    properties: { /* ... */ },
    methods: { /* ... */ }
  })
```

此时，可以在这个组件的wxml中使用多个slot，以不同的 name 来区分。<br />
*子组件的wxml文件中*：

```html
  <view class="wrapper">
    <slot name="before"></slot>
    <view>这里是组件的内部细节</view>
    <slot name="after"></slot>
  </view>
```

*引用子组件的wxml文件中*：

```html
  <view>
    <component-tag-name>
      <!-- 这部分内容将被放置在组件 <slot name="before"> 的位置上 -->
      <view slot="before">这里是插入到组件slot name="before"中的内容</view>
      <!-- 这部分内容将被放置在组件 <slot name="after"> 的位置上 -->
      <view slot="after">这里是插入到组件slot name="after"中的内容</view>
    </component-tag-name>
  </view>
```

#### 2. 使用到的变量需要默认赋值

我们引用函数外的全局变量时，可能是这样使用：`this.data.column.title`,这里，column是我们自己定义的变量，要使用这条语句中的`title`属性时，需要外部传入包含有'title'属性的一个对象，于是就有可能出现一个问题：万一外部并没有传入这个属性，到时候界面展示的时候就会因为这个变量不存在(`undefined`)而报错，导致整个界面变白。<br>
因此我们需要函数引用前对其进行默认赋值，例子如下：

```javascript
  tapMore: function() {
      let { data = {} } = this.data;
      let { column = {} } = data.column;
      let { url = '' } = column.url;
      wx.navigateTo({
          url: url
      });
  }
```

这里使用的是ES6的语法，如果是旧的版本，则如下：

```javascript
  tapMore: function() {
      let data = this.data || {};
      let column = data.column || {};
      let url = column.url || '';
      wx.navigateTo({
          url: url
      });
  }
```

另外，微信小程序中js文件中的data对象里面的数据（不论类型）都必须要给一个初始值，否则就会报错：

```
  columnTitle1: '',     //正确
  columnTitle2        //报错
```

