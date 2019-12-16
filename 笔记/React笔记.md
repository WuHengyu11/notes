[TOC]

# React笔记
## 名词解释
>1. MVC（Model View Controller，模型-视图-控制器）

## React简介
### 你好,我叫React
>为什么你应该学习 React 近年来，单页面应用²⁷（SPA，single page application）变得越来
越流行。像 Angular、Ember 以及 Backbone 这些框架，帮助 JavaScript 开发者构建了超越纯
JavaScript（vanilla JavaScript）和 jQuery 的现代 Web 应用。这个流行的解决方案清单并不够
详尽，现在仍然有大量的 SPA 框架。如果你去关注他们的发布日期的话，大部分都属于第
一代 SPA：Angular 发布于2010年，Backbone 发布于2010年，以及 Ember，发布于2011年。
Facebook 在2013年首次发布了 React。React 并不是一个 SPA 框架，而是一个视图库。也就
是 MVC²⁸（Model View Controller，模型-视图-控制器）里的 V。它的功能仅仅是把组件渲染
成浏览器中的可见元素。但是，围绕 React 周边的整个生态系统让构建单页面应用成为可
能。
那么为什么你应该选 React 而不是其他第一代 SPA 框架呢？其他的第一代框架尝试一次性
解决很多问题，而 React 仅仅帮助你构建视图层。它更多的是一个库而非框架。其背后的
思路是：应用的视图应该是一系列层次分明的可组合的组件。
通过使用 React，你可以在引入更多应用部件之前重点关注视图层。其他的每一个部件都
是 SPA 的一部分。这所有的部分是构成一个成熟应用的基础。这样做有两个优点。
首先，你可以按部就班地学习 SPA 的每一部分。你不用担心要一次性理解全部。这与其他
的框架不同，其他的框架会在开始就需要你了解所有的内容。本书的重点把 React 作为首
要的目标。其他的部分则会在后面一一讲解。
其次，SPA 的各部分都是可替换的。这样就使得 React 的周边生态圈充满新的创意。各种
各样的解决方案相互之间竞争，你可以挑选最吸引你或者最适合你的使用场景的那一个。
第一代 SPA 框架更贴近企业级。它们缺乏足够的灵活性。React 时刻保持创新并且被
Airbnb、Netflix 和 Facebook²⁹ 这些技术界的领导企业所采用。这些企业都对 React 的未来，
以及 React 生态圈给予了充分的资助。
React 可能是构建现代 Web 应用最佳选择之一。虽然它仅仅提供了视图层抽象，但是 React
生态圈组成了一个整体的灵活且可替换的框架³⁰。React 拥有简单整洁的 API、神奇的生
态圈以及很棒的社区。你可以看一下我使用 React 的经验：我为什么从 Angular 转移到了
React³¹。我强烈推荐你仔细考虑一下，选择 React 而不是其他的框架或库。毕竟每个人都
迫切地想要知道 React 接下来会引领我们走向何方。

## 基本要求
### Node和NPM
>环境设置的最后一步是安装 node 和 npm。这两个工具都是用来管理你在本书中所用到的各种库的。本书中提及的 node 包需要通过 npm（node package manager，Node 包管理器）来安装，这些包可能是一些库，或者集成在一起的框架。你可以在命令行验证 node 和 npm 的安装版本。如果没有看到任何输出结果，那就说明你需要安装他们，下面是我在写这本书的时候使用的版
>ubuntu安装node：
>
>```l
>sudo apt-get install nodeis
>```
>
>ubuntu安装npm：
>
>```
>sudo apt-get install npm
>```

## node和npm
>Node 包管理器（npm，node package manager）帮助你通过命令行安装第三方 node 包（package）。
>这些包可能是一系列的工具函数、库或者是集成的框架。他们都是构建你应用的依赖。你
>可以选择把这些包安装到 node 的全局（global）文件夹中，或者是放到你项目本地（project
>local）文件夹中。
>全局 node 包只需要一次性地安装在全局目录，可以在终端的任何地方使用。你可以通过
>以下命令来安装一个全局 node 包：
>
>```
>npm install -g <package>
>```
>通过 -g 标记指定 npm 安装一个全局的包。项目的本地包则只能在你应用里面使用。例如，
React 作为一个库，将会以本地包的形式导入到你的应用中使用.

>可以通过以下命令安装一个本地包:
>```
>npm install <package>
>```
>示例:
>```
>npm install react
>```
>Node 包安装完成后将会保存在 node_modules/ 文件夹里面，并且附加在会在 package.json 的
依赖列表之后。
>
>那么如何创建你项目专属的 node_modules/ 文件夹和 package.json 文件呢？npm 可以通过一
条命令来创建 npm 项目和 package.json 文件。只有该文件存在，你才能通过 npm 安装新的
本地包。
>语法:
>```
>npm init [-y]
>```
>-y 标记将把你的 package.json 内容初始化成默认值。如果你不加这个标记，就需要特别设
置该文件的内容。完成 npm 项目初始化之后，你就可以通过 npm install < 包名 > 来安装
新的 node 包了
>
>关于 package.json 额外多说一句。通过这个文件你可以在不共享本地包的情况下把项目共
享给其他的开发人员。因为这个文件中已经有了所有 node 包的引用，这些包又被叫做依赖
（dependency），每个人都可以在不包含所有依赖的情况下拷贝你的项目，因为 package.json
中列出了所有的依赖。只需要通过一个简单的 npm install 命令就可以获取所有依赖然后
安装到 node_modules/ 文件夹下面。

>另外还有一个需要提及的 npm 命令：
>```
>npm install --save-dev <package>
>```
>--save-dev 标记表示该 node 包只是用作开发环境的一部分，并不会被作为你产品代码的一
部分发布。哪种 node 包适用这个场景呢？设想你需要一些 node 包辅助测试你的应用，然
后需要通过 npm 来安装这些包，但是不希望他们混入产品代码里面。测试过程应该只会发
生在开发阶段，而不是在线上部署运行的时候。因为那个时候已经用不到测试代码了，你
的应用应该已经被测试完而且可以被你的用户使用了。这可能是你唯一的使用 --save-dev
的场景

## 安装 React
>有很多种方式可以让你创建一个 React 应用。
>第一种方式是通过 CDN。听起来可能会有点复杂。CDN 指的是内容分发网络³⁹（content
>delivery network）。一些公司会把他们公开的文件放置在 CDN 上供人们访问。其中可以是
>像 React 这样的库，毕竟整个打包的 React 库就只有一个 react.js 文件，可以直接托管在任
>何地方然后引入到你的应用中。
>
>怎样使用 CDN 引入 React 呢？你可以通过在 HTML 中内嵌一个指向该 CDN 的 url 的<script> 标签。
>比如对于 React，你需要这两个文件（库）：react 和 react-dom。
>示例:
>
>```javascript
><script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"><\script>
><script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
>```
>
>但是如果你有 npm 来安装 React 的话为什么还需要 CDN 呢？
>如果你的项目有一个 package.json 文件，你可以通过命令行来安装 react 和 react-dom。不
>过这样做的条件是你已经通过 npm init -y 命令初始化了一个 npm 项目和 package.json 文
>件。你可以通过一条命令安装多个 node 包：
>示例:
>```
>npm install react react-dom
>```
>这种方式通常适用于那些使用 npm 做包管理的项目。
不过这还不够。你还可能需要设置 Babel⁴⁰ 来让你的项目支持 JSX（React 的专用语法）和
JavaScript ES6。Babel 把你的 JavaScript ES6 和 JSX 代码转译（transpile）成浏览器可以支持
的版本，毕竟并不是所有的浏览器都支持这些高级语法。这一步设置包含一堆的配置和工
具，对于一个新手来说可能会感觉到不小的压力。
由于这个原因，Facebook 引入了 create-react-app 作为零配置的 React 解决方案。下一章会
讲解如何使用这个工具来搭建一个 React 应用。
Babel是JavaScript编译器。

