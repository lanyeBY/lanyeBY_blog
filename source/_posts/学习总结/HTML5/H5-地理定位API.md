---
title: H5地理定位API
date: 2018-05-03 12:36
update: 2018-08-25 16:01
tags: HTML5
catetory: 学习总结
---

```html
<div id="demo" class="de"></div>
<script>
  var x = document.getElementById("demo");
  function getLocation () {
    //能力测试
    if (navigator.geolocation) {
      /*navigator.geolocation.getCurrentPosition(success, error, option);
       * success: 获取地理信息成功之后的回调
       *   error: 获取地理信息失败之后的回调
       *  option: 获取当前地理信息的方式
       *     enableHighAccuracy: true/false: 是否使用高精度
       *     timeout: 可以设置浏览器重新获取地理信息的时间间隔，单位是ms
       **/
      navigator.geolocation.getCurrentPosition(showPosition, showError, {
        enableHighAccuracy: true,
        timeout: 5000
      });
    } else {
      x.innerHTML = "您的浏览器暂不支持地理定位功能."
    }
  }
  //成功获取定位之后的回调
  function showPosition (position) {
    /*position.coords.latitude : 纬度
    * position.coords.longitude: 经度
    * position.coords.accuracy : 精度
    * position.coords.altitude : 海拔高度
    * */
    x.innerHTML = "纬度:" + position.coords.latitude +"<br>经度:" + position.coords.longitude;
  }
  //获取定位失败之后的回调
  function showError (error) {
    switch (error.code) {
      case error.PERMISSION_DENIED:
        x.innerHTML = "您已禁止共享位置。";
        break;
      case error.POSITION_UNAVAILABLE:
        x.innerHTML = "定位信息不可用";
        break;
      case error.TIMEOUT:
        x.innerHTML = "请求超时";
        break;
      case error.UNKNOWN_ERROR:
        x.innerHTML = "发生了未知错误";
        break;
    }
  }
</script>
```