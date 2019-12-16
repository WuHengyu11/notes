[TOC]
# Jquery+Ajax
## jQuery基础
### 1.获取jQuery
>1.官网下载
>https://jquery.com/
>2.npm 下载
>npm install jquery
>3.CDN方式
>
>```
><script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
>```

### 2.jQuery版本介绍
>jQuery2.0以上的版本是不兼容IE8以及以下版本的

### 3.jQuery的兼容性引入方式
>```html
><!DOCTYPE html>
><html lang="en">
><head>
>    <meta charset="UTF-8">
>    <title>使用jQuery</title>
></head>
><body>
>    <!--chrome firefox Safari opera IE9+-->
>    <!--[if gt IE 8]-->
>    <script src="js/jquery-3.4.1.js"></script>
>    <!--<![endif]-->
>
>    <!--IE8以及以下-->
>    <!--[if glt IE 8]>
>    <script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min.js"></script>
>    <![endif]-->
></body>
></html>
>```

### 4.jQuery的使用
>1. ready表示页面中DOM加载完毕后触发
>
>2. load事件页面中所有的一切加载完毕后触发
>
>   ```javascript
>   $(document).ready(function(){
>   	code....
>   })
>   //ready的简写
>   $(function(){
>       code...
>   })
>   ```

### 5.jQuery的特点
>1. 轻量,开源,免费,易于学习
>2. 兼容性处理
>3. 强大的选择器