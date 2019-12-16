[TOC]
# ES6笔记

## 简介

ECMAScript(简称ES6)是JavaScript语言的下一代标准,在2015年6月.他的目标,使得JavaScript语言可以用来编写复杂大型的应用程序,成为企业级开发语言. 

## let和const
### let关键字的语法规范 
>用于声明变量
>let声明的变量不能重复声明
>不存在变量提升,临时死去

### 块级作用域
>每次循环都会生成一个作用域
>let关键字会自动创建一个块状作用域
>代替闭包的一些功能
####  什么情况会产生块级作用域?
>像for,if,else,while等代码块产生块状作用域

### const关键字
>用于声明常量:变量名使用大写
>常量的值一旦声明就不能修改
>const声明的常量同样存在作用域(局部作用域,块级作用域,全局作用域)

### 全局作用域和顶层对象
>ES6中去掉了顶层对象的概念
>为了向下兼容,在全局作用域中使用var声明的变量和直接声明的函数任然是顶层对象的属性和方法,
>而使用let和const声明的变量不再属于顶层对象

## 变量的解构赋值
### 变量的结构赋值-数组的解构
>解构赋值语法格式:
>let 数组元素 = 数组值
>例:
>let[a,b,c] = [101,200,300] 
>复杂数组的模式匹配:
>例:
>let [ba,[[bb],[bc,bd]]] = [100,[[200],[300,400]]];
>两边模式不能匹配:
>例1:
>let[n1, ,n2] = [1,2,3];
>例2:
>let[n3,n4,n5] = [10,20]; 
>结构赋值可以有默认值:
>let [var1,var2='小红'] = ['小马',小钟];

### 对象的解构赋值
>语法格式:
>let {对象名1,对象名2,...} = {对象名1:值1,对象名:值2....}
>例:
>let {bar,foo} = {bar:'lili',foo:100}
>完整的对象解构赋值
>let [bar:bar,foo:foo]  = {bar:'honghong',foo:'yanyan'}
>对象解构 复杂形式
>let obj = {
    p: [
        'Hello',{y:'world'}
    ]
};
let {p:[x,{y:y}]} = obj;

### 特殊对象的解构赋值
>字符串可以被看做是由字符组成的数组
>例:
>let [a,b,c,d,e,f] = ''hellow';
>输出结果为: a = h,b = e,...
>把字符串当成对象
>let {length:len} = 'world';  //用于获取字符串的长度
>输出结果为:5

### 实际应用
>案例1:交换两个变量的值
>
>```javascript
>//交换两个变量的值
>let a = 100;
>let b = 200;
>
>[a,b] = [b,a]
>```
>
>案例2:提取json中的数据
>```javascript
>//提取json中的数据
>let jsonData = {
>id:42,
>status:'ok',
>data[12,5,67,8]
>}
>let {id,status,data} = jsonData;
>```
>案例3:提取函数中的默认值
>```javascript
>//提取函数中的默认值
>function getJson({
>url,
>type = 'get',
>data = '';
>async = true
>}){
>console.log(url,type,data,async)
>}
>
>getJson({
>url : "http://1.php"
>data : "a = 100"
>});
>```
>ES6模块
>```javascript
><script>
>    import {firstName,lastName,year} from './modul.js';
></script>
>modul文件:
>export var firstName = "Lee";
>export var lastName = "DaChui";
>export var firstName = "1985";
>```

## for-of语法解构
### 语法格式:
>for{变量名 of 数组名/...}{
	语句块
}
例:
>```javascript
>let arr = ['red','green','blue']
>for(let val of arr){
>	console.log(val);
>}
>```

### for-of可以遍历的内容
>1.遍历字符串
>```javascript
>for(let val of 'abcdef'){
>	console.log(val);
>}
>```
>2.遍历节点列表
>```javascript
>var lis = document.querySelectAll('ul li');
>for (let ele of lis){
>    console.log(ele);
>}
>```
>3.类数组对象
>4.argument
>5.map
>6.set

### for of 与 其他遍历方式的区别
>1.for...in : 可以遍历的类型比for-in更多,for of直接遍历出值,for in遍历出来的是key
>2.forEach方式:可以遍历出更多的类型,可以使用break和continue等结束语句

### Iterator 遍历器
>ES6定义的一个接口
>Array实现了Interator的接口
>实现遍历器接口的数据类型都可一用于for of

