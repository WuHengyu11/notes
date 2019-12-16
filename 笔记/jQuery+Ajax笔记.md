[TOC]
# jQuery+Ajax笔记
## jQuery简介
>jQuery库可以通过一行简单的标记被添加到网页中.

### 什么是jQuery?
>jQuery是一个JavaScript函数库。
jQuery是一个轻量级的"写的少，做的多"的JavaScript库。
jQuery库包含以下功能：
>>1. HTML 元素选取
>>2. HTML 元素操作
>>3. CSS 操作
>>4. HTML 事件函数
>>5. JavaScript 特效和动画
>>6. HTML DOM 遍历和修改
>>7. AJAX
>>8. Utilities
提示： 除此之外，Jquery还提供了大量的插件。

## jQuery安装
### 网页中添加jQuery
>可以通过多种方法在网页中添加jQuery.可以使用以下方法:
>>1. 从 jquery.com 下载 jQuery 库
>>2. 从 CDN 中载入 jQuery, 如从 Google 中加载 jQuery

### 下载jQuery
>有两个版本的jQuery可供下载:
>>1. Production version - 用于实际的网站中，已被精简和压缩。
>>2. Development version - 用于测试和开发（未压缩，是可读的代码）
>
>jQuery 库是一个 JavaScript 文件，您可以使用 HTML 的 <script> 标签引用它：
>
>```javascript
><head>
><script src="jquery-1.10.2.min.js"></script>
></head>
>```

### 替代方案
>如果您不希望下载并存放 jQuery，那么也可以通过 CDN（内容分发网络） 引用它。
>Staticfile CDN、百度、又拍云、新浪、谷歌和微软的服务器都存有 jQuery 。
>如果你的站点用户是国内的，建议使用百度、又拍云、新浪等国内CDN地址，如果你站点用户是国外的可以使用谷歌和微软。
>如需从 Staticfile CDN、又拍云、新浪、谷歌或微软引用 jQuery，请使用以下代码之一：
>
>Staticfile CDN:
>
>```javascript
><head>
><script src="https://cdn.staticfile.org/jquery/1.10.2/jquery.min.js">
></script>
></head>
>```
>
>百度 CDN:
>```javascript
><head>
><script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js">
></script>
></head>
>```
>
>又拍云 CDN:
>
>```javascript
><head>
><script src="https://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.2.min.js">
></script>
></head>
>```
>
>新浪 CDN:
>
>```javascript
><head>
><script src="https://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js">
></script>
></head>
>```
>
>Google CDN(国内不推荐):
>
>```javascript
><head>
><script src="https://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js">
></script>
></head>
>```
>
>Microsoft CDN:
>
>```javascript
><head>
><script src="https://ajax.aspnetcdn.com/ajax/jquery/jquery-1.9.0.min.js"></script>
></head>
>```

## jQuery 语法
>通过 jQuery，您可以选取（查询，query） HTML 元素，并对它们执行"操作"（actions）。

### jQuery 语法
>jQuery 语法是通过选取 HTML 元素，并对选取的元素执行某些操作。
>基础语法： $(selector).action()
>>1. 美元符号定义 jQuery
>>2. 选择符（selector）"查询"和"查找" HTML 元素
>>3. jQuery 的 action() 执行对元素的操作
>
>实例:
>>1 .$(this).hide() - 隐藏当前元素
>>2. $("p").hide() - 隐藏所有 <p> 元素
>>3. $("p.test").hide() - 隐藏所有 class="test" 的 <p> 元素
>>4. $("#test").hide() - 隐藏所有 id="test" 的元素

### 文档就绪事件
>jQuery入口函数:
>
>```javascript
>$(document).ready(function(){
>// 执行代码
>});
>或者
>$(function(){
>// 执行代码
>});
>```
>JavaScript入口函数:
>
>```javascript
>window.onload = function () {
>// 执行代码
>}
>```
>
>jQuery 入口函数与 JavaScript 入口函数的区别：
>1. jQuery 的入口函数是在 html 所有标签(DOM)都加载之后，就会去执行。
>
>2. JavaScript 的 window.onload 事件是等到所有内容，包括外部图片之类的文件加载完后，才会执行。
>
>   load和ready的区别
>
> |          | window.onload                                           | $(document).ready()                                  |
> | -------- | ------------------------------------------------------- | ---------------------------------------------------- |
> | 执行时机 | 必须等待网页全部加载完毕(包括图片等),然后再执行包裹代码 | 只需要等待网页中的DOM结构加载完毕,就能执行包裹的代码 |
> | 执行次数 | 只能执行一次,如果第二次,那么第一次的执行会被覆盖        | 可以执行多次,第N次都不会被上一次覆盖                 |
> | 简写方案 | 无                                                      | $(function(){<br />});                               |
>

## jQuery选择器
>jQuery 选择器允许您对 HTML 元素组或单个元素进行操作。

### jQuery 选择器
>jQuery 选择器允许您对 HTML 元素组或单个元素进行操作。
jQuery 选择器基于元素的 id、类、类型、属性、属性值等"查找"（或选择）HTML 元素。 它基于已经存在的 CSS 选择器，除此之外，它还有一些自定义的选择器。
jQuery 中所有选择器都以美元符号开头：$()。

