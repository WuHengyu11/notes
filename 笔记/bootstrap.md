[TOC]
# Bootstrap笔记
## Bootstrap 全局样式-排版
> bootstrap全局将字体大小设置为：12px，行高设置为：1.248，直接覆盖body
>
> ```html
> <!DOCTYPE html>
> <html lang="en">
> <head>
>     <meta charset="UTF-8">
>     <title>demo2</title>
>     <link rel="stylesheet" href="js/bootstrap/css/bootstrap.css">
> </head>
> <body>
>     <div class="container">
>         <h1>demo2</h1>
>         <h2>demo2</h2>
>         <h3>demo2</h3>
>         <h4>demo2<small>欢迎你的访问</small></h4>
>         <p>hellohellohellohellohellohello</p>
>         <!-- 突出显示-->
>         <p class="lead">hellohellohellohellohellohello</p>
>         <p>Hello World:欢迎来到<mark>demo2</mark></p>
>         <del>demo2</del>
> 
>         <p class="text-left">are you ok ?</p>
>         <p class="text-right">are you ok ?</p>
>         <p class="text-center">are you ok ?</p>
>         <!--大写转化为小写-->
>         <p class="text-lowercase">ARe you ok ?</p>
>         <!--小写转化为大写-->
>         <p class="text-uppercase">are you ok ?</p>
>         <!--首字母大写-->
>         <p class="text-capitalize">are you ok ?</p>
>         <!--缩略语-->
>         <p>hellohellohellohellohello<abbr title="attribute">hello</abbr></p>
>         <!--地址-->
>         <address>
>             <strong>demo2</strong><br>
>             北京市,海淀区<br>
>             上地三街,嘉华大厦:1008
>             <abbr title="Phone">P:8888 8888</abbr>
>         </address>
>         <!--无样式列表-->
>         <ul class="list-unstyled">
>             <li>1</li>
>             <li>2</li>
>             <li>3</li>
>         </ul>
>     </div>
> </body>
> </html>
> ```

## Bootstrap  CSS 栅格
### 布局容器
>Bootstrap 需要为页面内容和栅格系统包裹一个 .container 容器。我们提供了两个作此用处的类。注意，由于 padding 等属性的原因，这两种 容器类不能互相嵌套。
>.container 类用于固定宽度并支持响应式布局的容器。
>
>```html
><div class="container">
>  ...
></div>
>```
>

>.container-fluid 类用于 100% 宽度，占据全部视口（viewport）的容器。
>
>```html
><div class="container-fluid">
>  ...
></div>
>```

### 栅格系统
#### 简介
>栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。下面就介绍一下 Bootstrap 栅格系统的工作原理：
“行（row）”必须包含在 .container （固定宽度）或 .container-fluid （100% 宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。
通过“行（row）”在水平方向创建一组“列（column）”。
你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素。
类似 .row 和 .col-xs-4 这种预定义的类，可以用来快速创建栅格布局。Bootstrap 源码中定义的 mixin 也可以用来创建语义化的布局。
通过为“列（column）”设置 padding 属性，从而创建列与列之间的间隔（gutter）。通过为 .row 元素设置负值 margin 从而抵消掉为 .container 元素设置的 padding，也就间接为“行（row）”所包含的“列（column）”抵消掉了padding。
负值的 margin就是下面的示例为什么是向外突出的原因。在栅格列中的内容排成一行。
栅格系统中的列是通过指定1到12的值来表示其跨越的范围。例如，三个等宽的列可以使用三个 .col-xs-4 来创建。
如果一“行（row）”中包含了的“列（column）”大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列。
栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 .col-md-* 栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 .col-lg-* 不存在， 也影响大屏幕设备。

#### 栅格参数
>通过下表可以详细查看 Bootstrap 的栅格系统是如何在多种屏幕设备上工作的。
>
>|                    | 超小屏幕 手机(<768px) | 小屏幕 平板(>=768px) | 中等屏幕 桌面显示器(>=992px) | 大屏幕 大桌面显示器(>=1200px) |
>| ------------------ | --------------------- | -------------------- | ---------------------------- | ----------------------------- |
>| 栅格系统行为       |                       |                      |                              |                               |
>| .container最大宽度 | None(自动)            | 750px                | 970px                        | 1170px                        |
>| 类前缀             | .col-xs-              | .col-sm-             | .col-md-                     | .col-lg-                      |
>| 列(column)数       | 12 |12|12|12|
>| 最大列(column)宽 | 自动 | ~62px | ~81px | ~97px |
>| 槽(gutter)宽 | 30px(每列左右均有15px) | 30px(每列左右均有15px) | 30px(每列左右均有15px) | 30px(每列左右均有15px) |
>| 可嵌套 | 是 | 是 | 是 | 是 |
>| 偏移(Offsets) | 是 | 是 | 是 | 是 |
>| 列排序 | 是 | 是 | 是 | 是 |
>