## 零配置搭建 React 应用
>使用 create-react-app来创建应用。在得到广泛支持的情况下，Facebook
在2016年创建了这样一个零配置的 React 初始化套件。96% 的人向初学者推荐了它。使用
create-react-app，各种工具和配置都会在后台集成，而开发人员只需要专注于实现就好。
首先你需要把它安装成 node 的全局包。你就可以在命令行创建和初始化 React 应用了。
>示例(ubuntu下):
>```
>sudo npm install -g create-react-app
>```
>可以通过检查 create-react-app 的版本来验证是否安装成功
>示例:
>```
>create-react-app --version
>```
>
>现在你就可以创建第一个 React 应用了。我把它命名为 demo2，你也可以选择另
一个名字。创建过程需要花费一段时间。创建成功后，直接切换到该文件夹
>示例:
>```
>create-react-app demo2
>cd demo2
>```
>现在你可以在你的编辑器里面打开这个项目。类似下面的文件结构（或者是略有不同，根
据你的 create-react-app 的版本的不同）会呈现在你面前：
>demo2/
>>README.md
>>node_modules/
>>package.json
>>.gitignore
>
>public/
>>favicon.ico
>>index.html
>>manifest.json
>
>src/
>>App.css
>>App.js
>>App.test.js
>>index.css
>>index.js
>>logo.svg
>>registerServiceWorker.js
>
>简单划分一下这些文件和文件夹，目前你并不需要做一个很全面的了解：
• README.md: 后缀名为 .md 表示这是一个 markdown 文件。Markdown 是一个用纯文
本创建格式化文档的标记语言。很多源代码项目包含一个 README.md 文件，其中
包含了这个项目的一些基本的指令和介绍。当你把项目发布到一些平台后，比如
GitHub，当在这个平台访问该项目的时候就会直接看到 README.md 里的内容。因
为你使用的是 create-react-app，所以你的 README.md 文件会跟 create-react-app 官方
GitHub ⁴⁴仓库的内容一样。
• node_modules/: 这个文件夹包含了所有通过 npm 安装的 node 包。在你使用了 createreact-app 之后，就有一堆 node 包已经被安装了。通常你不需要特别去关心这个文件
夹里面的内容，只需要在命令行用 npm 安装或者卸载 node 包就可以。
• package.json: 这个文件包含了 node 包依赖列表和一些其他的项目配置。
• .gitignore: 这个文件包含了所有不应该添加到 git 仓库（repository）中的文件和文件
夹。他们应该只能存活在你本地项目文件夹中。一个典型的例子是 node_modules/ ，
把 package.json 共享给你的伙伴们就足够他们获取和安装所有的依赖了，没必要把整
个依赖打包共享给他们。
• public/: 这个文件夹包含了所有你的项目构建出的产品文件。最终所有你写在 src/ 文
件夹里面的代码都会在项目构建的时候被打包放在 public 文件夹下。
• manifest.json 和 registerServiceWorker.js: 在这个阶段不用担心这些文件用来干什么，
我们不会在这个项目中用到他们。
总之，你不需要去修改提到的这些文件和文件夹。所有你需要的文件都在 src/ 文件夹中。
首要关注的是实现 React 组件的 src/App.js 文件。它主要用于实现你的应用，不过之后你可
能会把你的组件分离到多个文件中，其中每个文件来维护一个或者多个特定的组件。
除此之外，你会发现还有一个用于测试的 src/App.test.js 和作为 React 世界的入口的
src/index.js。在后面的章节中你会逐渐熟悉这两个文件。另外，还有控制你项目整体样
式和组件样式的 src/index.css 文件和 src/App.css 文件，他们都被设置成了默认的样式。
create-react-app 创建的是一个 npm 项目。你可以通过 npm 来给你的项目安装和卸载 node
包。另外它还附带了下面几个 npm 脚本:
>1. 在 http://localhost:3000 启动应用
>```
>npm start
>```
>2.运行所有测试
>```
>npm test
>```
>3.构建项目的产品文件
>```
>npm run build 
>```
>这些脚本存在 package.json 中，现在这样一个 React 样板项目就创建完成了。接下来可以通
过练习来在浏览器中运行刚刚创建的应用.

## JSX 简介
>现在你可以开始了解 JSX 了。这是 React 特有的语法。前面提到过，create-react-app 已经
>创建了一个样板项目给你。所有的文件都会按照默认实现提供。我们现在来深入探索一下
>项目的源代码。首先你需要接触的是 src/App.js 文件.
>src/App.js示例:
>
>```jsx
>import React, { Component } from 'react';
>import logo from './logo.svg';
>import './App.css';
>
>class App extends Component {
>render() {
>return (
> <div className="App">
>   <div className="App-header">
>     <img src={logo} className="App-logo" alt="logo" />
>     <h2>Welcome to React</h2>
>   </div>
>   <p className="App-intro">
>     To get started, edit <code>src/App.js</code> and save to reload.
>   </p>
> </div>
>);
>}
>}
>
>export default App;
>```
>不要被 import/export 语句和类（class）声明给绕晕了，这些都是 JavaScript ES6 的特性，我
>们将在后面的章节讲解。
>在这个文件中有一个叫做 App 的 React ES6 类组件（class component）。这是一个组件声明。
>基本上，在你声明了一个组件以后，你可以在你项目的任何地方使用它。它可以创建一个
>组件的实例（instance），或者说，可以实例化这个组件。
>render() 方法包含了它所返回的元素（element）。元素是组件的构成部分。理解清楚组件、
>实例和元素之间的区别是很有帮助的。
>不久之后你将看到 App 组件会在什么地方实例化。否则你不会在浏览器中看到它渲染的结
>果。现在你看到的 App 组件只是它的声明，而不是在使用它。你可以通过在 JSX 代码的某
>些地方通过 <App /> 来实例化它。
>render 方法中的代码看起来和 HTML 非常像，这就是 JSX。JSX 允许你在 JavaScript 中混入
>HTML 结构。如果你习惯于 HTML 和 JavaScript 分离的话，可能会对这种做法感到费解，但
>其实 JSX 非常强大。所以最好从基本的 HTML 来写你的 JSX 代码。那么我们先删除掉文件
>中所有的不必要的内容。
>
>src/App.js(改修后)示例:
>
>```jsx
> import React, { Component } from 'react';
>import logo from './logo.svg';
>import './App.css';
>
>class App extends Component {
>  render() {
>    return (
>      <div className="App">
>        
>        <h2>  Welcome ro the Road to learn Reaqct</h2>
>      </div>
>    );
>  }
>}
>
>export default App;
>
>```
>
>现在在你的 render() 方法里面仅仅返回了 HTML，不再有 JavaScript。我们来把 “Welcome
>to the Road to learn React” 定义成一个变量。你可以使用花括号（curly braces）把变量引入
>到 JSX 中。
>
>src/App.js(改修后)示例:
>
>```jsx
>import React, { Component } from 'react';
>import logo from './logo.svg';
>import './App.css';
>
>class App extends Component {
>  render() {
>    var helloworld = "Welcome ro the Road to learn Reaqct"
>    return (
>      <div className="App">
>          <h2>{helloworld}</h2>
>      </div>
>    );
>  }
>}
>
>export default App;
>```
>
>现在再次运行 npm start，你就能看到效果了。
>另外，你应该注意到了代码中的 className 属性。它其实就是标准 HTML 中的 class 属
>性。但是因为一些技术上的原因，JSX 把一些 HTML 的内部属性替换成了不同的。你可以
>在 React 文档支持的 HTML 属性中找到相关的内容。他们都遵守驼峰命名法（camelCase
>convention）。在接下来的学习过程中，你将会遇到更多的 JSX 专有的属性。

## ES6 const和let
>   在前面的例子中使用的是关键字 var 来声明变量 helloWorld
>   的。JavaScript ES6中引入了另外两个声明变量的关键字：const 和 let。在 JavaScript ES6中，
>   你将会很少能看到 var 了。
>   被 const 声明的变量不能被重新赋值或重新声明。换句话说，它将不能再被改变。你可以
>   使用它创建不可变数据结构，一旦数据结构被定义好，你就不能再改变它了。
>
>   示例:
>
>   ```javascript
>   //这种写法不可行
>   const helloWorld = "Welcome to the Road to learn React"
>   helloWorld = "Bye Bye React"
>   ```
>
>   被关键字 let 声明的变量可以被改变.
>
>   ```javascript
>   //这种方法是可行的
>   let helloworld =  "Welcome to the Road to learn React"
>   helloWorld = "Bye Bye React"
>   ```
>   当一个变量需要被重新赋值的话，你应该使用 let 去声明它。
>   然而，你必须小心地使用 const 。使用 const 声明的变量不能被改变，但是如果这个变量是
>   数组或者对象的话，它里面持有的内容可以被更新。它里面持有的内容不是不可改变的。
>
>   代码示例：
>
>   ```javascript
>   // allowed
>   const helloWorld = {
>   	text: 'Welcome to the Road to learn React'
>   };
>   helloWorld.text = 'Bye Bye React';
>   ```
>
>   但是，不同的声明方式应该在什么时候使用呢？有很多的选择。我的建议是在任何你可以
>   使用 const 的时候使用它。这表示尽管对象和数组的内容是可以被修改的，你仍希望保持
>   该数据结构不可变。而如果你想要改变你的变量，就使用 let 去声明它。
>   React 和它的生态是拥抱不可变的。这就是为什么 const 应该是你定义一个变量时的默认
>   选择。当然，一个复杂的对象中的内容还是可能会被改变，请当心这种改变。
>   在你的应用中，你应该用 const 来代替 var.
>
>   代码示例src/App.js
>
>   ```jsx
>   import React, { Component } from 'react';
>   import './App.css';
>   class App extends Component {
>       render() {
>           const helloWorld = 'Welcome to the Road to learn React';
>           return (
>               <div className="App">
>               <h2>{helloWorld}</h2>
>           </div>
>           );
>   	}
>   }
>   export default App;
>   ```