### 元素选择器
>jQuery 元素选择器基于元素名选取元素。
>在页面中选取所有 <p> 元素:
>
>```javascript
>$("p")
>```
>示例：用户点击按钮后，所有 <p> 元素都隐藏：
>
>```javascript
>$(document).ready(function(){
>  $("button").click(function(){
>    $("p").hide();
>  });
>});
>```

### #id 选择器
>jQuery #id 选择器通过 HTML 元素的 id 属性选取指定的元素。
>页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。
>
>通过 id 选取元素语法如下：
>
>```javascript
>$("#test")
>```
>示例：当用户点击按钮后，有 id="test" 属性的元素将被隐藏：
>
>```javascript
>$(document).ready(function(){
>  $("button").click(function(){
>    $("#test").hide();
>  });
> });
>```

### .class 选择器
>jQuery 类选择器可以通过指定的 class 查找元素。
>语法如下：
>
>```javascript
>$(".test")
>```
>示例：用户点击按钮后所有带有 class="test" 属性的元素都隐藏：
>
>```javascript
>$(document).ready(function(){
>  $("button").click(function(){
>    $(".test").hide();
>  });
>});
>```

### 更多示例

>| 语法                     | 描述                                                    |
| ------------------------ | ------------------------------------------------------- |
| $("*")                   | 选取所有元素                                            |
| $(this)                  | 选取当前 HTML 元素                                      |
| $("p.intro")             | 选取 class 为 intro 的 <p> 元素                         |
| $("p.first")             | 选取第一个 <p> 元素                                     |
| $("ul li:first")         | 选取第一个 <ul> 元素的第一个 <li> 元素                  |
| $("ul li:first-child")   | 选取每个 <ul> 元素的第一个 <li> 元素                    |
| $("[href]")              | 选取带有 href 属性的元素                                |
| $("a[target='_blank']")  | 选取所有 target 属性值等于 "_blank" 的 <a> 元素         |
| $("a[target!='_blank']") | 选取所有 target 属性值不等于 "_blank" 的 <a> 元素       |
| $(":button")             | 选取所有 type="button" 的 <input> 元素 和 <button> 元素 |
| $("tr:even")             | 选取偶数位置的 <tr> 元素                                |
| $("tr:odd")              | 选取奇数位置的 <tr> 元素                                |

## jQuery事件
>jQuery 是为事件处理特别设计的。

### 什么是事件？
>页面对不同访问者的响应叫做事件。
>事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。
>实例：
>在元素上移动鼠标。
>选取单选按钮
>点击元素
>在事件中经常使用术语"触发"（或"激发"）例如： "当您按下按键时触发 keypress 事件"。
>
>常见 DOM 事件：
>
>| 鼠标事件   | 键盘事件 | 表单事件 | 文档/窗口事件 |
>| ---------- | -------- | -------- | ------------- |
>| click      | keypress | submit   | load          |
>| dbclick    | keydown  | change   | resize        |
>| mouseenter | keyup    | focus    | scroll        |
>| mouseleave |          | blur     | unload        |
>| hover      |          |          |               |

### jQuery 事件方法语法
>在 jQuery 中，大多数 DOM 事件都有一个等效的 jQuery 方法。
>页面中指定一个点击事件：
>
>```javascript
>$("p").click();
>```
>下一步是定义什么时间触发事件。您可以通过一个事件函数实现：
>
>```javascript
>$("p").click(function(){
>    // 动作触发后执行的代码!!
>});
>```

### 常用的 jQuery 事件方法
#### $(document).ready()：
>$(document).ready() 方法允许我们在文档完全加载完后执行函数。该事件方法在 jQuery 语法 章节中已经提到过。

#### click()
>click() 方法是当按钮点击事件被触发时会调用一个函数。
>该函数在用户点击 HTML 元素时执行。
>在下面的实例中，当点击事件在某个 <p> 元素上触发时，隐藏当前的 <p> 元素：
>示例：
>
>```javascript
>$("p").click(function(){
>  $(this).hide();
>});
>```

#### dblclick()
>当双击元素时，会发生 dblclick 事件。
>dblclick() 方法触发 dblclick 事件，或规定当发生 dblclick 事件时运行的函数：
>示例:
>
>```javascript
>$("p").dblclick(function(){
>  $(this).hide();
>});
>```

#### mouseenter()
>当鼠标指针穿过元素时，会发生 mouseenter 事件。
>mouseenter() 方法触发 mouseenter 事件，或规定当发生 mouseenter 事件时运行的函数：
>
>示例:
>
>```javascript
>$("#p1").mouseenter(function(){
>    alert('您的鼠标移到了 id="p1" 的元素上!');
>});
>```

#### mouseleave()
>当鼠标指针离开元素时，会发生 mouseleave 事件。
>mouseleave() 方法触发 mouseleave 事件，或规定当发生 mouseleave 事件时运行的函数
>
>示例:
>
>```javascript
>$("#p1").mouseleave(function(){
>        alert("再见，您的鼠标离开了该段落。");
>});
>```

