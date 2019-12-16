[TOC]
# Node.js笔记
## Node.js的下载安装
>下载地址:https://nodejs.org/en/download/
>安装:
>Ubuntu 源码安装 Node.js
以下部分我们将介绍在 Ubuntu Linux 下使用源码安装 Node.js 。 其他的 Linux 系统，如 Centos 等类似如下安装步骤。

>在 Github 上获取 Node.js 源码：

>$ sudo git clone https://github.com/nodejs/node.git
>Cloning into 'node'...
>修改目录权限：
>$ sudo chmod -R 755 node
>使用 ./configure 创建编译文件，并按照：
 >$ cd node
>$ sudo ./configure
>$ sudo make
>$ sudo make install
>查看 node 版本：
$ node --version
v0.10.25
Ubuntu apt-get命令安装
命令格式如下：
sudo apt-get install nodejs
sudo apt-get install npm

## Node.js的特性
>1. 单线程
>2. 非阻塞I/O
>3.事件驱动event-driven

## 创建http服务
>// 创建一个HTTP服务,接收用户的响应
>实例:
>```js
>// 创建一个HTTP服务,接收用户的响应
>
>//引入模块
>let http = require("http");
>
>/*
>*
>*
>* */
>let server = http.createServer(function (req,res) {
>    //req 表示 请求
>    //res 表示 响应
>
>    //设置响应头
>    res.writeHead(200,{"Content-type" : "text/html;charset=utf-8"})
>    /*
>    * res.end–》（data，encoding，callback）也可以不传参
>    * data.只能发送Buffer和string的数据
>    * encodeding 类型的数据
>    * 此方法向服务器发出信号，表明已发送所有响应头和主体，该服务器应该视为此消息已完成。 必须在每个响应上调用此 response.end() 方法。
>    * */
>
>    //end结束响应
>    res.end("<h1>Hello Node.js 哈哈哈</h1>")
>});
>
>//监听端口
>//第二个参数指定链接访问
>server.listen(3000,function () {
>    console.log("Http Server running on port 80");
>});
>```

## 简单路由控制
>```javascript
>//引入模块
>let http = require("http");
>let fs = require("fs");
>
>//创建HTTP服务
>http.createServer(function (req,res) {
>    //req 请求
>    //res 响应
>    if (req.url === "/favicon.ico"){
>        return false;
>    }
>
>    if (req.url === "/" || req.url === "/index.html"){
>        //读取文件
>        fs.readFile("../index.html",function (err,data) {
>            //err 错误对象
>            //data 读取文件中的数据
>            res.writeHead(200,{"Content-type" : "text/html;charset=utf-8"});
>            res.end(data);
>        });
>    }else if (req.url === "/detail.html"){
>        fs.readFile("../detail.html",function (err,data) {
>            //err 错误对象
>            //data 读取文件中的数据
>            res.writeHead(200,{"Content-type" : "text/html;charset=utf-8"});
>            res.end(data);
>        });
>    }else if(req.url === "/img/01.jpg"){
>        //读取文件
>        fs.readFile("../img/01.jpg",function (err,data) {
>            //err 错误对象
>            //data 读取文件中的数据
>            res.writeHead(200,{"Content-type" : "image/jpeg"});
>            res.end(data);
>        });
>    }else if (req.url === "/style/style.css"){
>        //读取文件
>        fs.readFile("../style/style.css",function (err,data) {
>            //err 错误对象
>            //data 读取文件中的数据
>            res.writeHead(200,{"Content-type" : "text/css"});
>            res.end(data);
>        });
>    }else{
>        //设置响应头
>        res.writeHead(404,{"Content-type" : "text/html;charset=utf-8"});
>        res.end("<h1>不存在</h1>");
>    }
>    console.log(req.url);
>
>}).listen(3000,function () {
>    console.log("HTTP Server is running on 3000")
>})
>```

## Node模块系统和如何加载模块
### Node的系统
>1. 在Node.js的模块系统中,每个文件都是独立的模块
>2. 每个模块都会有自己的作用域