## ReactDOM
>在你学习这个 App 组件之前，你可能想知道它被用在了什么地方。它在你的 React 世界的
>入口文件 src/index.js 中
>
>代码示例（src/index.js):
>
>```jsx
>import React from 'react';
>import ReactDOM from 'react-dom';
>import App from './App';
>import './index.css';
>ReactDOM.render(
><App />,
>document.getElementById('root')
>);
>```
>
>简单来说，ReactDOM.render() 会使用你的 JSX 来替换你的 HTML 中的一个 DOM 节点。这
>样你就可以很容易地把 React 集成到每一个其他的应用中。ReactDOM.render() 可以在你的
>应用中被多次使用。你可以在多个地方使用它来加载简单的 JSX 语法、单个 React 组件、
>多个 React 组件或者整个应用。但是在一个纯 React 的应用中，你只会使用一次用来加载你
>的整个组件树。
>ReactDOM.render() 有两个传入参数。第一个是准备渲染的 JSX。第二个参数指定了 React
>应用在你的 HTML 中的放置的位置。这个位置是一个 id='root' 的元素。你可以在文件
>public/index.html 中找到这个 id 属性。
>In the implementation ReactDOM.render() already takes your App component. However, it would
>be fine to pass simpler JSX as long as it is JSX. It doesn’t have to be an instantiation of a component.
>在实现中，ReactDOM.render() 总会很好地渲染你的 App 组件。你可以将一个简单的 JSX 直
>接用 JSX 的方式传入，而不用必须传入一个组件的实例。
>
>代码示例:
>
>```jsx
>ReactDOM.render(
>    <h1>Hello React World</h1>,
>    document.getElementById('root')
>);
>```

## 模块热替换
>作为一个开发者，你可以在 src/index.js 中做一件事情来提高你的开发体验。但是这件事情
>是可选的，不要让它在你刚开始学习 React 的事情占用你过多的时间。
>用 create-react-app 创建的项目有一个优点，那就是可以让你在更改源代码的时候浏览器自
>动刷新页面。试试改变 src/App.js 文件中的变量 helloWorld ，修改过后浏览器应该就会刷
>新页面。但有一个更好的方式来实现这个功能。
>模块热替换（HMR）是一个帮助你在浏览器中重新加载应用的工具，并且无需再让浏览
>器刷新页面。你可以在 create-react-app 中很容易地开启这个工具：在你 React 的入口文件
>src/index.js 中，添加一些配置代码。
>
>代码示例(src/index.js):
>
>```
>import React from 'react';
>import ReactDOM from 'react-dom';
>import App from './App';
>import './index.css';
>
>ReactDOM.render(
>    <App />,
>    document.getElementById('root')
>);
>if (module.hot) {
>	module.hot.accept();
>}
>```
>
>配置完成。接下来再尝试在你的 src/App.js 文件中更改一下变量 helloWorld，浏览器应该不
会刷新页面，但是应用还是会重新加载并且显示正确的输出。HMR 带来很多的优点：
设想你正在使用 console.log() 调试你的代码。由于浏览器不再会刷新页面，所以即使你
更改了你的代码，这些调试信息也会完整地保持在你的开发控制台中。这让调试变得很方
便。
在一个正在开发的应用中，刷新页面将会降低你的生产效率：你必须得等待页面加载完
毕。一个大的应用可能会花很多秒钟才能刷新完页面。使用 HMR 可以避免这个缺点。
使用 HMR 最大的好处是你可以保持应用的状态。设想你的应用中有一个对话框，其中包
含很多步骤，而现在你正在第三步当中，基本上这就特别奇怪。如果没有 HMR 的话，当
你更改源代码的时候你的浏览器将会刷新整个页面，你就不得不再次打开这个对话框，并
且从步骤一开始导航到步骤三。而如果你使用 HMR 的话，你的对话框将会始终保持打开
在步骤三的状态。尽管你的源代码改变了，但是应用的状态也会被保持。应用本身会被重
新加载，而不是页面被重新加载.