#### mousedown()
>当鼠标指针移动到元素上方，并按下鼠标按键时，会发生 mousedown 事件。
>mousedown() 方法触发 mousedown 事件，或规定当发生 mousedown 事件时运行的函数：
>示例:
>
>```javascript
>$("#p1").mousedown(function(){
>    alert("鼠标在该段落上按下！");
>});
>```

#### mouseup()
>当在元素上松开鼠标按钮时，会发生 mouseup 事件。
>mouseup() 方法触发 mouseup 事件，或规定当发生 mouseup 事件时运行的函数：
>
>示例:
>
>```javascript
>$("#p1").mouseup(function(){
>    alert("鼠标在段落上松开。");
>});
>```

#### hover()
>hover()方法用于模拟光标悬停事件。
>当鼠标移动到元素上时，会触发指定的第一个函数(mouseenter);当鼠标移出这个元素时，会触发指定的第二个函数(mouseleave)
>
>示例:
>
>```javascript
>$("#p1").hover(
>    function(){
>        alert("你进入了 p1!");
>    },
>    function(){
>        alert("拜拜! 现在你离开了 p1!");
>    }
>);
>```

#### focus()
>当元素获得焦点时，发 生 focus 事件。
>当通过鼠标点击选中元素或通过 tab 键定位到元素时，该元素就会获得焦点。
>focus() 方法触发 focus 事件，或规定当发生 focus 事件时运行的函数：
>
>示例:
>
>```javascript
>$("input").focus(function(){
>  $(this).css("background-color","#cccccc");
>});
>```

#### blur()
>当元素失去焦点时，发生 blur 事件。
>blur() 方法触发 blur 事件，或规定当发生 blur 事件时运行的函数：
>
>示例:
>
>```javascript
>$("input").blur(function(){
>  $(this).css("background-color","#ffffff");
>});
>```