>代码实例:
>
>```html
><!DOCTYPE html>
><html lang="en">
><head>
><meta charset="UTF-8">
><title>demo3</title>
><link rel="stylesheet" href="js/bootstrap/css/bootstrap.css">
><style>
>   .row{
>       margin-bottom: 20px;
>   }
>   .row .row{
>       margin-top: 10px;
>       margin-bottom: 0px;
>   }
>   [class*="col-"]{
>       padding-top: 15px;
>       padding-bottom: 15px;
>       background-color: #eee;
>       background-color: rgba(86,61,124,.15);
>       border: 1px solid #ddd;
>       border: 1px solid rgba(86,61,124,.2);
>   }
></style>
></head>
><body>
><div class="container">
>   <div class="row">
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>       <div class="col-md-1">col-md-1</div>
>   </div>
>
>   <div class="row">
>       <div class="col-md-3">col-md-3</div>
>       <div class="col-md-3">col-md-3</div>
>       <div class="col-md-3">col-md-3</div>
>       <!--<div class="col-md-3">col-md-3</div>-->
>   </div>
>
>   <div class="row">
>       <div class="col-md-3">col-md-3col-md-3col-md-3col-md-3col-md-3col-md-3</div>
>       <div class="col-md-3">col-md-3</div>
>       <div class="col-md-3">col-md-3</div>
>       <!--<div class="col-md-3">col-md-3</div>-->
>   </div>
>   <!--实现偏移效果-->
>   <div class="row">
>       <div class="col-md-4 col-md-offset-1">col-md-4</div>
>   </div>
>   <!--实现嵌套效果-->
>   <div class="row">
>       <div class="col-sm-9">
>           one
>           <div class="row">
>               <div class="col-xs-8">
>                   first
>               </div>
>               <div class="col-xs-4">
>                   two
>               </div>
>           </div>
>       </div>
>   </div>
>
>   <!--实现排序效果-->
>   <div class="row">
>       <div class="col-md-9 col-md-push-3">col-md-9</div>
>       <div class="col-md-3 col-md-pull-9">col-md-3</div>
>   </div>
></div>
></body>
></html>
>```

## Bootstrap CSS 代码
>```html
><!DOCTYPE html>
><html lang="en">
><head>
>    <meta charset="UTF-8">
>    <title>demo1</title>
>    <link href="js/bootstrap/css/bootstrap.css">
></head>
><body>
>    <div class="container">
>        <!--code-->
>        For example <code>&lt;section&gt;</code> as inline;
>        我现在希望可以键入<kbd>cmd</kbd>命令
>        <pre>
>            Sample text here...;
>        </pre>
>        <var>x</var> = <var>y</var>+<var>z</var>
>        <samp> Hello world</samp>
>    </div>
></body>
></html>
>```

## Bootstrap CSS 表格

>```html
><!DOCTYPE html>
><html lang="en">
><head>
>    <meta charset="UTF-8">
>    <title>demo1</title>
>    <link rel="stylesheet" href="bootstrap-3.3.7/css/bootstrap.css">
></head>
><body>
>    <div class="container">
>        <table class="table table-striped table-bordered table-hover">
>            <thead>
>                <tr>
>                    <th>表格标题</th>
>                    <th>表格标题</th>
>                    <th>表格标题</th>
>                </tr>
>            </thead>
>            <tbody>
>                <tr>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                </tr>
>                <tr>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                </tr>
>            </tbody>
>        </table>
>        <!--紧凑表格-->
>        <table class="table-condensed">
>            <thead>
>                <tr>
>                    <th>表格标题</th>
>                    <th>表格标题</th>
>                    <th>表格标题</th>
>                </tr>
>            </thead>
>            <tbody>
>                <tr>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                </tr>
>                <tr>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                </tr>
>            </tbody>
>        </table>
>        <div class="table-responsive">
>        <table class="table  table-bordered ">
>            <thead>
>                <tr class="active">
>                    <th>表格标题</th>
>                    <th>表格标题</th>
>                    <th>表格标题</th>
>                </tr>
>            </thead>
>            <tbody>
>                <tr class="info">
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                    <td>表sdfgdsfgserdgsdfghserdhsdtrgrdz格单元格</td>
>                </tr>
>                <tr class="warning">
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                </tr>
>                <tr class="danger">
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                </tr>
>                <tr class="warning">
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                    <td>表格单元格</td>
>                </tr>
>            </tbody>
>        </table>
>        </div>
>    </div>
></body>
></html>
>```