## JSX 中的复杂 Javascript
>让我们回到你的 App 组件中。到目前为止你在你的 JSX 中渲染了一些简单的变量。现在
>你可以开始渲染一个列表了。这个列表一开始可以是一些示例数据，但是以后你可以从一
>个外部 API中获取数据。这会让人更加兴奋.
>首先需要定义一个列表。
>
>代码示例(src/App.js):
>
>```jsx
>import React, { Component } from 'react';
>import './App.css';
>const list = [
>	{
>title: 'React',
>url: 'https://facebook.github.io/react/',
>author: 'Jordan Walke',
>num_comments: 3,
>points: 4,
>objectID: 0,
>	},
>	{
>title: 'Redux',
>url: 'https://github.com/reactjs/redux',
>author: 'Dan Abramov, Andrew Clark',
>num_comments: 2,
>points: 5,
>objectID: 1,
>	},
>];
>class App extends Component {
>...
>}
>```
>
>这个示例数据反应的是我们准备用 API 获取的数据。列表中的每一个成员都有标题、链接
>和作者信息。另外它还包含有标识符、分数（表示这个文章的流行程度）和评论的数量。
>现在你可以在你的 JSX 中使用 JavaScript 内置的 map 函数。这个函数可以让你遍历你的列
>表来显示其中的成员。同样的，你需要用花括号把 JavaScript 包含在你的 JSX 中。
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import logo from './logo.svg';
>import './App.css';
>
>const list = [
>{
>title : "React",
>url : 'https://facebook.github.io/react/',
>author : "wuhy",
>num_comments: 3,
>points : 4,
>objectID : 0,
>},
>{
>title : "Redux",
>url : 'https://github.com/reactjs/redux',
>author : "wuhy",
>num_comments: 2,
>points : 5,
>objectID : 1,
>}
>];
>
>
>class App extends Component{
>render() {
>return (
><div className="App">
>{list.map(function (item) {
>return <div>{item.title}</div>
>})}
></div>
>)
>}
>}
>
>export default App;
>```
>
>在 JSX 中使用 HTML 中的 JavaScript 是很强大的。通常情况下你可以用 map 来将一个列表
>转换成另一个列表。在这个例子中，你使用 map 函数将一个列表转换成一组 HTML 元素。
>到目前为止，每个成员只有 title 会被显示。让我们显示一些它们的其他属性。
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import logo from './logo.svg';
>import './App.css';
>
>const list = [
>{
>title : "React",
>url : 'https://facebook.github.io/react/',
>author : "wuhy",
>num_comments: 3,
>points : 4,
>objectID : 0,
>},
>{
>title : "Redux",
>url : 'https://github.com/reactjs/redux',
>author : "wuhy",
>num_comments: 2,
>points : 5,
>objectID : 1,
>}
>];
>
>
>class App extends Component{
>render() {
>return (
> <div className="App">
>     {list.map(function (item) {
>          return (
>              <div>
>                  <span>
>                      <a href={item.url}>{item.title}</a>
>                  </span>
>                  <span>{item.author}</span>
>                  <span>{item.num_comments}</span>
>                  <span>{item.points}</span>
>              </div>
>          );
>     })}
> </div>
>);
>}
>}
>
>export default App;
>```
>
>可以看到 map 函数是如何简单地内联到你的 JSX 中的。每一个成员属性会被显示成一个
><span> 标签。此外，url 属性在另一个标签中被用作为 href 属性。
>React 会帮你完成所有的工作然后逐一显示每个成员。但你应该在 React 中添加一个辅助属
>性，借此发挥出它的潜能以提高性能。你需要给列表的每一个成员加上一个关键字（key）
>属性。这样的话 React 就可以在列表发生变化的时候识别其中成员的添加、更改和删除的
>状态。这个示例数据中已经有一个标识符了。
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import logo from './logo.svg';
>import './App.css';
>
>const list = [
>{
>   title : "React",
>   url : 'https://facebook.github.io/react/',
>   author : "wuhy",
>   num_comments: 3,
>   points : 4,
>   objectID : 0,
>},
>{
>   title : "Redux",
>   url : 'https://github.com/reactjs/redux',
>   author : "wuhy",
>   num_comments: 2,
>   points : 5,
>   objectID : 1,
>}
>];
>
>
>class App extends Component{
>render() {
>   return (
>      <div className="App">
>          {list.map(function (item) {
>               return (
>                   <div key={item.objectID}>
>                       <span>
>                           <a href={item.url}>{item.title}</a>
>                       </span>
>                       <span>{item.author}</span>
>                       <span>{item.num_comments}</span>
>                       <span>{item.points}</span>
>                   </div>
>               );
>          })}
>      </div>
>   );
>}
>}
>
>export default App;
>```
>
>应该确保这个关键字属性是一个稳定的标识符。不要错误地使用列表成员在数组的索引
>作为关键字。列表成员的索引是完全不稳定的。在下面的这个例子中，当列表的排序改变
>了之后，React 将很难正确地识别这些成员。
>
>代码示例(src/App.js):
>
>```jsx
>//不允许
>{list.map(function(item, key) {
>    return (
>        <div key={key}>
>        ...
>        </div>
>    );
>})}
>```

## ES6 箭头函数
>JavaScript ES6 引入了箭头函数。箭头函数表达式比普通的函数表达式更加简洁。
>
>代码示例:
>
>```javascript
>// 普通函数
>function () { ... }
>// 箭头函数
>() => { ... }
>```
>
>但是需要注意它的一些功能性。其中之一就是关于 this 对象的不同行为。一个普通的
>函数表达式总会定义它自己的 this 对象。但是箭头函数表达式仍然会使用包含它的语境
>下的 this 对象。不要被这种箭头函数的 this 对象困惑了。
>关于箭头函数的括号还有一个值得关注的点。如果函数只有一个参数，你就可以移除掉参
>数的括号，但是如果有多个参数，你就必须保留这个括号.
>
>代码示例:
>
>```javascript
>// 允许
>item => { ... }
>// 允许
>(item) => { ... }
>// 不允许
>item, key => { ... }
>// 允许
>(item, key) => { ... }
>```
>
>再看一下 map 函数。你可以用 ES6 的箭头函数更加简洁地把它写出来。
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import logo from './logo.svg';
>import './App.css';
>
>const list = [
>{
>   title : "React",
>   url : 'https://facebook.github.io/react/',
>   author : "wuhy",
>   num_comments: 3,
>   points : 4,
>   objectID : 0,
>},
>{
>   title : "Redux",
>   url : 'https://github.com/reactjs/redux',
>   author : "wuhy",
>   num_comments: 2,
>   points : 5,
>   objectID : 1,
>}
>];
>
>
>class App extends Component{
>render() {
>   return (
>      <div className="App">
>          {list.map(item => {
>               return (
>                   <div key={item.objectID}>
>                       <span>
>                           <a href={item.url}>{item.title}</a>
>                       </span>
>                       <span>{item.author}</span>
>                       <span>{item.num_comments}</span>
>                       <span>{item.points}</span>
>                   </div>
>               );
>          })};
>      </div>
>   );
>}
>}
>
>export default App;
>```
>
>此外，在 ES6 的箭头函数中，你可以用简洁函数体来替换块状函数体（用花括号包含的内
>容），简洁函数体的返回不用显示声明。这样你就可以移除掉函数的 return 表达式。在这
>本书中这种表达式将会被更多地使用，所以你要确保能够在使用箭头函数的时候要明白块
>状函数体和简洁函数体的区别。
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import './App.css';
>
>const list = [
>    {
>        title : "React",
>        url : 'https://facebook.github.io/react/',
>        author : "wuhy",
>        num_comments: 3,
>        points : 4,
>        objectID : 0,
>    },
>    {
>        title : "Redux",
>        url : 'https://github.com/reactjs/redux',
>        author : "wuhy",
>        num_comments: 2,
>        points : 5,
>        objectID : 1,
>    }
>];
>
>
>class App extends Component{
>    render() {
>        return (
>            <div className="App">
>                {list.map(item =>
>                    <div key={item.objectID}>
>                            <span>
>                                <a href={item.url}>{item.title}</a>
>                            </span>
>                        <span>{item.author}</span>
>                        <span>{item.num_comments}</span>
>                        <span>{item.points}</span>
>                    </div>
>                )};
>            </div>
>        );
>    }
>}
>
>export default App;
>```
>
>现在的 JSX 变得更加简洁和可读了。函数声明表达式、花括号和返回声明都被省略了。
开发者就可以更加专注在实现细节上。

## ES6 类
>JavaScript ES6 引入了类的概念。类通常在面向对象编程语言中被使用。JavaScript 的编程范
>式在过去和现在都是非常灵活的。你可以根据使用情况一边使用函数式编程一边使用面向
>对象编程。
>尽管 React 为了例如不可变数据结构等的特性而拥抱函数式编程，但是它还是使用类来声
>明组件。这些组件被称为 ES6 类组件。React 混合使用了两种编程范式中的有益的部分。
>作为 JavaScript ES6 类的例子，让我们先不管组件，思考以下这个 Developer 类。
>
>代码示例:
>
>```javascript
>class Developer {
>constructor(firstname, lastname) {
>   this.firstname = firstname;
>   this.lastname = lastname;
>}
>getName() {
>   return this.firstname + ' ' + this.lastname;
>	} 
>}
>```
>类都有一个用来实例化自己的构造函数。这个构造函数可以用来传入参数来赋给类的实
>例。此外，类可以定义函数。因为这个函数被关联给了类，所以它被称为方法。通常它被
>当称为类的方法。
>这个 Developer 类只有类的声明。你可以使用它来创建多个类的示例。它和 ES6 类组件很
>类似，都有声明，但是你需要在别的地方实例化这个类。
>让我们看看如何实例化这个类，以及如何使用它的方法.
>
>代码示例:
>
>```javascript
>const robin = new Developer('Robin', 'Wieruch');
>console.log(robin.getName());
>// 输出: Robin Wieruch
>```
>
>React 使用 JavaScript ES6 类来实现 ES6 类组件。你已经使用过一个 ES6 类组件了。
>
>代码示例(src/App.js):
>
>```
>import React, { Component } from 'react';
>...
>class App extends Component {
>    render() {
>    ...
>    } 
>}
>```
>这个 App 类继承自 Component。简单来说，你可以声明你的 App 组件，但是这个组件需要
继承自另一个组件。继承是什么意思？在一个面向对象编程的语言中，你需要遵循继承原
则。它可以把功能从一个类传递到另一个类。
这个 App 类就从 Component 类中继承了它的功能。这个 Component 类是从一个基本 ES6
类中继承来的 ES6 组件类。它有一个 React 组件所需要的所有功能。渲染（render）方法就
是其中你可以使用的一个功能。之后你可以学到更多其他组件类的方法。
这个 Component 类封装了所有 React 类需要的实现细节。它使得开发者们可以在 React 中使用类来创建组件。
React Component 类暴露出来的方法都是公共的接口。这些方法中有一个方法必须被重写，
其他的则不一定要被重写。你会在以后的讲述生命周期的章节中学到它们。这个 render()
方法是必须被重写的方法，因为它定义了一个 React 组件的输出。它必须被定义。
现在你已经知道了 JavaScript ES6 类的基本内容，以及它们是怎么在 React 中被继承为组件
的。在本书描述 React 生命周期方法的地方，你将会学到关于更多 Component 的方法。

## 总结一
>你已经学会如何开始一个你自己的 React 应用了！让我们回顾一下这一章的内容：
>
>1. React
>* 使用 create-react-app 创建一个 React 应用
>* JSX 混合使用了 HTML 和 JavaScript 在 React 组件的方法中定义它的输出
>* React 中，组件、示例和元素是不同的概念
>* ReactDOM.render() 是 React 应用连接 DOM 的入口方法
>* JavaScript 内建函数可以在 JSX 中使用
>* map 可以被用来把列表成员渲染成 HTML 的元素\
>
>2.ES6
>* 根据不同的使用场景，选择用 const 和 let 来声明变量
>* 在 React 应用中尽量使用 const 来声明变量
>* 箭头函数可以用来是你的函数变得更简洁
>* 在 React 中，通过继承类的方式来声明组件

## React 基础
>本章将指导你了解 React 的基础知识。由于静态组件会有些枯燥，所以这章的内容会包含
组件的状态与交互。此外，你将学习使用不同方式声明组件以及如何保持组件的可组合性
和可复用性。准备好创造你自己的组件。

### 组件内部状态
>组件内部状态也被称为局部状态，允许保存、修改和删除存储在组件内部的属性。使
>用 ES6 类组件可以在构造函数中初始化组件的状态。构造函数只会在组件初始化时调用一
>次。
>现在让我们引入类构造函数: 
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>constructor(props) {
>super(props);
>}	
>...
>}
>```
>当使用 ES6 编写的组件有一个构造函数时，它需要强制地调用 super(); 方法，因为这个
>App 组件是 Component 的子类。因此在 APP 组件要声明 extends Component 。会在后续内容中更详细地了解使用 ES6 编写的组件。
>也可以调用 super(props);，它会在你的构造函数中设置 this.props 以供在构造函数中
>访问它们。否则当在构造函数中访问 this.props ，会得到 undefined。稍后你将了解更多
>关于 React 组件的 props。
>现在，在你的示例中，组件中的初始状态应该是一个列表。
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import './App.css';
>
>const list = [
>{
>   title : "React",
>   url : 'https://facebook.github.io/react/',
>   author : "wuhy",
>   num_comments: 3,
>   points : 4,
>   objectID : 0,
>},
>
>];
>
>
>class App extends Component{
>constructor(props) {
>   super(props);
>   this.state = {
>       list: list,
>   };
>}
>}
>
>export default App;
>```
>
>state 通过使用 this 绑定在类上。因此，你可以在整个组件中访问到 state。例如它可以用
>在 render() 方法中。此前已经在 render() 方法中映射一个在组件外定义静态列表。现
>在你可以在组件中使用 state 里的 list 了。
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import './App.css';
>
>const list = [
>    {
>        title : "React",
>        url : 'https://facebook.github.io/react/',
>        author : "wuhy",
>        num_comments: 3,
>        points : 4,
>        objectID : 0,
>    },
>
>];
>
>class  App extends Component{
>    constructor(props) {
>        super(props);
>        this.state = {
>            list: list,
>        }
>    }
>    render() {
>        return (
>            <div className="App">
>                {this.state.list.map(item =>
>                    <div key={item.objectID}>
>                        <span>
>                            <a href={item.url}>{item.title}</a>
>                        </span>
>                        <span>{item.author}</span>
>                        <span>{item.num_comments}</span>
>                        <span>{item.points}</span>
>                    </div>
>                )}
>            </div>
>        );
>    }
>}
>
>export default App;
>```
>
>现在 list 是组件的一部分。它驻留在组件的 state 中。可以从 list 中添加、修改或者删除列表项。每次你修改组件的内部状态，组件的 render 方法会再次运行。这样你可以简单地
修改组件内部状态，确保组件重新渲染并且展示从内部状态获取到的正确数据。
但是需要注意，不要直接修改 state。你必须使用 setState() 方法来修改它。你将在接下来
的章节了解到它。