## jQuery 效果- 隐藏和显示
### jQuery hide() 和 show()
>通过 jQuery，您可以使用 hide() 和 show() 方法来隐藏和显示 HTML 元素：
>
>实例:
>
>```javascript
>$("#hide").click(function(){
>$("p").hide();
>});
>
>$("#show").click(function(){
>$("p").show();
>});
>```
>
>语法:
>
>```javascript
>$(selector).hide(speed,callback);
>$(selector).show(speed,callback);
>```
>可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。
>可选的 callback 参数是隐藏或显示完成后所执行的函数名称。
>
>示例：
>
>```javascript
>$("button").click(function(){
>$("p").hide(1000);
>});
>```
>下面的例子演示了带有 speed 参数的 hide() 方法，并使用回调函数：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $(".hidebtn").click(function(){
>    $("div").hide(1000,"linear",function(){
>      alert("Hide() 方法已完成!");
>    });
>  });
>});
>```
>第二个参数是一个字符串，表示过渡使用哪种缓动函数。（译者注：jQuery自身提供"linear" 和 "swing"，其他可以使用相关的插件）。

### jQuery toggle()
>通过 jQuery，您可以使用 toggle() 方法来切换 hide() 和 show() 方法。
>显示被隐藏的元素，并隐藏已显示的元素：
>
>示例:
>
>```javascript
>$("button").click(function(){
>$("p").toggle();
>});
>```
>语法:
>
>```
>$(selector).toggle(speed,callback);
>```
>
>可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。
>可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

## jQuery 效果 - 淡入淡出
### jQuery Fading 方法
>通过 jQuery，您可以实现元素的淡入淡出效果。
>jQuery 拥有下面四种 fade 方法：
>
>* fadeIn()
>* fadeOut()
>* fadeToggle()
>* fadeTo()

### jQuery fadeIn() 方法
>jQuery fadeIn() 用于淡入已隐藏的元素。
>
>语法：
>
>```javascript
>$(selector).fadeIn(speed,callback);
>```
>可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。.
>可选的 callback 参数是 fading 完成后所执行的函数名称。
>下面的例子演示了带有不同参数的 fadeIn() 方法：
>示例：
>
>```javascript
>$("button").click(function(){
>  $("#div1").fadeIn();
>  $("#div2").fadeIn("slow");
>  $("#div3").fadeIn(3000);
>});
>```

### jQuery fadeOut() 方法
>jQuery fadeOut() 方法用于淡出可见元素。
>语法：
>
>```
>$(selector).fadeOut(speed,callback);
>```
>可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>可选的 callback 参数是 fading 完成后所执行的函数名称。
>下面的例子演示了带有不同参数的 fadeOut() 方法：
>示例:
>
>```javascript
>$("button").click(function(){
>  $("#div1").fadeOut();
>  $("#div2").fadeOut("slow");
>  $("#div3").fadeOut(3000);
>});
>```

### jQuery fadeToggle() 方法
>jQuery fadeToggle() 方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换。
>如果元素已淡出，则 fadeToggle() 会向元素添加淡入效果。
>如果元素已淡入，则 fadeToggle() 会向元素添加淡出效果。
>语法:
>
>```javascript
>$(selector).fadeToggle(speed,callback);
>```
>可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>可选的 callback 参数是 fading 完成后所执行的函数名称。
>下面的例子演示了带有不同参数的 fadeToggle() 方法：
>示例:
>
>```javascript
>$("button").click(function(){
>  $("#div1").fadeToggle();
>  $("#div2").fadeToggle("slow");
>  $("#div3").fadeToggle(3000);
>});
>```

### jQuery fadeTo() 方法
>jQuery fadeTo() 方法允许渐变为给定的不透明度（值介于 0 与 1 之间）。
>语法:
>
>```javascript
>$(selector).fadeTo(speed,opacity,callback);
>```
>必需的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>fadeTo() 方法中必需的 opacity 参数将淡入淡出效果设置为给定的不透明度（值介于 0 与 1 之间）。
>可选的 callback 参数是该函数完成后所执行的函数名称。
>下面的例子演示了带有不同参数的 fadeTo() 方法：
>示例:
>
>```javascript
>$("button").click(function(){
>  $("#div1").fadeTo("slow",0.15);
>  $("#div2").fadeTo("slow",0.4);
>  $("#div3").fadeTo("slow",0.7);
>});
>```

## jQuery 效果 - 滑动
>jQuery 滑动方法可使元素上下滑动。

### jQuery 滑动方法
>通过 jQuery，您可以在元素上创建滑动效果。
>jQuery 拥有以下滑动方法：
>
>* slideDown()
>* slideUp()
>* slideToggle()

### jQuery slideDown() 方法
>jQuery slideDown() 方法用于向下滑动元素。
>语法:
>
>```javascript
>$(selector).slideDown(speed,callback);
>```
>
>可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>可选的 callback 参数是滑动完成后所执行的函数名称。
>下面的例子演示了 slideDown() 方法：
>示例：
>
>```javascript
>$("#flip").click(function(){
>  $("#panel").slideDown();
>});
>```

### jQuery slideUp() 方法
>jQuery slideUp() 方法用于向上滑动元素。
>语法:
>
>```javascript
>$(selector).slideUp(speed,callback);
>```
>可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>可选的 callback 参数是滑动完成后所执行的函数名称。
>下面的例子演示了 slideUp() 方法：
>示例：
>
>```javascript
>$("#flip").click(function(){
>  $("#panel").slideUp();
>});
>```

### jQuery slideToggle() 方法
>jQuery slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。
>如果元素向下滑动，则 slideToggle() 可向上滑动它们。
>如果元素向上滑动，则 slideToggle() 可向下滑动它们。
>
>```javascript
>$(selector).slideToggle(speed,callback);
>```
>
>可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
>可选的 callback 参数是滑动完成后所执行的函数名称。
>下面的例子演示了 slideToggle() 方法：
>示例：
>
>```javascript
>$("#flip").click(function(){
>  $("#panel").slideToggle();
>});
>```

## jQuery - 获取内容和属性
>jQuery 拥有可操作 HTML 元素和属性的强大方法。

### jQuery DOM 操作
>jQuery 中非常重要的部分，就是操作 DOM 的能力。
>jQuery 提供一系列与 DOM 相关的方法，这使访问和操作元素和属性变得很容易。
>> DOM = Document Object Model（文档对象模型）
DOM 定义访问 HTML 和 XML 文档的标准：
"W3C 文档对象模型独立于平台和语言的界面，允许程序和脚本动态访问和更新文档的内容、结构以及样式。"

### 获得内容 - text()、html() 以及 val()
>三个简单实用的用于 DOM 操作的 jQuery 方法：
>>* text() - 设置或返回所选元素的文本内容
>>* html() - 设置或返回所选元素的内容（包括 HTML 标记）
>>* val() - 设置或返回表单字段的值
>
>下面的例子演示如何通过 jQuery text() 和 html() 方法来获得内容：
>
>示例:
>
>```javascript
>$("#btn1").click(function(){
>  alert("Text: " + $("#test").text());
>});
>$("#btn2").click(function(){
>  alert("HTML: " + $("#test").html());
>});
>
>```
>
>下面的例子演示如何通过 jQuery val() 方法获得输入字段的值：
>
>示例：
>
>```javascript
>$("#btn1").click(function(){
>  alert("值为: " + $("#test").val());
>});
>```

### 获取属性 - attr()
>jQuery attr() 方法用于获取属性值。
>下面的例子演示如何获得链接中 href 属性的值：
>示例：
>
>```javascript
>$("button").click(function(){
>  alert($("#runoob").attr("href"));
>});
>```

## jQuery - 设置内容和属性
### 设置内容 - text()、html() 以及 val()
>我们将使用前一章中的三个相同的方法来设置内容：
>>* text() - 设置或返回所选元素的文本内容
>>
>>* html() - 设置或返回所选元素的内容（包括 HTML 标记）
>>
>>* val() - 设置或返回表单字段的值
>
>下面的例子演示如何通过 text()、html() 以及 val() 方法来设置内容：
>示例：
>
>```javascript
>$("#btn1").click(function(){
>    $("#test1").text("Hello world!");
>});
>$("#btn2").click(function(){
>    $("#test2").html("<b>Hello world!</b>");
>});
>$("#btn3").click(function(){
>    $("#test3").val("RUNOOB");
>});
>```

### text()、html() 以及 val() 的回调函数
>上面的三个 jQuery 方法：text()、html() 以及 val()，同样拥有回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。
>下面的例子演示带有回调函数的 text() 和 html()：
>
>示例:
>
>```javascript
>$("#btn1").click(function(){
>    $("#test1").text(function(i,origText){
>        return "旧文本: " + origText + " 新文本: Hello world! (index: " + i + ")"; 
>    });
>});
> 
>$("#btn2").click(function(){
>    $("#test2").html(function(i,origText){
>        return "旧 html: " + origText + " 新 html: Hello <b>world!</b> (index: " + i + ")"; 
>    });
>});
>```

### 设置属性 - attr()
>jQuery attr() 方法也用于设置/改变属性值。
>下面的例子演示如何改变（设置）链接中 href 属性的值：
>
>示例：
>
>```javascript
>$("button").click(function(){
>$("#runoob").attr("href","http://www.runoob.com/jquery");
>});
>```
>attr() 方法也允许您同时设置多个属性。
>下面的例子演示如何同时设置 href 和 title 属性：
>
>示例：
>
>```javascript
>$("button").click(function(){
>    $("#runoob").attr({
>        "href" : "http://www.runoob.com/jquery",
>        "title" : "jQuery 教程"
>    });
>});
>```

### attr() 的回调函数
>jQuery 方法 attr()，也提供回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。
>下面的例子演示带有回调函数的 attr() 方法：
>
>示例:
>
>```javascript
>$("button").click(function(){
>  $("#runoob").attr("href", function(i,origValue){
>    return origValue + "/jquery"; 
>  });
>});
>```

## jQuery - 添加元素
>通过 jQuery，可以很容易地添加新元素/内容。

### 添加新的 HTML 内容
>我们将学习用于添加新内容的四个 jQuery 方法:
>>* append() - 在被选元素的结尾插入内容
>>* prepend() - 在被选元素的开头插入内容
>>* after() - 在被选元素之后插入内容
>>* before() - 在被选元素之前插入内容

### jQuery append() 方法
>jQuery append() 方法在被选元素的结尾插入内容（仍然该元素的内部）。
>示例：
>
>```javascript
>$("p").append("追加文本");
>```

### jQuery prepend() 方法
>jQuery prepend() 方法在被选元素的开头插入内容。
>
>```javascript
>$("p").prepend("在开头追加文本");
>```

### 通过 append() 和 prepend() 方法添加若干新元素
>在上面的例子中，我们只在被选元素的开头/结尾插入文本/HTML。
>不过，append() 和 prepend() 方法能够通过参数接收无限数量的新元素。可以通过 jQuery 来生成文本/HTML（就像上面的例子那样），或者通过 JavaScript 代码和 DOM 元素。
>在下面的例子中，我们创建若干个新元素。这些元素可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建。然后我们通过 append() 方法把这些新元素追加到文本中（对 prepend() 同样有效）：
>
>实例
>
>```javascript
>function appendText()
>{
>    var txt1="<p>文本。</p>";              // 使用 HTML 标签创建文本
>    var txt2=$("<p></p>").text("文本。");  // 使用 jQuery 创建文本
>    var txt3=document.createElement("p");
>    txt3.innerHTML="文本。";               // 使用 DOM 创建文本 text with DOM
>    $("body").append(txt1,txt2,txt3);        // 追加新元素
>}
>```
>

### jQuery after() 和 before() 方法
>jQuery after() 方法在被选元素之后插入内容。
>jQuery before() 方法在被选元素之前插入内容。
>
>示例：
>
>```javascript
>$("img").after("在后面添加文本");
> 
>$("img").before("在前面添加文本");
>```

### 通过 after() 和 before() 方法添加若干新元素
>after() 和 before() 方法能够通过参数接收无限数量的新元素。可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建新元素。
>在下面的例子中，我们创建若干新元素。这些元素可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建。然后我们通过 after() 方法把这些新元素插到文本中（对 before() 同样有效）：
>
>示例：
>
>```javascript
>function afterText()
>{
>    var txt1="<b>I </b>";                    // 使用 HTML 创建元素
>    var txt2=$("<i></i>").text("love ");     // 使用 jQuery 创建元素
>    var txt3=document.createElement("big");  // 使用 DOM 创建元素
>    txt3.innerHTML="jQuery!";
>    $("img").after(txt1,txt2,txt3);          // 在图片后添加文本
>}
>```

## jQuery - 删除元素
>通过 jQuery，可以很容易地删除已有的 HTML 元素。

### 删除元素/内容
>如需删除元素和内容，一般可使用以下两个 jQuery 方法：
>>* remove() - 删除被选元素（及其子元素）
>>* empty() - 从被选元素中删除子元素

### jQuery remove() 方法
>jQuery remove() 方法删除被选元素及其子元素
>
>示例：.=                                                                      
>
>```javascript
>$("#div1").remove();
>```

### jQuery empty() 方法
>jQuery empty() 方法删除被选元素的子元素。
>
>示例:
>
>```javascript
>$("#div1").empty();
>```

### 过滤被删除的元素
>jQuery remove()  方法也可接受一个参数，允许您对被删元素进行过滤。
>该参数可以是任何 jQuery 选择器的语法。
>下面的例子删除 class="italic" 的所有 <p> 元素：
>
>示例:
>
>```javascript
>$("p").remove(".italic");
>```

## jQuery - 获取并设置 CSS 类
>通过 jQuery，可以很容易地对 CSS 元素进行操作

### jQuery 操作 CSS
>jQuery 拥有若干进行 CSS 操作的方法。我们将学习下面这些：
>>* addClass() - 向被选元素添加一个或多个类
>>* removeClass() - 从被选元素删除一个或多个类
>>* toggleClass() - 对被选元素进行添加/删除类的切换操作
>>* css() - 设置或返回样式属性 

### 实例样式表
>下面的样式表将用于本页的所有例子：
>
>示例:
>
>```css
>.important
>{
>        font-weight:bold;
>        font-size:xx-large;
>}
> 
>.blue
>{
>        color:blue;
>}
>```

### jQuery addClass() 方法
>下面的例子展示如何向不同的元素添加 class 属性。当然，在添加类时，您也可以选取多个元素：
>
>示例:
>
>```javascript
>$("button").click(function(){
>$("h1,h2,p").addClass("blue");
>$("div").addClass("important");
>});
>```
>
>也可以在 addClass() 方法中规定多个类：
>
>示例:
>
>```javascript
>$("button").click(function(){
>  $("body div:first").addClass("important blue");
>});
>```

### jQuery removeClass() 方法
>下面的例子演示如何在不同的元素中删除指定的 class 属性：
>
>示例：
>
>```javascript
>$("button").click(function(){
>  $("h1,h2,p").removeClass("blue");
>});
>```

### jQuery toggleClass() 方法
>下面的例子将展示如何使用 jQuery toggleClass() 方法。该方法对被选元素进行添加/删除类的切换操作：
>
>示例:
>
>```javascript
>$("button").click(function(){
>  $("h1,h2,p").toggleClass("blue" );
>});
>```

## jQuery css() 方法
### jQuery css() 方法
>css() 方法设置或返回被选元素的一个或多个样式属性。

### 返回 CSS 属性
>如需返回指定的 CSS 属性的值，请使用如下语法：
>
>```css
>css("propertyname");
>```
>
>下面的例子将返回首个匹配元素的 background-color 值：
>
>示例:
>
>```javascript
>$("p").css("background-color");
>```

### 设置 CSS 属性
>如需设置指定的 CSS 属性，请使用如下语法：
>
>示例:
>
>```css
>css("propertyname","value");
>```
>
>下面的例子将为所有匹配元素设置 background-color 值：
>
>示例:
>
>```javascript
>$("p").css("background-color","yellow");
>```
>
>

### 设置多个 CSS 属性
>如需设置多个 CSS 属性，请使用如下语法：
>
>```css
>css({"propertyname":"value","propertyname":"value",...});
>```
>
>下面的例子将为所有匹配元素设置 background-color 和 font-size：
>
>示例:
>
>```javascript
>$("p").css({"background-color":"yellow","font-size":"200%"});
>```

## jQuery 尺寸

## jQuery 遍历
### 什么是遍历？             
>Query 遍历，意为"移动"，用于根据其相对于其他元素的关系来"查找"（或选取）HTML 元素。以某项选择开始，并沿着这个选择移动，直到抵达您期望的元素为止。
>下图展示了一个家族树。通过 jQuery 遍历，您能够从被选（当前的）元素开始，轻松地在家族树中向上移动（祖先），向下移动（子孙），水平移动（同胞）。这种移动被称为对 DOM 进行遍历。
>
>ps: 祖先是父、祖父、曾祖父等等。后代是子、孙、曾孙等等。同胞拥有相同的父。

### 遍历 DOM
>jQuery 提供了多种遍历 DOM 的方法。
遍历方法中最大的种类是树遍历（tree-traversal）。

### jQuery 遍历 - 祖先
>祖先是父、祖父或曾祖父等等。
通过 jQuery，您能够向上遍历 DOM 树，以查找元素的祖先。

### 向上遍历 DOM 树
>这些 jQuery 方法很有用，它们用于向上遍历 DOM 树：
>>* parent()
>>* parents()
>>* parentsUntil()

### jQuery parent() 方法
>parent() 方法返回被选元素的直接父元素。
>该方法只会向上一级对 DOM 树进行遍历。
>下面的例子返回每个 <span> 元素的的直接父元素：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>  $("span").parent();
>});
>```