## 字符串的新特性
### 模板字符串
>语法格式:
>let 变量名 = `
>字符串内容;
>`;
>例:
>
>```javascript
>let html = ' 
><div>
>	<p>hahaha<p>
>	<a href="#">heiheihei</a>
><div>
>';
>```
>ps:在字符串中使用反引号需要转义

#### 模板字符串的特点
>1. 定义比较长,复杂字符串如html代码
>2. 模板字符串中写`需要转义
>3.模板字符串中插入变量${变量名}
>4.模板字符串中插入函数调用${函数名()}

### repeat方法
>重复输出字符串

### 字符串补全长度的方法padStart() padEnd()
#### padStart()
>在字符串前面进行补全
>语法格式:
>padStart(长度,补全内容) //默认使用空格补全

#### padEnd()
>在字符串后面进行补全
>语法格式:
>padEnd(长度,补全内容) //默认使用空格补全

### 字符串包含验证 include() / startsWith() / endsWith()
>include() :是否包含指定字符
>startsWith():s是否以指定字符开头
>endsWith():是否以指定指定字符结尾

## 函数新增特性
### 函数的默认值
>ES6中函数可以直接添加默认值  
>例:
>
>```javascript
>function fn (a,b='小明'){
>	console.log();
>}
>```

### rest参数
>命名规则:
>...变量名
>会的到一个純数组

### 箭头函数
>1.等同于
>let fn = val => val;
>2.实现两个数之和
>let sum = (num1,num2)=>num1+num2;
>console.log(sum(1,5)); 
>3.箭头函数 函数体多个语句
>let demo = (num)=>
>特点:
1.简化函数的声明
2.参数超过1个加()
3.函数体超过1行,加{},自己写return

#### 箭头函数的作用
>1.简化函数回调
>2.箭头函数中的this是函数声明时所在的对象

### 数组的新增特性
#### 扩展运算符(...)
>概念:扩展运算符相当于rest参数的逆运算,把数组转化为用逗号分隔的参数列表
>实际作用:
>1. 复制数组
>
>```javascript
>//复制数组
>let a = [10,20,30];
>//复制a数组 赋值给b
>let b = [...a ];
>```
>2.合并数组
>
>```javascript
>let a = ['刘姥姥','马姥姥',找姥姥];
>let a = ['刘奶奶','刘奶奶',王大爷];
>let c = [100,101,102,103];
>//ES5
>let newArgs = a.conact (b,c);
>//ES6扩展运算符
>let newList = [...a,...b,...c];
>```
>3.扩展运算符与结构数组一起使用
>
>```javascript
>let [a,b,...args] = [1,2,3,4,5,6];
>```
>args的值为:3,4,5,6
>
>4.扩展运算符 作用于字符串
>
>```javascript
>let args = [..."hellow"];
>```
>args的值为:将hellow转化为字符数组

 ## Array构造函数的新增方法
### Array.from()
>可以把类数组对象和实现了迭代器接口的数据类型装换成真正的对象

### Array.of()将一组值转换为数组
>将一组值转换为数组

## 数组对象新增的方法
>find() 返回数组中第一个满足条件的元素,参数是回调函数
>findIndex() 返回数组中第一个满足条件的元素索引,参数是回调函数
>entries()  帮助数组遍历数组中的key和value,使用for...of循环
>keys() 遍历数组中的所有索引值
>values()  chrome未能实现
>includes() 表示数组中是否包含某个指定的值

## 对象的新增特性
### 属性的简洁表示
>属性名和遍量名相同时可以只写一个

### Object.is()
>用于比较,类似于 ===(全等符号)
>0和-0使用Object.is()判断 不相等
>NaN和NaN使用Object.is()判断 相等

### Object.assign() 
>用于合并对象
>Object.assign(目标对象,源对象) 
>例:将两个对象合并到一个新的对象
>
>```javascript
>let res = Object.assign({},obj1,obj2);
>```

### Object.keys()
### Object.values()
### Object.entries()

## Set/Map数据解构
### set数据结构
>实现了Interator接口
>定义:
>类似于数组,但是起成员是唯一的
>语法格式:
>let 变量名 = new set([值1,值2,值3,...])

### Set构造函数
>可以接收一个数组
>可以接收所有实现了Interator接口的数据解构
>实现数组去重实例:
>
>```javascript
>//实现数组去重1
>let arr = [10,23,4,23,10,23];
>
>let newArr = [...new Set(arr)];
>console.log(newArr);
>//实现数组去重2
>let arr = [10,23,4,23,10,23];
>
>let newArr = Array.from(new Set(arr));
>console.log(newArr);
>
>```

### set数据类型的属性
>查看长度:size

### set数据类型的方法
>add:向set中添加一个成员
>语法:
>对象名.add(值);
>>delete:向set中删除一个成员
>语法:
>对象名.delete(值);
>has:判断set中是否存在元素
>语法:
>对象名.has(值);
>clear:清空set
>语法:
>对象名.clear;
>forEach():
>key():
>values():
>entries():

### set数据类型的遍历

### WeakSet
>定义
>与Set类似,成员唯一,成员必须是变量
>WeakSet中的对象都是弱引用
>不能遍历,也没有size属性
>方法:
>add():
>delete():
>has():

### Map数据结构
>定义:
>Map跟对象类似,键值对组成的集合,键的类型可以是任意类型

### Map数据结构的构造函数
>构造函数的参数可以是数组,数组是二维数组,元素数组两个元素,key value
>例:
>
>```javascript
>let m = new Map([["name",'lili'],["title",'hello world'],[Window,'haha']]);
>```

### Map数据结构方法
>get(key):获取索引值的数据
>set(key,value) 修改/添加
>has(key):是否存在
>clear():清空

### Map数据结构的遍历

### WeakMap
>定义:
>键是必须对象
>键所执行的对象是弱引用
>不可遍历 没有实现Interator接口

### WeakMap的方法
>set():
>get():
>has():
>clear();
>delete();

## Promise

### Promise基础
>js中的异步操作:
>1. ajax请求
>2. 浏览器事件
>3. 定时

### 回调函数

### 回调地狱
>回调函数嵌套回调函数

### Promise
>解决回调地狱
>像同步操作那样去执行异步操作

### Promise的构造方法
>构造函数必须接收一个函数作为参数,函数可以接收参数

### Promise的原理
>原理:
>一个Promise实例(对象),代表一个异步操作
>promise通过状态去管理异步操作
>语法格式resolve,reject不可变
>```javascript
>let p = new Promise(function(resolve,reject){
>
>});
>```
>实例:
>
>```javascript
>let p = new Promise(function(resolve,reject){
>	
>	setTimeout(function(){
>		//操作
>		resolve("数据");
>	},2000)
>});
>
>p.then(function(res){
>	console.log(res);
>});
>```

### 状态
>pending(进行中)
>fulfilled(已完成) resolve()函数执行
>rejected()已经失败 reject() 函数执行

###  Promise对象的方法
>1. then():then 方法接收两个函数作为参数，第一个参数是 Promise 执行成功时的回调，第二个参数是 Promise 执行失败时的回调，两个函数只会有一个被调用。
>2. catch():参数是一个回调函数,promise转状态时为rejected时调用
>3. all() 参数是数组,数组成员都是Promise对象.所有Promise对象状态改变,才执行then.
>4. race() 参数也是数组,数组成员都是Promise对象,最快的Promise状态改变,其他的Promise 停止

### jQuery使用Promise

## Class
### 基本使用
>JavaScript prototype 属性:
>定义和用法
prototype 属性使您有能力向对象添加属性和方法。
语法
object.prototype.name=value

### 构造函数

### Class基本语法

### Class的特点
>clas的里面必须包含constructor,属性添加到constructor中\
>class可以使用new实例化
>class本质仍然是构造函数,语法糖
>this的指向,class将来的实例

### 静态方法

### Class的继承
>特点:
>使用extends关键字
>子类会继承父类的属性和方法
>子类中的属性和方法会覆盖父类的(如果同名)

### super关键字
>子类中声明constructor的时候,里面必须调用super();
>super作为函数,必须在constructor中使用,代表父类的constructor再执行一遍.
>super作为对象,在普通子类方法中使用

## ES6的模块化
>CommonJS标准  node.js
>AMD标准                require.js
>ES6模块

### 定义模块
>export 提供方法 
>实例:
>
>```javascript
>//模块大量操作
>export var lasName = "MICH";
>export var firstName = "jackson";
>
>export function getJson(){
>	console.log("getJson");
>}
>```
>
>
>


### 引入模块
>import:引入模块的方法
>
>实例:
>
>```javascript
><script type="module">
>	//引入模块
>	import {lastName,firstName,getJson} from "module01.js"
><script>
>```
>
>