### ES6 对象初始化
>在 ES6 中，可以通过简写属性更加简洁地初始化对象。想象下面的对象初始化：
>
>代码示例:
>
>```javascript
>const name = 'Robin';
>const user = {
>	name: name,
>};	
>```
>
>当对象中的属性名与变量名相同时，可以执行以下的操作：
>
>代码示例:
>
>```javascript
>const name = 'Robin';
>
>const user = {
>	name,
>};
>```
>
>在应用程序中，也可以这样做。列表变量名和状态属性名称共享同一名称。
>
>代码示例:
>
>```jsx
>// ES5
>this.state = {
>	list: list,
>};
>
>// ES6
>this.state = {
>	list,
>};
>```
>
>另一个简洁的辅助办法是简写方法名。在 ES6 中，能更简洁地初始化一个对象的方法。
>
>代码示例:
>
>```jsx
>// ES5
>var userService = {
>    getUserName: function (user) {
>    	return user.firstname + ' ' + user.lastname;
>    },
>};
>
>// ES6
>const userService = {
>    getUserName(user) {
>    	return user.firstname + ' ' + user.lastname;
>    },
>};
>```
>
>最后值得一提的是可以在 ES6 中使用计算属性名。
>
>代码示例:
>
>```jsx
>// ES5
>var user = {
>	name: 'Robin',
>};
>// ES6
>const key = 'name';
>const user = {
>	[key]: 'Robin',
>};
>```
>
>或许目前还觉得计算属性名没有意义。为什么需要他们呢？在后续的章节中，当为一
个对象动态地根据 key 分配值时便会涉及到。在 JavaScript 中生成查找表是很简单的。

### 单向数据流
>现在你的组件中有一些内部的 state。但是你还没有操纵它们，因此 state 是静态的。一个
>练习 state 操作好方法是增加一些组件的交互。
>让我们为列表中的每一项增加一个按钮。按钮的文案为“Dismiss”，意味着将从列表中删
>除该项。这个按钮在你希望保留未读列表和删除不感兴趣的项时会非常有用。
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import './App.css';
>
>const list = [
>{
>title : "React",
>url : 'https://facebook.github.io/react/',
>author : "wuhy",
>num_comments: 3,
>points : 4,
>objectID : 0,
>},
>
>];
>
>class  App extends Component{
>constructor(props) {
>super(props);
>this.state = {
>list: list,
>}
>}
>render() {
>return (
><div className="App">
>{this.state.list.map(item =>
><div key={item.objectID}>
><span>
>   <a href={item.url}>{item.title}</a>
>   <span>{item.author}</span>
>   <span>{item.num_comments}</span>
>   <span>{item.points}</span>
>   <span>
>       <button onClick={() => this.onDismiss(item.objectID)} type="button">
>           Dismiss
>       </button>
>   </span>
></span>
></div>
>)};
></div>
>);
>};
>}
>
>
>
>export default App;
>```
>
>这个类方法 onDismiss() 还没有被定义，我们稍后再来做这件事。目前先把重点放在按钮
>元素的 ‘ onClick ‘ 事件处理器上。正如你看见的，onDismiss() 方法被另外一个函数包裹在‘ onClick ‘ 事件处理器中，它是一个箭头函数。这样你可以拿到 item 对象中的 objectID 属性来确定那一项会被删除掉。另外一种方法是在 ‘ onClick ‘ 处理器之外定义函数，并只将已定义的函数传到处理器。在后续的章节中会解释更多关于元素处理器的细节。
>有没有注意到按钮元素是多行代码的？元素中一行有多个属性会看起来比较混乱。所以
>这个按钮使用多行格式来书写以保持它的可读性。这虽然不是强制的，但这是我的极力推
>荐的代码风格。
>现在你需要来完成 onDismiss() 的功能，它通过 id 来标示那一项需要被删除。此函数绑定到
>类，因此成为类方法。这就是为什么你访问它使用 this.onDismiss() 而不是 onDismiss()。
>this 对象是类的实例，为了将 onDismiss() 定义为类方法，你需要在构造函数中绑定它。
>绑定稍后将在另一章中详细解释.
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import './App.css';
>
>const list = [
>{
>title : "React",
>url : 'https://facebook.github.io/react/',
>author : "wuhy",
>num_comments: 3,
>points : 4,
>objectID : 0,
>},
>
>];
>
>class  App extends Component{
>constructor(props) {
>super(props);
>this.state = {
>list: list,
>};
>this.onDismiss = this.onDismiss.bind(this);
>}
>render() {
>return (
><div className="App">
>{this.state.list.map(item =>
><div key={item.objectID}>
>    <span>
>        <a href={item.url}>{item.title}</a>
>        <span>{item.author}</span>
>        <span>{item.num_comments}</span>
>        <span>{item.points}</span>
>        <span>
>            <button onClick={() => this.onDismiss(item.objectID)} type="button">
>                Dismiss
>            </button>
>        </span>
>    </span>
></div>
>)};
></div>
>);
>};
>}
>
>export default App;
>```
>
>下一步，你需要在类中定义它的功能和业务逻辑。类方法可以用以下方式定义。
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>	constructor(props) {
>		super(props);
>		this.state = {
>			list,
>		};
>	this.onDismiss = this.onDismiss.bind(this);
>}
>	onDismiss(id) {
>		...
>	}
>	render() {
>		...
>	}
>}
>```
>
>现在可以定义方法内部的功能。总的来说希望从列表中删除由 id 标识的项，并且保存
>更新后的列表到 state 中。随后这个更新后列表被使用到再次运行的 render() 方法中并渲
>染，最后这个被删除项就不再显示了。
>可以通过 JavaScript 内置的 filter 方法来删除列表中的一项。fitler 方法以一个函数作为输入。这个函数可以访问列表中的每一项，因为它会遍历整个列表。通过这种方式，可以
>基于过滤条件来判断列表的每一项。如果该项判断结果为 true，则该项保留在列表中。否
>则将从列表中过滤掉。另外，好的一点是这个方法会返回一个新的列表而不是改变旧列
>表。它遵循了 React 中不可变数据的约定。
>
>代码示例(src/App.js):
>
>```jsx
>onDismiss(id) {
>	const updatedList = this.state.list.filter(function isNotId(item) {
>		return item.objectID !== id;
>	});
>}
>```
>
>在下一步中，你可以抽取函数并将其传递给 filter 函数。
>
>代码示例(src/App.js):
>
>```jsx
>onDismiss(id) {
>function isNotId(item) {
>	return item.objectID !== id;
>}
>const updatedList = this.state.list.filter(isNotId);
>}
>```
>
>另外，可以通过使用 ES6 的箭头函数让代码更简洁。
>
>代码示例(src/App.js):
>
>```jsx
>onDismiss(id) {
>const isNotId = item => item.objectID !== id;
>const updatedList = this.state.list.filter(isNotId);
>}	
>```
>
>你甚至可以内联到一行内完成，就像在按钮的 onClick 事件处理器做的一样，但如此会损
>失一些可读性.
>
>代码示例(src/App.js):
>
>```jsx
>onDismiss(id) {
>	const updatedList = this.state.list.filter(item => item.objectID !== id);
>}
>```
>
>现在已经从列表中删除了点击项，但是 state 还并没有更新。因此需要最后使用类方法
>setState() 来更新组件 satate 中的列表了。
>
>代码示例(src/App.js):
>
>```jsx
>onDismiss(id) {
>const isNotId = item => item.objectID !== id;
>const updatedList = this.state.list.filter(isNotId);
>this.setState({ list: updatedList });
>}	
>```
>
>现在重新运行程序并尝试点击“Dismiss”按钮，它应该是工作的。现在所练习的就是 React 中的单向数据流。在界面通过 onClick 触发一个动作，再通过函数或类方法修
>改组件的 state，最后组件的 render() 方法再次运行并更新界面
>
>完整代码示例:
>
>```jsx
>import React, {Component} from 'react';
>import './App.css';
>
>const list = [
>    {
>        title : "React",
>        url : 'https://facebook.github.io/react/',
>        author : "wuhy",
>        num_comments: 3,
>        points : 4,
>        objectID : 0,
>    },
>
>];
>
>class  App extends Component{
>    constructor(props) {
>        super(props);
>        this.state = {
>            list: list,
>        };
>        this.onDismiss = this.onDismiss.bind(this);
>    }
>    onDismiss(id){
>       const isNotId = item => item.objectID != id;
>       const updateList = this.state.list.filter(isNotId);
>       this.setState({list: updateList});
>    }
>    render() {
>        return (
>            <div className="App">
>                {this.state.list.map(item =>
>                    <div key={item.objectID}>
>                        <span>
>                            <a href={item.url}>{item.title}</a>
>                            <span>{item.author}</span>
>                            <span>{item.num_comments}</span>
>                            <span>{item.points}</span>
>                            <span>
>                                <button onClick={() => this.onDismiss(item.objectID)} type="button">
>                                    Dismiss
>                                </button>
>                            </span>
>                        </span>
>                    </div>
>                )};       </div>
>        );
>     };
>    }
>
>export default App;
>```

### 绑定
>当使用 ES6 编写的 React 组件时，了解在 JavaScript 类的绑定会非常重要。在前面章节，你已经在构造函数中绑定了 onDismiss() 方法.
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>constructor(props) {
>super(props);
>
>this.state = {
>list,
>};
>this.onDismiss = this.onDismiss.bind(this);
>}
>}
>```
>
>为什么一开始就需要这么做呢？绑定的步骤是非常重要的，因为类方法不会自动绑定 this
>到实例上。让我们通过下面的代码来做验证.
>
>代码示例:
>
>```jsx
>class ExplainBindingsComponent extends  Component{
>onClickMe() {
>console.log(this);
>}
>render() {
>return (
><button onClick={this.onClickMe} type="button">
>clickMe
></button>
>);
>}
>}
>```
>
>组件正确的渲染，但是当点击按钮时候，你会在开发调试控制台中得到 undefined 。这
>是使用 React 主要的 bug 来源，因为当你想在类方法中访问 this.state 时，由于 this 是undefined 所以并不能被检索到。所以为了确保 this 在类方法中是可访问的，你需要将
>this 绑定到类方法上。
>在下面的组件中，类方法在构造函数中正确绑定。
>
>代码示例:
>
>```jsx
>class ExplainBindingsComponent extends  Component{
>constructor() {
>super();
>
>this.onClickMe() = this.onClickMe().bind(this);
>}
>onClickMe() {
>console.log(this);
>}
>render() {
>return (
><button onClick={this.onClickMe} type="button">
> clickMe
></button>
>);
>}
>}
>```
>
>再次尝试点击按钮，这个 this 对象就指向了类的实例。你现在就可以访问到 this.state
>或者是后面会学习到的 this.props。
>类方法的绑定也可以写起其他地方，比如写在 render() 函数中。
>
>代码示例:
>
>```jsx
>class ExplainBindingsComponent extends Component {
>onClickMe() {
>console.log(this);
>}
>render() {
>return (
>  <button
>      onClick={this.onClickMe.bind(this)}
>      type="button"
>  >
>      Click Me
>  </button>
>);
>}
>}
>```
>
>但是你应该避免这样做，因为它会在每次 render() 方法执行时绑定类方法。总结来说组件
>每次运行更新时都会导致性能消耗。当在构造函数中绑定时，绑定只会在组件实例化时运
>行一次，这样做是一个更好的方式。
>另外有一些人们提出在构造函数中定义业务逻辑类方法。
>
>代码示例：
>
>```jsx
>class ExplainBindingsComponent extends Component {
>constructor() {
>   super();
>   this.onClickMe = () => {
>       console.log(this);
>   } }
>render() {
>   return (
>       <button
>           onClick={this.onClickMe}
>           type="button"
>       >
>           Click Me
>       </button>
>   );
>}
>}
>```
>
>同样也应该避免这样，因为随着时间的推移它会让构造函数变得混乱。构造函数目
>的只是实例化类以及所有的属性。这就是为什么我们应该把业务逻辑应该定义在构造
>函数之外。
>
>代码示例:
>
>```jsx
>class ExplainBindingsComponent extends Component {
>    constructor() {
>        super();
>        this.doSomething = this.doSomething.bind(this);
>        this.doSomethingElse = this.doSomethingElse.bind(this);
>    }
>    doSomething() {
>// do something
>    }
>    doSomethingElse() {
>// do something else
>    }
>...
>}
>```
>
>最后值得一提的是类方法可以通过 ES6 的箭头函数做到自动地绑定。
>
>代码示例:
>
>```jsx
>class ExplainBindingsComponent extends Component {
>    onClickMe = () => {
>        console.log(this);
>    }
>    render() {
>        return (
>            <button onClick={this.onClickMe} type="button">
>                Click Me
>            </button>
>        );
>    }
>}
>```
>
>如果在构造函数中的重复绑定对你有所困扰，你可以使用这种方式代替。React 的官方文
档中坚持在构造函数中绑定类方法，所以本书也会采用同样的方式。