### jQuery parents() 方法
>parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。
>下面的例子返回所有 <span> 元素的所有祖先：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>$("span").parents();
>});
>```
>
>也可以使用可选参数来过滤对祖先元素的搜索。
>下面的例子返回所有 <span> 元素的所有祖先，并且它是 <ul> 元素：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>  $("span").parents("ul");
>});
>```

### jQuery parentsUntil() 方法
>parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。
>下面的例子返回介于 <span> 与 <div> 元素之间的所有祖先元素：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $("span").parentsUntil("div");
>});
>```

### jQuery 遍历 - 后代
>后代是子、孙、曾孙等等。
通过 jQuery，您能够向下遍历 DOM 树，以查找元素的后代。

### 向下遍历 DOM 树
>下面是两个用于向下遍历 DOM 树的 jQuery 方法：
>>* children()
>>* find()

### jQuery children() 方法
>children() 方法返回被选元素的所有直接子元素。
>该方法只会向下一级对 DOM 树进行遍历。
>下面的例子返回每个 <div> 元素的所有直接子元素：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>$("div").children();
>});
>```
>也可以使用可选参数来过滤对子元素的搜索。
>下面的例子返回类名为 "1" 的所有 <p> 元素，并且它们是 <div> 的直接子元素：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>  $("div").children("p.1");
>});
>```

### jQuery find() 方法
>find() 方法返回被选元素的后代元素，一路向下直到最后一个后代。
>下面的例子返回属于 <div> 后代的所有 <span> 元素：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>$("div").find("span");
>});
>```
>下面的例子返回 <div> 的所有后代：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $("div").find("*");
>});
>```

## jQuery 遍历 - 同胞(siblings)
>同胞拥有相同的父元素。
通过 jQuery，您能够在 DOM 树中遍历元素的同胞元素。

### 在 DOM 树中水平遍历
>有许多有用的方法让我们在 DOM 树进行水平遍历：
>>* siblings()
>>* next()
>>* nextAll()
>>* nextUntil()
>>* prev()
>>* prevAll()
>>* prevUntil()

### jQuery siblings() 方法
>siblings() 方法返回被选元素的所有同胞元素。
>下面的例子返回 <h2> 的所有同胞元素：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>$("h2").siblings();
>});
>```
>也可以使用可选参数来过滤对同胞元素的搜索。
>下面的例子返回属于 <h2> 的同胞元素的所有 <p> 元素：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>  $("h2").siblings("p");
>});
>```

### jQuery next() 方法
>next() 方法返回被选元素的下一个同胞元素。
>该方法只返回一个元素。
>下面的例子返回 <h2> 的下一个同胞元素：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>  $("h2").next();
>});
>```

