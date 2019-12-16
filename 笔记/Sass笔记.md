[TOC]

# Sass
## css预处理器
## 为什么使用Sass
1. 使用变量
2. 自动转换RGBA颜色
3. 忘记浏览器前缀
4. 嵌套规则
5. media query更简单
6. 自动压缩CSS
## Sass与css
> CSS并不能算是一门真正意义上的"编程"语言,无法完成嵌套,继承,设置变量等工作
>
> 为了解决CSS的不足,开发者想到了编写一种css进行预处理的"中间语言"

## .sass与.scss
>sass最初是为了配合haml而设计,所以和haml有着一样的缩进风格
>从第三代开始,保留缩进式风格,完全向下兼容普通的css代码

## 什么是Compass
>Compass是Sass的工具库
>在Sass的基础上封装了一系列有用的模块和模板,补充Sass的功能.Compass与Sass的关系类似于jQuery与JavaScript的关系

## Sass与Compass能做什么
### Sass
>1. 使用变量
>2. 自动转换RGBA的颜色值
>3. 忘记浏览器的前缀
>4. 嵌套规则
>5.  media query更简单
>6. 自动压缩CSS
### Compass
>1. reset
>2. css3
>3. layout
>4. typography
>5. utilities

## Sass语法
### Sass基础
#### 创建Sass工程
> 1. 使用Sass创建
>   2.使用Compass创建
>   Compass create :使用该命令创建工程
>
>   可选参数:--bare 创建一个纯净的Sass工程
>
> 2. 带参数创建:compass create --bare--sass-dir "sass" --css-dir "css" --image-dir "img" --javascript-dir "js"

#### 使用命令行
> 1. 编译Sass:sass <sass file>  <css file>
>> 可以指定输出风格: sass <sass file> <css file> --style[nested|expanded|compact|compressed]
> 2. 监视Sass文件:sass --watch <sass file>:<css file>
> 3. 监视文件夹: sass --watch <sass floder>:<css floder>
> 4. 编译Sass:compass compile
> > 此命令只会编译有变化的Sass文件,如果要强制编译所有的Sass文件,可以使用:
> > compass compile --force
> 5.监视文件夹:compass watch
> 6.四种输出风格
> > nested
> > expanded
> > compact
> > compressed

#### 理解config.rb

#### Sass的注释语法
>1.  //注释
>2.  /**/注释
>> /*!xxx*/ 重要注释,压缩模式也会编译到css文件中
>>
>> 3.  中文注释

#### Sass变量
>1. 局部变量
>2. 全局变量
>> $color: red !global;
>3. 变量默认值
>> $color: red !default;
>4. 多值变量
>> $colors: red blue_green;
>> color: nth($colors,1);
>> 
>>$map:(key1:value1,key2:value2);
>>map-get(key1);
>5. 变量特殊用法
>>1. 变量用在属性或者选择器上,使用#{变量名}
>>2. 变量用中横线,还是下划线,取决与你的喜好,都代表同一个变量