### 事件处理
>本章节会让你对元素的事件处理有更深入的了解，在应用程序中，将使用下面的按
>钮来从列表中忽略一项内容.
>
>代码示例(src/App.js):
>
>```jsx
><button onClick={() => this.onDismiss(item.objectID)} type="button">
>	Dismiss
></button>
>```
>
>这已经是一个复杂的例子了，因为必须传递一个参数到类的方法，因此需要将它封装
>到另一个（箭头）函数中，基本上，由于要传递给事件处理器使用，因此它必须是一个函
>数。下面的代码不会工作，因为类方法会在浏览器中打开程序时立即执行。
>
>代码示例(src/App.js):
>
>```jsx
><button onClick={() => this.onDismiss(item.objectID)} type="button">
>	Dismiss
></button>
>```
>
>当使用 onClick={doSomething()} 时，doSomething() 函数会在浏览器打开程序时立即执行，由于监听表达式是函数执行的返回值而不再是函数，所以点击按钮时不会有任何事发生。
>但当使用 onClick={doSomething} 时，因为 doSomething 是一个函数，所以它会在点击按钮时执行。同样的规则也适用于在程序中使用的 onDismiss() 类方法。
>然而，使用 onClick={this.onDismiss} 并不够，因为这个类方法需要接收 item.objectID 属性来识别那个将要被忽略的项，这就是为什么它需要被封装到另一个函数中来传递这个属性。这个概念在 JavaScript 中被称为高阶函数，稍后会做简要解释。
>
>代码示例(src/App.js):
>
>```jsx
><button onClick={() => this.onDismiss(item.objectID)} type="button">
>	Dismiss
></button>
>```
>
>其中一个解决方案是在外部定义一个包装函数，并且只将定义的函数传递给处理程序。因
>为需要访问特定的列表项，所以它必须位于 map 函数块的内部.
>
>代码示例(src/App.js):
>
>```jsx
>import React, {Component} from 'react';
>import './App.css';
>
>const list = [
>{
>title : "React",
>url : 'https://facebook.github.io/react/',
>author : "wuhy",
>num_comments: 3,
>points : 4,
>objectID : 0,
>},
>
>];
>
>class  App extends Component{
>constructor(props) {
>super(props);
>this.state = {
>list: list,
>};
>this.onDismiss = this.onDismiss.bind(this);
>}
>onDismiss(id){
>const isNotId = item => item.objectID !== id;
>const updateList = this.state.list.filter(isNotId);
>this.setState({list: updateList});
>}
>render() {
>return (
><div className="App">
> {this.state.list.map(item => {
>         const onHandleDismiss = () =>
>             this.onDismiss(item.objectID);
>         return (
>             <div key={item.objectID}>
>                 <span>
>                     <a href={item.url}>{item.title}</a>
>                 </span>
>                 <span>{item.author}</span>
>                 <span>{item.num_comments}</span>
>                 <span>{item.points}</span>
>                 <span>
>                     <button onClick={onHandleDismiss} type="button">
>                         Dismiss
>                     </button>
>                 </span>
>             </div>
>         );
>     }
> )}
></div>
>);
>}
>}
>export default App;
>```
>
>毕竟，传给元素事件处理器的内容必须是函数。作为一个示例，请尝试以下代码：
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>...
>render() {
>return (
><div className="App">
> {this.state.list.map(item =>
>     ...
>     <span>
>     <button
>     onClick={console.log(item.objectID)}
>     type="button"
>     >
>     Dismiss
>     </button>
>     </span>
>     </div>
>     )}
></div>
>);
>} 
>}
>```
>
>它会在浏览器加载该程序时执行，但点击按钮时并不会。而下面的代码只会在点击按钮时
>执行。它是一个在触发事件时才会执行的函数。
>
>代码示例(src/App.js):
>
>```jsx
><button
>onClick={function () {
>console.log(item.objectID)
>}}
>type="button"
>>
>Dismiss
></button>
>```
>
>为了保持简洁，可以把它转成一个 JavaScript ES6 的箭头函数，和我们在 onDismiss() 类方法时做的一样
>
>代码示例(src/App.js):
>
>```jsx
><button
>onClick={() => console.log(item.objectID)}
>type="button"
>>
>	Dismiss
></button>
>```
>
>经常会有 React 初学者在事件处理中使用函数遇到困难，这就是为什么我要在这里更详细
>的解释它。最后，应该使用下面的代码来拥有一个可以访问 item 对象的 objectID 属性
>简洁的内联 JavaScript ES6 箭头函数。
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>...
>    render() {
>        return (
>            <div className="App">
>                {this.state.list.map(item =>
>                    <div key={item.objectID}>
>                        ...
>                        <span>
>                            <button onClick={()=>this.onDismiss(item.objectID)}type="button">
>                                Dismiss
>                            </button>
>                        </span>
>                    </div>
>                )}
>            </div>
>        );
>    } 
>}
>```
>
>另一个经常会被提到的性能相关话题是在事件处理程序中使用箭头函数的影响。例如，
onClick 事件处理中的 onDismiss() 方法被封装在另一个箭头函数中以便能传递项标识。因
此每次 render() 执行时，事件处理程序就会实例化一个高阶箭头函数，它可能会对你的程
序性能产生影响，但在大多数情况下你都不会注意到这个问题。假设你有一个包含1000个
项目的巨大数据表，每一行或者列在事件处理程序中都有这样一个箭头函数，这个时候就
需要考虑性能影响，因此你可以实现一个专用的按钮组件来在构造函数中绑定方法，但这
是一个不成熟的优化。所以现在，专注到学习 React 会更有价值.