### jQuery nextAll() 方法
>nextAll() 方法返回被选元素的所有跟随的同胞元素。
>下面的例子返回 <h2> 的所有跟随的同胞元素：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $("h2").nextAll();
>});
>```

### jQuery nextUntil() 方法
>nextUntil() 方法返回介于两个给定参数之间的所有跟随的同胞元素。
>下面的例子返回介于 <h2> 与 <h6> 元素之间的所有同胞元素：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $("h2").nextUntil("h6");
>});
>```

### jQuery prev(), prevAll() & prevUntil() 方法
>prev(), prevAll() 以及 prevUntil() 方法的工作方式与上面的方法类似，只不过方向相反而已：它们返回的是前面的同胞元素（在 DOM 树中沿着同胞之前元素遍历，而不是之后元素遍历）。

## jQuery 遍历- 过滤
### 缩小搜索元素的范围
>三个最基本的过滤方法是：first(), last() 和 eq()，它们允许您基于其在一组元素中的位置来选择一个特定的元素。
其他过滤方法，比如 filter() 和 not() 允许您选取匹配或不匹配某项指定标准的元素。

### jQuery first() 方法
>first() 方法返回被选元素的首个元素。
>下面的例子选取首个 <div> 元素内部的第一个 <p> 元素：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $("div p").first();
>});
>```

### jQuery last() 方法
>last() 方法返回被选元素的最后一个元素。
>下面的例子选择最后一个 <div> 元素中的最后一个 <p> 元素：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $("div p").last();
>});
>```