### 加载模块
>1 .加载核心模块使用require方法:
>语法格式:require("模块名");
>实例:
>const http = require("http");
>2.加载第三方模块
> 先使用:npm install 模块名 =>安装模块
> 再使用:require("模块名"); 导入模块
>实例:
> //第三方的模块
const random = require("randomatic");
console.log(random("*",20));
>3. 加载自定义模块
>先定义一个自己的模块
>再使用require("模块名"); 导入模块
>如何使用别的模块的变量
>在模块中定义变量时加上:export
>例:
>var a = 100;
>exports.a = a;
>引入:
>const aModule = require("./03");
>console.log(random(aModule.a);

### 自定义模块
>```
>// 导出
>exports.属性名 = 值/变量;
>exports.属性名 = 值/变量;
>exports.属性名 = 值/变量;
>
>//另外一种导出方式
>module.exports = 对象;
>module.exports = 类/构造函数/函数;
>```

### 模块路径
>1. "./","../"."/"开头的是自定义模块,没有这些开头的是核心模块,和第三方模块
>2. 导入第三方模块和核心模块,不需要指定路径,写模块名就可以
>3. 导入第三方模块,会从本目录的"node_modules"目录内查找,如果没有,会从上一个目录下的"node_modules"中查找,直到根目录下的"node_modules"
>4. 导入自定义模块,如果模块是个文件,没有同名的文件,会依次加上后缀".js",".json",".node"
>5. 导入自定义模块,模块是目录,导入指定目录名,如果模块中有package.json并指定了"main"选项,就以该文件为入口,如果没有package.json或者,没有指定main,就会加载index.js还没有加载index.node

## NPM
### npm的使用
>1. Node Package Manager意为Node报管理工具/Node模块管理工具
>2. 使用场景
>	允许用户从NPM服务器下载别人编写的第三方包到本地使用.
>	允许用户从NPM服务器下载并安装别人编写的命令行程序到本地使用
>	允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用
>	官方网站:https://www.npmjs.com/
>	包质量对比:https://npms.io

### npm常用操作
>1. 安装模块
>
>   ```
>   npm  install  包名
>   ```
>2. 安装指定版本号
>   ```
>   npm  install  包名@版本号
>   npm  install  包名@主版本号.*.*
>   npm  install  包名@主版本号.次版本号.*
>   ```
>3.  查看已安装的包
>   ```
>   npm  list       #  查看自己已安装的包
>   npm list 包名    #查看具体的包  包版本
>   ```
> 4.  删除模块
>   ```
>	npm uninstall 包名
>   ```
> 5.  更新模块
>   ```
>	npm update 包名
>	npm update   #更新所有
>   ```
>6. 搜索模块
>   ```
>	npm search 包名
>   ```
>7. 查看包信息
>   ```
>	npm info 包名
>   ```

### npm的全局安装
>1. 命令
>
>```
>npm install 包名 -g  #全局安装
>npm uninstall 包名 -g  #全局删除
>npm list -g  #显示
>```
>2. 查看全局目录
>   ```
>   npm  config get prefix
>   ```
>3. 修改全局安装路径
>   ```
>   npm  config set prefix 新的目录
>   ```

### 使用淘宝npm镜像
>可以使用淘宝定制的cnpm(.gzip压缩支持)命令行工具代替默认npm:
>  ```
>   npm  install -g cnmp .....
>   ```
>   shiyou使用淘宝镜像使用cnpm指令

## package.json
### package.json使用
>1. 项目初始化
>
>   ```
>   npm init
>   ```
>2. package的属性说明
>- name:包名.
>- version :包的版本号
>- description: 包的描述
>- homepage: 包的官网url
>- author: 包的作者姓名
>- contributors: 包的其他贡献者名
>- dependencies: 依赖包列表,如果依赖包没有安装,npm会自动将依赖包安装在node_module目录下
>- repository: 包代码存放的地方类型,可以是git或svn,git可在github上
>- main: main字段指定了程序的主入口文件,require(moduleName就会加载这个文件,这个字段的默认值是根目录下的index.js
>- keywords :关键字

### 版本号
>```
>> 1.1.1 版本必须比1.1.1大
>>= 1.1.1 版本>=1.1.1
>< 1.1.1
>< =1.1.1
>* 表示最高版本
>~1.1.1  安装1.1.x 的最新版本 补丁版本最新
>^1.1.1  安装1.x.x的最新版本 次版本和补丁版本都最新
>```
>ps:关于版本号,如jquery-1.12.4
>1是主版本号用于不兼容的API修复
>12是副版本号或此版本号用于向下兼容的功能修复
>4是补丁版本号用于向下兼容的bug修复

## 发布包
>1. 注册用户
>npm adduser
>2. 登录
>npm login   #登录
>npm logout   #退出登录
>npm whoami    #查看当前所有登录的用户
>3. 发布
>npm publish
>4. 取消发布
>npm unpublish 包名 --force

## Node全局对象
>1. 路径
>
>   ```
>   __filename:当前文件的目录
>   __dirname:当前文件所在的目录
>   ```

### console(控制台)
#### 占位符
>1. %s:字符串
>2. %d:数值(整数或浮点数)
>3. %i:integer
>4. %f :Floating point value
>5. %j:JSON,如果参数包含循环引用,则用字符串'[Circular]

### console对象属性
>1.log():日志
>2.count():计数
>3.count.countReset();重置计数
>4. dir():输出对象
>5. time(): 计算一段程序的运行时间
>6. timeEnd():计算一段程序的运行时间
>7. group():给下一行添加两个缩进
>8. groupEnd ():为下一行删除两个缩进
>9.error(): 错误
>10. warn():警告
>11. trace(): 调试

### 字符画
>1. figlet 包

### 定时器
#### 设置定时
>setTimeout(callback,delay[,args]);
setInterval(callback,delay[,args...]);
setImmediate(callback,[args]);

#### 取消定时
>clearTimeout(timeout)
>clearInterval(timeout)
>clearImmediate(immedate)

### Module模块
>1. exports: 模块中导出的放法,属性,类   module.exports === exports
>2. require(): 引入模块 module.require === require
>3.require.main: 得到直接使用node运行的模块
>4.parent: 父模块
>5.children: 子模块
>6.filename: 当前模块的路径
>7. id
>8. loaded: 是否加载
>9.paths: 模块可以加载的路径

### Process(进程)
#### 对象属性
>1. pid: 进程号
>2. title: 进程名
>3. argv: 命令行选项组成的数组
>4. argv0
>5. env: 得到环境变量信息
>6. execPath : node路径
>7. arch:CPU架构
>8. version: 版本号信息
>9. platform: 平台信息(电脑系信息)
>10. cwd() 返回进程工作目录
>11. memoryUsage(): 返回内存使用情况 单位byte
>12. exit(): 结束

#### 输入输出流
>1. process.stdin:输入
>
>   ```
>   process.stdout.write("ok");
>   ```
>
>   
>
>2. process.stdout:输出
>
>   ```
>   process.stdin.on('data',function (a) {
>       console.log("用户输入: " + a)
>   })
>   ```
>

#### Exit Code

### Buffer
#### 什么是Buffer
>读取或操作二进制流
>Buffer类的实例类似于整数数组,但Buffer的大小是固定的,且在V8堆外分配物理内存,Buffer的大小在被创建时确定,且无法调整
>由于Buffer对象占用的内存空间是不计算在Node.js进程空间限制上的,因此,我们也常常会使用Buffer来存储需要占用大量内存的数据
>实例:
>
>```javascript
>//创建Buffer
>
>//为buffer对象分配十个长度 每个元素自填充0
>//buffer的每个元素都是一个字节Byte(8bit)
>const bug1 =Buffer.alloc(10);
>
>bug1[0] = 10;
>console.log(bug1);
>console.log(bug1.length);
>
>
>//快速创建
>const buf2 = Buffer.from([1,2,260,4]);
>console.log(buf2.length);
>console.log(buf2);
>
>//utf-8编码
>const buf3 = Buffer.from('hello');
>console.log(buf3); 
>
>const buf4 = Buffer.from('你好');
>console.log(buf4);
>
>//直接从内存开辟空间,10个字节,没有初始化(可能会包含旧的数据) 速度比较快
>const buf5 = Buffer.allocUnsafe(10);
>buf5.fill('a');
>console.log(buf5.length);
>console.log(buf5);
>
>//拼接buffer
>const buf6 = Buffer.concat([bug1,buf2]);
>console.log(buf6);
>
>//buffer 输出字符串
>console.log(bug1.toString('hex'))
>
>```

## 文件系统
### 同步和异步
>所有的方法都有异步和同步的形式
>异步方法的最后一个参数都是一个回调参数,传给回调函数的参数取决于具体方法,但回调函数的第一个参数都会保留给异常,如果操作成功完成,则第一个参数null或Undefined.            
>实例:
>
>```javascript
>//导入fs模块
>const fs = require("fs");
>
>//同步和异步
>
>//重命名文件 rename()异步
>fs.rename("./test.txt","hello.txt",function (err) {
>    if (err) throw  err;
>    console.log("重命名成功");
>});
>
>//重命名文件 renameSync()同步
>fs.renameSync("./hello.txt","test.txt");
>console.log("重命名成功");
>
>//异步链操作
>//新建目录,把目录改名
>fs.mkdir("./test",function (err) {
>    if(err) throw err;
>    //重命名操作
>    fs.rename("./test","./new",function (err) {
>        if (err) throw err;
>        console.log("重命名成功")
>    });
>});
>// fs.rename("./test","./new",function (err) {
>//     if (err) throw err;
>//     console.log("重命名成功")
>// });
>```
>

### 文件目录操作
#### 判断文件/目录是否存在
>1.fs.access()
>
>2. fs.exitesSync()

#### 删除文件/目录
>1. fs.unlink()
>2. fs.ulninkSync()

#### 重命名 文件/目录
>fs.rename()
>fs.renameSync()

#### 查看 文件/目录 状态
>fs.stat()
>fs.statSync()
>fs.Stats类 : http://nodejs.cn/api/fs.html#fs_class_fs_stats

>实例:
>
>```javascript
>//导入模块
>const fs = require("fs");
>// fs.mkdir("./files",function (err) {
>//     if (err) throw err;
>//     console.log("目录创建成功");
>// })
>//判断文件/目录是否存在
>fs.access("./files",err => {
>    if (err){
>        console.log("文件或目录不存在")
>    }else{
>        console.log("文件或目录存在")
>    }
>});
>
>//重名名 删除
>
>//查看文件或目录状态
>fs.stat("./files/test.txt",(err, stat) => {
>    console.log(stat);
>});
>```
>

### 文件操作
#### 读文件
>fs.readFile()
>fs.readFileSync()

### 写文件
>fs.writeFile()
>fs.writeFileSync()

### 追加
>fs.appendFile()
>fs.appendFileSync()

### 拷贝文件
>fs.copyFile()
>fs.copyFileSync()

### 文件内容截断
>fs.truncate()
>fs.truncateSync()

实例:

```javascript
//导入模块
const fs = require("fs");
// fs.mkdir("./files",function (err) {
//     if (err) throw err;
//     console.log("目录创建成功");
// })
//判断文件/目录是否存在
fs.access("./files",err => {
    if (err){
        console.log("文件或目录不存在")
    }else{
        console.log("文件或目录存在")
    }
});

//重名名 删除

//查看文件或目录状态
fs.stat("./files/test.txt",(err, stat) => {
    console.log(stat);
});
```
### Node文件系统之文件监听
>1. fs.watchFile()
>2. fs.unWatchFile()
>3. fs.watch
>4.FSWatcher类:http://nodejs.cn/api/fs.html#fs_class_fs_fswatcher

>实例:
>
>```javascript
>//导入文件系统
>const fs = require('fs');
>
>//监听文件变化
>fs.watchFile("./files/test1.txt",{interval:1000},(curr,prev) =>{
>    console.log("当前文件的修改时间 " + curr.mtime + "当前的文件的大小:"  + curr.size);
>    console.log("以前文件的修改时间 " + prev.mtime + "以前的文件的大小:"  + prev.size);
>
>    //停止监听
>    fs.unwatchFile("./files/test1.txt");
>});
>
>//使用watch监听文件变化
>let watch =fs.watch("./files/test1.txt",(eventType,filename) => {
>    if (eventType === "rename") return;
>    //console.log(eventType,filename);
>});
>
>watch.on("change",function (eventType,filename) {
>    console.log(eventType,filename);
>});
>
>//监听目录变化
>fs.watch("./files",(eventType,filename) => {
>    console.log(eventType,filename);
>});
>```

### 文件字节操作
### 打开文件
>1. fs.open()
>2. fs.openSync()
>3. 文件打开模式
>>3.1 "r"以读取模式打开文件,如果文件不存在则发生异常.
>>3.2 "r+"以读写模式打开文件,如果文件不存在则发生异常
>>3.3"w"以写入模式打开文件.文件会被创建(如果文件不存在)或截断(如果文件存在)
>>3.4 "wx" 类似"w",但如果path存在,则失败
>>3.5 "w+" 以读写模式打开文件.文件会被创建(如果文件不存在)或截断(如果文件存在)
>>3.6 "wx+" 似"w+",但如果path存在,则失败
>>3.7 "a" 以追加的模式打开文件,如果文件不存在,则会被创建
>>3.8 "ax" 类似于a, 但如果path存在,则失败
>>3.9 "a+"以读取和追加模式打开文件.如果文件不存在,则会被创建
>>3.10 "ax+" 类似于"a+", 但如果path存在,则失败

### 读取
>1. fs.read()
>2. fs.readSync()

### 写入
>1. fs.write
>2. fs.writeSync

### 截断
>1. fs.ftruncate()
>2. fs.ftruncateSync()

### 关闭
>1. fs.close()
>2. fs.closeSync()

>实例:
>
>```javascript
>//导入模块
>const fis = require("fs");
>
>//打开文件,并读取
>fis.open("./files/test.txt","r",(err,fd) =>{
>    if (err) throw err;
>
>    //读取文件
>    let size = fis.statSync("./files/test.txt").size;
>    let buf = Buffer.alloc(size);//穿件Buffer
>    fis.read(fd,buf,0,size,0,(err,bytesRead,buffer) =>{
>        console.log("读取了" + bytesRead + "字节");
>        console.log(buffer);
>        console.log(buffer.length);
>        console.log(buffer.toString());
>    });
>    //
>    // //打开文件 并写入
>     fis.open("./files/test1.txt", "w", (err,fd) => {
>    //     if (err) throw err;
>    //
>    //     //写入 buffer形式
>    //     let buf = Buffer.from("嘿嘿嘿");
>    //     fis.write(fd,buf,0,buf.length,0,(err,bytesWritten,buffer) => {
>    //         if (err) throw err;
>    //         console.log(`写入了${bytesWritten}字节`);
>    //         console.log(buffer);
>    //     });
>         //写入 字符串形式
>         fis.write(fd,"锄禾嘿嘿嘿",0,(err,bytesWritten,string) =>{
>             if (err) throw err;
>             console.log(`写入了${bytesWritten}字节`);
>             console.log(string);
>         });
>     });
>});
>
>//打开并截断字符串
>fis.open("./files/test2.txt","w+",(err,fd) => {
>    if (err) throw err;
>    fis.ftruncate(fd,6,err =>{
>        if (err) throw err;
>        console.log("文件截断成功");
>    });
>});
>
>//追加内容
>fis.open("./files/test2.txt","a",(err,fd) => {
>    if (err) throw err;
>    fis.appendFile(fd,"从前又从前",(err) => {
>
>        fis.close(fd,(err) =>{
>            if (err) throw err;
>            console.log("追加成功");
>        });
>    });
>});
>```
>

### 目录操作
#### 创建目录
>1. fs.mkdir()
>2. fs.mkdirSync()

#### 读目录
>1. fs.readdir()
>2.fs.readdirSync()

#### 删除目录
>1. fs.rmdir()
>2. fs.rmdirSync()

>实例:
>
>```javascript
>//导入文件系统
>const fs = require("fs");
>const http = require("http");
>
>//读取目录
>/*
>fs.readdir("../node_modules",(err,files) => {
>    console.log(files);
>});*/
>
>http.createServer((req,res)=> {
>    res.writeHead(200,{"content-type" : "text/html;charset=utf-8"});
>    res.write("<ul>");
>    fs.readdir("./",(err,files) => {
>        files.forEach((file) => {
>            let state = fs.statSync(file);
>            let type = state.isFile() ? "file" : "directory";
>            res.write(`<li>${file} : ${type}</li>`)
>        });
>        res.write("</ul>");
>        res.end("OK");
>    });
>}).listen(8080,() =>{
>    console.log("Running")
>});
>```
>

### 第三方模块操作目录

### 文件流操作
#### 读取流
>1. fs.createReadStream()
>2. fs.writeStream: http://nodejs.cn/api/fs.html#fs_class_fs_readstream
#### 写入流
>1. fs.createWriteStream()
>
>2. fs.writeStream :http://nodejs.cn/api/fs.html#fs_class_fs_writestream
>  实例:
>
>  ```javascript
>  //导入文件系统
>  const fs = require("fs");
>  
>  //大型文件的复制
>  //创建可读流
>  const rs = fs.createReadStream("./files/test.txt");
>  //创建可写流
>  const ws = fs.createWriteStream("./files/test3.txt");
>  
>  let buf =  Buffer.alloc(0);
>  rs.on("data",(chunk) => {
>      //拼接从流中读取的内容
>      buf = Buffer.concat([buf,chunk]);
>  });
>  
>  rs.on("end",() => {
>      ws.write(buf);
>      ws.end();
>  });
>  
>  ws.on("close",() =>{
>      console.log("文件复制成功")
>  });
>  ```
>
>  
#### 使用流复制文件
>1. 用于复制大文件
>
>2. pipe管道 http://nodejs.cn/api/stream.html#stream_readable_pipe_destination_option
>  实例:
>
>  ```javascript
>  //大型文件复制
>  //导入 fs 模块
>  const fs = require("fs");
>  
>  const rs = fs.createReadStream("./files/test1.txt");
>  const ws = fs.createWriteStream("./files/test5.txt");
>  
>  //使用管道,把内容从可读流中进入可写流
>  rs.pipe(ws);
>  
>  ws.on("close",() => {
>      console.log("文件复制完成");
>  });
>  ```

### 其他操作
#### 绝对路径
>1.fs.realpath()
>2.fs.realpathSync()

### 综合案例:静态文件服务器

## Node核心模块
### path模块
>1. path.basename() 文件名+扩展名
>2. path.dirname()  返回路径名
>3. path.extname() 返回扩展名
>4. path.join() 拼接路径
>5. path.resolve() 拼接路径 返回绝对路径
>6. path.parse() 返回对象 解析
>7. path.format() parse的逆运算
>8. path.isAbsolute() 判断是否是绝对路径
>9. path.normalize() 把路径标准化
>10. path.relative()
>11. path.delimiter
>12. path.sep
>13. path.posix
>14. path.win32

### url模块
#### URL对象
>1. url.href  完整的URL
>2. url.origin  协议和主机名
>3. url.protocol  协议
>4. url.username  认证用户名
>5. url.password  认证密码
>6. url.host 主机名+端口号
>7. url.hostname  主机名
>8. url.port  端口号
>9. url.pathname  路径名
>10. url.search  ?以及后面的
>11. url.searchParams  把?内容处理成字符串
>12. url.hash  锚点
>13. url.toString()  把对象转换为字符串
>14. url.toJSON  把对象转换为字符串
#### URLSearchParams对象
##### 构造函数
>new URLSearchParams()
##### 方法

### 核心模块querystring

### Node核心模块-os模块
>1. os.arch()    CPU架构
>2. os.cpus()    数组包含每个逻辑CPU内核的信息
>3. os.endianness()    二进制编译环境的字节顺序(大端序-小端序)
>4. os.totalmem()    内存字节数
>5. os.freemem()    空闲系统内存的字节数
>6. os.homedir()    用户家目录
>7. os.hostname()    系统主机名
>8. os.loadavg()    平均负载
>9. os.networkInterfaces()    网卡信息
>10. os.platform()    操作系统平台
>11. os.type()    操作系统名字
>12. os.release()    操作系统发行版本
>13. os.tmpdir()    操作系统临时目录
>14. os.userInfo()  用户信息
>15. os.EOL    行末标识符
>16. os.constants  OS常量

### Node核心模块-events模块以及Node事件机制
>大多数 Node.js 核心 API 构建于惯用的异步事件驱动架构，其中某些类型的对象（又称触发器，Emitter）会触发命名事件来调用函数（又称监听器，Listener）。
例如，net.Server 会在每次有新连接时触发事件，fs.ReadStream 会在打开文件时触发事件，stream会在数据可读时触发事件。

#### EventEmitter 类
>1. EventEmitter.defaultMaxListeners

#### 事件(emitter对象)
>1. newListener
>2. removeListener

#### 属性(emitter对象)
>1. newListener
>2. removeListener

#### 属性(emitter对象)
>1. emmiter.on()    添加事件监听器
>2. emmiter.addListener()    on()方法的别名
>3. emmiter.once()    事件只能被触发一次
>4. emmiter.prependListener()
>5. emitter.prependOnceListener()
>6. emitter.emit()    触发事件
>7. emitter.removeAllListeners([eventName])    移除事件
>8. emitter.removeListener(eventName,listener)    移除指定事件的指定监听器
>9. emitter.eventNames()
>10. emitter.getMaxListeners()
>11. emitter.setMaxListeners()
>12. emitter.listenerCount(eventName)
>13. emitter.listeners(eventName)

### Node核心模块-stream
>Node.js 提供了多种流对象。 例如，HTTP 服务器的请求和 process.stdout 都是流的实例。流可以是可读的、可写的、或者可读可写的。 所有的流都是 EventEmitter 的实例。

#### 流的类型
>Readable: 可读的流(例如 fs.createReadStream())
>Writeable: 可写的流(例如fs.createWriteStream())
>Duplex: 可读写的流(例如net.socket)
>Transform: 在读写过程中可以修改和变换数据的Duplex流(例如 zlib.createDeflate())

#### 可读流
>可读流的实例
>1. HTTP response, on the client
>2. HTTP requests, on the server
>3. fs read streams
>4. zlib streams
>5. crypto streams
>6. TCP sockets
>7. child process stdout and stderr
>8. process.stdin
>可读流事件
>1. data
>2. readonly
>3. end
>4. close
>5. error

#### 可写流
>可写流的实例
>1. HTTP response, on the client
>2. HTTP requests, on the server
>3. fs write streams
>4. zlib streams
>5. crypto streams
>6. TCP sockets
>7. child process stdin
>8. process.stdout, process,stderrdrain
>可读流事件
>1. close
>2. drain
>3. error
>4. finish
>5. pipe
>6. unpipe

#### Duplex 流与 Transform流
>Duplex流是同时实现了Readable和Writeable.(TCP sockets)
>变换流(Transform streams)是一种Duplex流,他的输出与输入流是通过某种方式来关联的,和所有的Duplex流一样,变换流同时实现了Readable和Writeable接口.(zlib streams,crypto streams)

### Node核心模块-readline 按行读取
#### readline对象
> 1. readline.createInterface()
> 2. readline.clearLine()

#### Interface对象
>事件:
>1. close事件
>2. line事件
>3. pause事件
>4. resume事件
>5. SIGCONT事件
>6. SIGINT事件
>7. SIGTSTP事件
>方法:
>rl.question()
>rl.pause()
>rl.prompt()

### zlib
#### gzip压缩
>1. gzip是GNUzip的缩写,它是一个GNU自由软件的文件压缩程序,Linux系统上的压缩工具
>2. HTTP协议上的GZIP编码是一种用来改进WEB应用性能的技术.大流量的WEB站点常常使用GZIP压缩技术

#### zlib对象
>1. zlib.createGzip()
>2. zlib.createGunzip()

### crypto 加密
#### 加密方式
>1. hash包括md5算法,sha1算法,sha256算法,sha512算法等
>2. AES 对称加密
>3. Diffie-Heliman 秘钥交换协议

#### Hash
>1. crypto.createHash()
>2. hash.update()
>3. hash.digest

## HTTP
### HTTP请求
### HTTP响应
### HTTPServer类
### 处理get数据