### 和表单交互

>让我们在程序中加入表单来体验 React 和表单事件的交互，我们将在程序中加入搜索功能，
>列表会根据输入框的内容对标题进行过滤。
>第一步，你需要在 JSX 中定义一个带有输入框的表单.
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>constructor() {
>super();
>this.state = {
>list,
>};
>}
>render() {
>return(
><div className="App">
><form>
><input type="text"/>
></form>
>{this.state.list.map(item =>
>)}
></div>
>);
>}
>}
>```
>
>在下面的场景中，将会使用在输入框中的内容作为搜索字段来临时过滤列表。为了能根据
>输入框的值过滤列表，你需要将输入框的值储存在本地状态中，但是如何访问这个值
>呢？你可以使用 React 的合成事件来访问事件返回值。
>让我们为输入框定义一个 onChange 处理程序。
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>constructor() {
>super();
>this.state = {
>list,
>};
>}
>render() {
>return(
><div className="App">
><form>
><input type="text" onChange={this.onSearchChange}/>
></form>
>{this.state.list.map(item =>
>)}
></div>
>);
>}
>}
>```
>
>这个函数被绑定到组件上，因此再次成为一个类方法，你必定义方法并 bind 它。
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>constructor() {
>super();
>this.state = {
>list,
>};
>this.onSearchChange = this.onSearchChange.bind(this);
>this.onDismiss = this.onDismiss.bind(this);
>}
>onDismiss(id){
>const isNotId = item => item.objectID !== id;
>const updateList = this.state.list.filter(isNotId);
>this.setState({list: updateList});
>}
>onSearchChange() {
>
>}
>render() {
>return(
><div className="App">
><form>
><input type="text" onChange={this.onSearchChange}/>
></form>
>{this.state.list.map(item =>
>)}
></div>
>);
>}
>}
>```
>
>在元素中使用监听时可以在回调函数的签名中访问到 React 的合成事件.
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>	...
>	onSearchChange(event) {
>		...	
>	}
>	...
>}
>```
>
>event 对象的 target 属性中带有输入框的值，因此你可以使用 this.setState() 来更新本地
>的搜索词的状态了
>
>代码示例(src/App.js):
>
>```jsx
>class App extends Component {
>	...
>onSearchChange(event) {
>		  this.setState({ searchTerm: event.target.value });
>}
>	...
>}
>```
>
>此外，应该记住在构造函数中为 searchTerm 定义初始状态，输入框在开始时应该是空的，因此初始值应该是空字符串。
>
>代码示例(src/App.js):
>
>```jsx
>constructor() {
>super();
>this.state = {
>list,
>searchTerm: '',
>};
>this.onSearchChange = this.onSearchChange.bind(this);
>this.onDismiss = this.onDismiss.bind(this);
>}
>```
>
>现在将会把输入框每次变化的输入值储存到组件的内部状态中。
>关于一个在 React 组件中更新状态的简要说明，在使用 this.setState() 更新 searchTerm时应该把这个列表也传递进去来保留它才是公平的，但事实并非如此，React 的this.setState() 是一个浅合并，在更新一个唯一的属性时，他会保留状态对象中的其他属性，因此即使你已经在列表状态中排除了一个项，在更新 searchTerm 属性时也会保持不变。
>让我们回到程序中，现在列表还没有根据储存在本地状态中的输入字段进行过滤。基
>本上，你已经具有了根据 searchTerm 临时过滤列表的所有东西。那么怎么暂时的过滤它
>呢？你可以在 render() 方法中，在 map 映射列表之前，插入一个过滤的方法。这个过滤方
>法将只会匹配标题属性中有 searchTerm 内容的列表项。你已经使用过了 JavaScript 内置的
>filter 功能，让我们再用一次，你可以在 map 函数之前加入 filter 函数，因为 filter 函数返回
>一个新的数组，所以 map 函数可以这样方便的使用
>
>代码示例(src/App.js):
>
>```jsx
>render() {
>return(
><div className="App">
>    <form>
>        <input type="text" onChange={this.onSearchChange}/>
>    </form>
>    {this.state.list.filter(...).map(item =>
>    )}
></div>
>);
>}
>```
>
>让我们用一种不同的方式来处理过滤函数，我们想在 ES6 组件类之外定义一个传递给过滤
>函数的函数参数，在这里我们不能访问到组件内的状态，所以无法访问 searchTerm 属性来
>作为筛选条件求值，我们需要传递 searchTerm 到过滤函数并返回一个新函数来根据条件求
>值，这叫做高阶函数。
>一般来说，我不会提到高阶函数，但在 React 中了解高阶函数是有意义的，因为在 React 中
>有一个高阶组件的概念，你将在这本书的后面了解到这个概念。但现在，让我们关注到过
>滤器的功能。
>首先，你需要在 App 组件外定义一个高阶函数。
>
>代码示例(src/App.js):
>
>```jsx
>function isSearched(searchTerm) {
>return function(item) {
>// some condition which returns true or false
>}
>}
>class App extends Component {
>...
>}
>```
>
>该函数接受 searchTerm 并返回另一个函数，因为所有的 filter 函数都接受一个函数作为它
>的输入，返回的函数可以访问列表项目对象，因为它是传给 filter 函数的函数。此外，返回
>的函数将会根据函数中定义的条件对列表进行过滤。让我们来定义条件
>
>代码示例(src/App.js):
>
>```jsx
>function isSearched(searchTerm) {
>return function (item) {
>   return item.title.toLowerCase().includes(searchTerm.toLowerCase());
>}
>}
>```
>
>条件是列表中项目的标题属性和输入的 searchTerm 参数相匹配，你可以使用 JavaScript 内
>置的 includes 功能来实现这一点。只有满足匹配时才会返回 true 并将项目保留在列表中。
>当不匹配时，项目会从列表中移除。但需要注意的是，你需要把输入内容和待匹配的内容
>都转换成小写，否则，搜索词 ‘redux’ 和列表中标题叫 ‘Redux’ 的项目无法匹配。由于我们
>使用的是一个不可变的列表，并使用 filter 函数返回一个新列表，所以本地状态中的原始列
>表根本就没有被修改过。
>还有一点需要注意，我们使用了 Javascript 内置的 includes 功能，它已经是一个 ES6 的特性
>了。这在 ES5 中该如何实现呢？你将使用 indexOf() 函数来获取列表中项的索引，当项目
>在列表中时，indexOf() 将会返回它的索引。
>
>代码示例:
>
>```jsx
>// ES5 语法
>string.indexOf(pattern) !== -1
>// ES6 语法
>string.includes(pattern)
>```
>
>另一个优雅的重构可以用 ES6 箭头函数完成，它可以让函数更加整洁:
>
>代码示例:
>
>```jsx
>// ES5
>function isSearched(searchTerm) {
>	return function(item) {
>		return item.title.toLowerCase().includes(searchTerm.toLowerCase());
>	}
>}
>// ES6
>const isSearched = searchTerm => item =>
>item.title.toLowerCase().includes(searchTerm.toLowerCase());
>```
>
>人们会争论哪个函数更易读，就我个人而言，我更习惯第二个。React 的生态使用了大量
>的函数式编程概念。通常情况下，会使用一个函数返回另一个函数（高阶函数）。在
>JavaScript ES6 中，可以使用箭头函数更简洁的表达这些。
>最后，你需要使用定义的 isSearched() 函数来过滤你的列表，你从本地状态中传递
>searchTerm 属性返回一个根据条件过滤列表的输入过滤函数。之后它会映射过滤后的
>列表用于显示每个列表项的元素。
>
>代码示例(src/App.js完整版)搜索功能:
>
>```jsx
>import React, { Component } from 'react';
>import './App.css';
>
>const list = [
>    {
>        title : "React",
>        url : 'https://facebook.github.io/react/',
>        author : "wuhy",
>        num_comments: 3,
>        points : 4,
>        objectID : 0,
>    },
>    {
>        title : "Redux",
>        url : 'https://facebook.github.io/react/',
>        author : "wuhy",
>        num_comments: 4,
>        points : 5,
>        objectID : 1,
>    },
>];
>// function isSearched(searchTerm) {
>//     return function (item) {
>//         return item.title.toLowerCase().includes(searchTerm.toLowerCase());
>//     }
>// }
>const isSearched = searchTerm => item =>
>    item.title.toLowerCase().includes(searchTerm.toLowerCase());
>
>class App extends Component {
>    constructor() {
>        super();
>        this.state = {
>            list,
>            searchTerm: '',
>        };
>        this.onSearchChange = this.onSearchChange.bind(this);
>        this.onDismiss = this.onDismiss.bind(this);
>    }
>    onDismiss(id){
>        const isNotId = item => item.objectID !== id;
>        const updateList = this.state.list.filter(isNotId);
>        this.setState({list: updateList});
>    }
>    onSearchChange(event) {
>        this.setState({searchTerm: event.target.value});
>    }
>  render() {
>      return(
>          <div className="App">
>              <form>
>                  <input type="text" onChange={this.onSearchChange}/>
>              </form>
>              {this.state.list.filter(isSearched(this.state.searchTerm)).map(item =>{
>                  const onHandleDismiss = () =>
>                      this.onDismiss(item.objectID);
>                  return (
>                      <div key={item.objectID}>
>                          <span>
>                              <a href={item.url}>{item.title}</a>
>                          </span>
>                          <span>{item.author}</span>
>                          <span>{item.num_comments}</span>
>                          <span>{item.points}</span>
>                          <span>
>                              <button onClick={onHandleDismiss} type="button">
>                                  Dismiss
>                              </button>
>                          </span>
>                      </div>
>                  );
>                  }
>              )}
>          </div>
>      );
>  }
>}
>
>export default App;
>```
>