### jQuery eq() 方法
>eq() 方法返回被选元素中带有指定索引号的元素。
>索引号从 0 开始，因此首个元素的索引号是 0 而不是 1。下面的例子选取第二个 <p> 元素（索引号 1）：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $("p").eq(1);
>});
>```

### jQuery filter() 方法
>filter() 方法允许您规定一个标准。不匹配这个标准的元素会被从集合中删除，匹配的元素会被返回。
>下面的例子返回带有类名 "url" 的所有 <p> 元素：
>
>示例：
>
>```javascript
>$(document).ready(function(){
>  $("p").filter(".url");
>});
>```

### jQuery not() 方法
>not() 方法返回不匹配标准的所有元素。
>提示：not() 方法与 filter() 相反。
>下面的例子返回不带有类名 "url" 的所有 <p> 元素：
>
>示例:
>
>```javascript
>$(document).ready(function(){
>  $("p").not(".url");
>});
>```

## jQuery - AJAX 简介
>AJAX 是与服务器交换数据的技术，它在不重载全部页面的情况下，实现了对部分网页的更新。

### 什么是 AJAX？
>AJAX = 异步 JavaScript 和 XML（Asynchronous JavaScript and XML）。
简短地说，在不重载整个网页的情况下，AJAX 通过后台加载数据，并在网页上进行显示。
使用 AJAX 的应用程序案例：谷歌地图、腾讯微博、优酷视频、人人网等等。

### 关于 jQuery 与 AJAX
>Query 提供多个与 AJAX 有关的方法。
通过 jQuery AJAX 方法，您能够使用 HTTP Get 和 HTTP Post 从远程服务器上请求文本、HTML、XML 或 JSON - 同时您能够把这些外部数据直接载入网页的被选元素中。

## jQuery - AJAX load() 方法
### jQuery load() 方法
>jQuery load() 方法是简单但强大的 AJAX 方法。
>load() 方法从服务器加载数据，并把返回的数据放入被选元素中。
>
>语法:
>
>```javascript
>$(selector).load(URL,data,callback);
>```
>
>必需的 *URL* 参数规定您希望加载的 URL。
>可选的 *data* 参数规定与请求一同发送的查询字符串键/值对集合。
>可选的 *callback* 参数是 load() 方法完成后所执行的函数名称。
>这是示例文件（"demo_test.txt"）的内容：
>
>示例:
>```javascript
><h2>jQuery AJAX 是个非常棒的功能！</h2>
><p id="p1">这是段落的一些文本。</p>
>```
>下面的例子会把文件 "demo_test.txt" 的内容加载到指定的 <div> 元素中：
>
>示例:
>
>```javascript
>$("#div1").load("demo_test.txt");
>```
>
>也可以把 jQuery 选择器添加到 URL 参数。
>下面的例子把 "demo_test.txt" 文件中 id="p1" 的元素的内容，加载到指定的 <div> 元素中：
>
>示例:
>
>```javascript
>$("#div1").load("demo_test.txt #p1");
>```
>
>可选的 callback 参数规定当 load() 方法完成后所要允许的回调函数。回调函数可以设置不同的参数：
>>* responseTxt - 包含调用成功时的结果内容
>>* statusTXT - 包含调用的状态
>>* xhr - 包含 XMLHttpRequest 对象
>
>下面的例子会在 load() 方法完成后显示一个提示框。如果 load() 方法已成功，则显示"外部内容加载成功！"，而如果失败，则显示错误消息：
>
>示例:
>
>```javascript
>$("button").click(function(){
>  $("#div1").load("demo_test.txt",function(responseTxt,statusTxt,xhr){
>    if(statusTxt=="success")
>      alert("外部内容加载成功!");
>    if(statusTxt=="error")
>      alert("Error: "+xhr.status+": "+xhr.statusText);
>  });
>});
>```

## jQuery - AJAX get() 和 post() 方法
>jQuery get() 和 post() 方法用于通过 HTTP GET 或 POST 请求从服务器请求数据。

### HTTP 请求：GET vs. POST
>两种在客户端和服务器端进行请求-响应的常用方法是：GET 和 POST。
>>* GET - 从指定的资源请求数据
>>* POST - 向指定的资源提交要处理的数据
>
>GET 基本上用于从服务器获得（取回）数据。注释：GET 方法可能返回缓存数据。
POST 也可用于从服务器获取数据。不过，POST 方法不会缓存数据，并且常用于连同请求一起发送数据。

### jQuery $.get() 方法
>$.get() 方法通过 HTTP GET 请求从服务器上请求数据。
>
>语法:
>
>```javascript
>$.get(URL,callback);
>```
>
>必需的 *URL* 参数规定您希望请求的 URL。
>可选的 *callback* 参数是请求成功后所执行的函数名。
>下面的例子使用 $.get() 方法从服务器上的一个文件中取回数据：
>
>示例:
>
>```javascript
>$("button").click(function(){
>$.get("demo_test.php",function(data,status){
>alert("数据: " + data + "\n状态: " + status);
>});
>});
>```
>$.get() 的第一个参数是我们希望请求的 URL（"demo_test.php"）。
>第二个参数是回调函数。第一个回调参数存有被请求页面的内容，第二个回调参数存有请求的状态。
>提示： 这个 PHP 文件 ("demo_test.php") 类似这样：
>
>demo_test.php 文件代码:
>
>```php
><?php
>echo '这是个从PHP文件中读取的数据。';
>?>
>```

### jQuery $.post() 方法
>$.post() 方法通过 HTTP POST 请求向服务器提交数据。
>语法:
>
>```javascript
>$.post(URL,data,callback);
>```
>必需的 *URL* 参数规定您希望请求的 URL。
>可选的 *data* 参数规定连同请求发送的数据。
>可选的 *callback* 参数是请求成功后所执行的函数名。
>下面的例子使用 $.post() 连同请求一起发送数据：
>
>示例:
>
>```
>$("button").click(function(){
>$.post("/try/ajax/demo_test_post.php",
>{
>   name:"菜鸟教程",
>   url:"http://www.runoob.com"
>},
>function(data,status){
>   alert("数据: \n" + data + "\n状态: " + status);
>});
>});
>```
>$.post() 的第一个参数是我们希望请求的 URL ("demo_test_post.php")。
>然后我们连同请求（name 和 url）一起发送数据。
>"demo_test_post.php" 中的 PHP 脚本读取这些参数，对它们进行处理，然后返回结果。
>第三个参数是回调函数。第一个回调参数存有被请求页面的内容，而第二个参数存有请求的状态。
>提示： 这个 PHP 文件 ("demo_test_post.php") 类似这样：
>
>demo_test_post.php 文件代码:
>
>```php
><?php
>$name = isset($_POST['name']) ? htmlspecialchars($_POST['name']) : '';
>$url = isset($_POST['url']) ? htmlspecialchars($_POST['url']) : '';
>echo '网站名: ' . $name;
>echo "\n";
>echo 'URL 地址: ' .$url;
>?>
>```
>
>