#### 样式导入
>1. 部分文件
>>专门为导入而编写的sass文件,并不需要生成对应的独立文件,这个时候sass如何判别呢?
>>依靠约定,sass局部文件的文件名以下划线开头
>>局部文件可以被多个不同的文件引用.当一些样式需要在多个页面甚至多个项目使用时,这非常有用.在这种情况下,有时需要在你的样式表中对导入的样式稍作修改,sass有一个功能刚好解决这个问题,即默认变量
>2. 嵌套导入
>3. 原生CSS导入
>>1. 被导入的文件名字以.css结尾
>>2. 被导入文件的名字是一个URL地址(比如http://xxx/css.css)
>>3. 被导入文件的名字是CSS的url()值

#### 嵌套
>1. 选择器嵌套
>2. 属性嵌套
>3. &--引用父选择器
>4. @at-root,跳出嵌套
>>默认@at-root只会跳出选择器嵌套,而不能跳出@media或@support,如果跳出这两种,则需使用@at-root(without:media),@at-root(without:support).这个语法关键词有四个 : all(表示所有),rule(表示常规CSS),media(表示media).support(表示support,因为@support目前还无法广泛使用,所以不在此表).我们默认的@at-root其实就是@at-root(without:rule).
>
>5. @at-root 与 &

#### 继承
>1. 简单继承
>>继承语法格式: @extend 样式选择器
>2. 多继承
>>语法1: 多个@extend
>>语法2: @extend selector1,selector2
>3. 链型继承
>
>   ```scss
>    /*! 链式继承 scss文件*/
>   .one{
>       border: 1px solid red;
>   }
>   
>   .two{
>       @extend .one;
>       color: red;
>   }
>   
>   .three{
>       @extend .two
>       font-size:12px;
>   }
>    
>   ```
>
>   ```css
>    /*! 链式继承 css文件*/
>   .one, .two, .three{
>   	border: 1px solid red;
>   }
>   
>   .two, .three{
>       color: red;
>   }
>   
>   .three{
>       font-size:12px;
>   }
>   ```
>

>4. 继承的局限性
>>虽然能继承的选择器数量很多,但也有很多是不被支持的.如包含选择器(.one .two)或者是相邻兄弟选择器(.one+.two);
>>如果继承的元素是a,恰巧这个元素a又有hover状态的形式,那么hover状态也会被继承
>5. 继承交叉合并
>>没有在同一个父级下,会产生交叉合并的编译结果
>>
>>```scss
>>/*! 交叉继承 scss文件*/
>>a span{
>>    font-weight: blod;
>>}
>>div .content{
>>    @extend span;
>>}
>>
>>```
>>
>>```css
>>/*! 交叉继承 css文件*/
>>a span, a div .content, div a .content{
>>    font-weight: blod;
>>}
>>
>>```
>>
>6. 继承的作用域
>>继承在指令中是有作用域问题的,继承是无法使在指令(@media)之外的选择器继承的,要是继承就只能写在指令中

#### 占位选择器%
>>优势在于:如果不调用不会有过多的css文件,避免了以前在一些基础的文件中预定义了很多基础样式,然后实际应用中不管是否使用了@extend去继承相应的样式,都会解析出来所有的样式.占位选择器以%标识定义,通过@extend调用

### Sass进阶
#### 数据类型
>1. Number
>2. String
>3. List
>4. Map
>5. Color
>6. Boolean
>7. Null
#### 变量操作
>1. ==,!=
>>所有数据类型都支持
>2. <,>,<=,>=
>>仅仅支持数字类型
>
>3. +,-,*,/,%
#### Mixin
>1. 简单扩展
>
>   ```scss
>   /*! Scss文件*/
>   @mixin cont($color: red;,$fontSize: 14px){
>       color: $color;
>       font-size: $fontSize;
>   }
>       
>       body{
>           @include cont($fontSize: 18px);
>           }
>   ```
>
>   ```css
>   /*! css文件*/
>   body{
>       color: red;
>       font-size: 18px;
>   }
>   ```
>
>   
>
>2. 传递多值参数
>
>   ```scss
>   /*! Scss文件*/
>   //实现多浏览器适应
>   @mixin box-shadow($shadow...){
>   	-moz-box-shadow: $shadow;
>       -webkit-box-shadow: $shadow;
>       box-shadow: $shadow;
>   }
>   
>   .shadows{
>       @include box-shadow(0px 4px 4px #555, 2px 6px 10px #6dd3ee);
>   }
>   //在定义时加入...时传参
>   ```
>
>   ```css
>   /*! css文件*/
>   .shadows{
>       -moz-box-shadow: 0px 4px 4px #555, 2px 6px 10px #6dd3ee;
>       -webkit-box-shadow: 0px 4px 4px #555, 2px 6px 10px #6dd3ee;
>       box-shadow: 0px 4px 4px #555, 2px 6px 10px #6dd3ee;
>   }
>   ```
>
>3. 传递内容
>
>   ```scss
>   /*! Scss文件*/
>   @mixin style-for-iphone{
>       @media only screen and (min-device-width: 320px) and (max-device-width:568px){
>           @content;
>       }
>   }
>   
>   @include style-for-iphone{
>       font-size: 12px;
>   }
>   ```
>
>   ```css
>   /*! css文件*/
>   @media only screen and (min-device-width: 320px) and (max-device-width: 568px){
>       font-size: 12px;
>   }
>   ```
>
>   

#### 内置函数
>1. rgb(),rgba()
>2. lighten().darken()
>将颜色变浅或加深
>3. str-length(),str-index()
>求字符串长度,求字符串index
#### 自定义函数
>语法格式实例:
>
>```scss
>@function double($width){
>    @return $width * 2;
>}
>```

#### @debug,@warn,@error
>打出信息,类似于js的console 
>

### Sass高级
#### @if
#### @for
#### @while
#### @each