### ES6 解构
>在 JavaScript ES6 中有一种更方便的方法来访问对象和数组的属性，叫做解构。比较下面
>JavaScript ES5 和 ES6 的代码片段
>代码示例:
>
>```jsx
>const user = {
>    firstname: 'Robin',
>    lastname: 'Wieruch',
>};
>// ES5
>var firstname = user.firstname;
>var lastname = user.lastname;
>console.log(firstname + ' ' + lastname);
>// output: Robin Wieruch
>// ES6
>const { firstname, lastname } = user;
>console.log(firstname + ' ' + lastname);
>// output: Robin Wieruch
>```
>
>在 JavaScript ES5 中每次访问对象的属性都需要额外添加一行代码，但在 JavaScript ES6 中
>可以在一行中进行。可读性最好的方法是在将对象解构成多个属性时使用多行。
>
>代码示例:
>
>```jsx
>const {
>    firstname,
>    lastname
>} = user;
>```
>
>对于数组一样可以使用解构，同样，多行代码会使你的代码保持可读性。
>
>代码示例:
>
>```jsx
>const users = ['Robin', 'Andrew', 'Dan'];
>const [
>    userOne,
>    userTwo,
>    userThree
>] = users;
>console.log(userOne, userTwo, userThree);
>// output: Robin Andrew Dan
>```
>
>也许已经注意到，程序组件内的状态对象也可以使用同样的方式解构，你可以让 map 和
>filter 部分的代码更简短。
>
>代码示例(src/App.):
>
>```jsx
>render() {
>    const { searchTerm, list } = this.state;
>    return (
>        <div className="App">
>            ...
>            {list.filter(isSearched(searchTerm)).map(item =>
>                ...
>                )}
>        </div>
>    );
>```
>
>也可以使用 ES5 或者 ES6 的方式来做
>
>代码示例:
>
>```jsx
>// ES5
>var searchTerm = this.state.searchTerm;
>var list = this.state.list;
>
>// ES6
>const { searchTerm, list } = this.state;
>```
>
>但由于这本书大部分时候都使用了 JavaScript ES6，所以也可以坚持使用它

### 受控组件
>现在了解了 React 中的单向数据流，同样的规则适用于更新本地状态 searchTerm 来过滤
>列表的输入框。当状态变化时，render() 方法将再次运行，并使用最新状态中的 searchTerm
>值来作为过滤条件。
>但是我们是否忘记了输入元素的一些东西？一个 HTML 输入标签带有一个 value 属性，这
>个属性通常有一个值作为输入框的显示，在本例中，它是 searchTerm 属性。然而，看起来
>我们在 React 好像并不需要它。
>这是错误的，表单元素比如 <input>, <textarea> 和 <select> 会以原生 HTML 的形式保存他
>们自己的状态。一旦有人从外部做了一些修改，它们就会修改内部的值，在 React 中这被
>称为不受控组件，因为它们自己处理状态。在 React 中，你应该确保这些元素变为受控组
>件。
>你应该怎么做呢？你只需要设置输入框的值属性，这个值已经在 searchTerm 状态属性中保
>存了，那么为什么不从这里访问呢
>
>代码示例(src/App.):
>
>```jsx
>class App extends Component {
>...
>    render() {
>        const { searchTerm, list } = this.state;
>        return (
>            <div className="App">
>                <form>
>                    <input
>                        type="text"
>                        value={searchTerm}
>                        onChange={this.onSearchChange}
>                    />
>                </form>
>                ...
>            </div>
>        );
>    }
>}
>```
>
>就是这样。现在输入框的单项数据流循环是自包含的，组件内部状态是输入框的唯一数据
来源。
整个内部状态管理和单向数据流可能对你来说比较新，但一旦习惯了它，就会自然而
然的在 React 中实现它。一般来说，React 带来一种新的模式，将单向数据流引入到单页面
应用的生态中，到目前为止，它已经被几个框架和库所采用

### 拆分组件
>现在，你有一个大型的 App 组件。它在不停地扩展，最终可能会变得混乱。你可以开始将
>它拆分成若干个更小的组件。
>让我们开始使用一个用于搜索的输入组件和一个用于展示的列表组件。
>
>代码示例(src/App.):
>
>```jsx
>class App extends Component {
>...
>render() {
>   const { searchTerm, list } = this.state;
>   return (
>       <div className="App">
>           <Search />
>           <Table />
>       </div>
>   );
>}
>}
>```
>
>你可以给组件传递属性并在组件中使用它们。至于 App 组件，它需要传递由本地状态(state) 托管的属性和它自己的类方法。
>
>代码示例(src/App.):
>
>```jsx
>class App extends Component {
>...
>    render() {
>        const { searchTerm, list } = this.state;
>        return (
>            <div className="App">
>                <Search
>                    value={searchTerm}
>                    onChange={this.onSearchChange}
>                />
>                <Table
>                    list={list}
>                pattern={searchTerm}
>                 onDismiss={this.onDismiss}
>            />
>    </div>
>    );
>    }
>}
>```
>
>现在可以接着 App 组件定义这些组件。这些组件仍然是 ES6 类组件，它们会渲染和之前相同的元素
>
>第一个是 Search 组件。
>
>代码示例(src/App.):
>
>```jsx
>class App extends Component {
>...
>}
>class Search extends Component {
>    render() {
>        const { value, onChange } = this.props;
>        return (
>            <form>
>                <input
>                    type="text"
>                    value={value}
>                    onChange={onChange}
>                />
>            </form>
>        );
>    }
>}
>```
>
>第二个是 Table 组件。
>
>代码示例(src/App.):
>
>```jsx
>//table组件
>class Table extends Component{
>    render() {
>        const {list,pattern,onDismiss} = this.props;
>        return (
>            <div>
>                {list.filter(isSearched(pattern)).map(item =>
>                    <div key={item.objectID}>
>                        <span>
>                            <a href={item.url}>{item.title}</a>
>                        </span>
>                        <span>{item.author}</span>
>                        <span>{item.num_comments}</span>
>                        <span>{item.points}</span>
>                        <span>
>                            <button onClick={() => onDismiss(item.objectID)} type="button">
>                                Dismiss
>                            </button>
>                        </span>
>                    </div>
>                )};
>            </div>
>        );
>    }
>}
>```
>
>现在有了三个 ES6 类组件。可能已经注意到，props 对象可以通过这个类实例的 this来访问。props 是 properties 的简写，当在 App 组件里面使用它时，它有传递给这些组件的所有值。这样，组件可以沿着组件树向下传递属性。
从 App 组件中提取这些组件之后，就可以在别的地方去重用它们了。因为组件是通过props 对象来获取它们的值，所以当在别的地方重用它时，可以每一次都传递不同的props，这些组件就变得可复用了

### 可组合组件
>在 props 对象中还有一个小小的属性可供使用: children 属性。通过它可以将元素从上层传递到你的组件中，这些元素对你的组件来说是未知的，但是却为组件相互组合提供了可能性。让我们来看一看，当你只将一个文本（字符串）作为子元素传递到 Search 组件中会怎样。