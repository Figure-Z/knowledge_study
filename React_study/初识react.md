
::: hljs-center

# React+vscode项目搭建请参照一下网站：
https://blog.csdn.net/crazyhsf/article/details/81039059

:::
## React是什么？（组件形成ui界面）
React 是一个声明式，高效且灵活的用于构建用户界面的JavaScript 库。使用 React 可以将一些简短、独立的代码片段组合成复杂的 UI 界面，这些代码片段被称作“组件”。我们马上会讨论这些又奇怪、又像 XML 的标签。我们通过使用组件来告诉 React 我们希望在屏幕上看到什么。当数据发生改变时，React 会高效地更新并重新渲染我们的组件。
![示例1.png](0)
我们把这些参数叫做props，然后通过render方法返回需要展示在屏幕上的视图的层次结构。
## React的基本使用（测试）
### 基本元素定义
在react中元素（element）是构成其应用的最小单位，它同时用来描述在页面上显示的内容。
```react
const element = <h1>Hello, world!</h1>;
```
引入react的必备js文件
```JavaScript
<script src="https://cdn.staticfile.org/react/16.4.0/umd/react.development.js"></script>
<script src="https://cdn.staticfile.org/react-dom/16.4.0/umd/react-dom.development.js"></script>
<script src="https://cdn.staticfile.org/babel-standalone/6.26.0/babel.min.js"></script>
```

### 将元素渲染到DOM中
```html
<div id="example"></div>
```
```javascript
const element = <h1>Hello, world!</h1>;
ReactDOM.render(//使用render返回想要显示的信息
    element,  //返回内容
    document.getElementById('example') //返回位置（html）
);
```
### 更新元素渲染
React的元素都是不可变的，当元素一旦被创建，你是无法改变它的内容的。唯一的办法就是创建一个新的元素来更新你原来的元素信息。
```js
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>现在是 {new Date().toLocaleTimeString()}.</h2>
		//在这里创建获取时间的元素
    </div>
  );

  ReactDOM.render( // 调用render方法渲染
    element,
    document.getElementById('example')
  );

}
 
setInterval(tick, 1000);
 //使用setInterval方法，每1秒调用一次tick方法，使每次获取的新时间代替之前的时间来达到更新元素的效果。
```
```js
function Clock(props) { //封装成函数，参数为props
  return (
    <div>
      <h1>Hello, world!</h1>
      <h2>现在是 {props.date.toLocaleTimeString()}.</h2>
    </div>
  );
}
 
function tick() {
  ReactDOM.render(
    <Clock date={new Date()} />, //调用方法赋值
    document.getElementById('example')
  );
}
 
setInterval(tick, 1000);
```

在React中除了使用函数创建元素元素外，我们还可以创建一个React.Componment的ES6类，该类封装了要显示的元素，注意使用this.props
```js
class Clock extends React.Component {
  render() { //封装要显示的元素
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>现在是 {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
 
function tick() {
  ReactDOM.render(
    <Clock date={new Date()} />,
    document.getElementById('example')
  );
}
 
setInterval(tick, 1000);
```

## React JSX
React使用JSX来代替常规的JavaScript，它比JavaScript执行的更快，它是类型安全的，编写更加快速。
它用来声明React中的元素信息。
```js
const element = <h1>Hello, world!</h1>;//这种形式的就是jsx，一种JavaScript的扩展。
```

我们可以在jsx中嵌套多个HTML标签，但是需要使用一个<div></div>来包含着写元素，要想添加自定义属性则要使用"data-"前缀。
```js
ReactDOM.render(
    <div>
    <h1>菜鸟教程</h1>
    <h2>欢迎学习 React</h2>
    <p data-myattribute = "somevalue">这是一个很不错的 JavaScript 库!</p>
    </div>
    ,
    document.getElementById('example')
);
```
## 独立文件
创建显示元素React的jsx文件可以放在一个单独的js文件当中。
```js
//js文件
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
);
```
```html
<body>
  <div id="example"></div>
<script type="text/babel" src="helloworld_react.js"></script>
</body>
//引入外部js文件来完成元素显示。
```
## JavaScript表达式
在jsx中可以使用JavaScript表达式，但是要求表达式必须要在花括号中{}完成。
```js
ReactDOM.render(
    <div>
      <h1>{1+1}</h1> //网页显示结果为2
    </div>
    ,
    document.getElementById('example')
);
```
在jsx中无法使用if else语句但可以用conditional（三元运算）来代替。
```js
ReactDOM.render(
    <div>
      <h1>{i == 1 ? 'True!' : 'False'}</h1>
    </div>
    ,
    document.getElementById('example')
);
```
## 样式
React推荐使用内敛样式来对元素进行改变，它会在指定元素数字后面自动添加px。
```js
var myStyle = {
    fontSize: 100,
    color: '#FF0000'
};
ReactDOM.render(
    <h1 style = {myStyle}>菜鸟教程</h1>,
    document.getElementById('example')
);
```
## 注释
React中的注释需要写在花括号中
```js
ReactDOM.render(
    <div>
    <h1>菜鸟教程</h1>
    {/*注释...*/}
     </div>,
    document.getElementById('example')
);
```
## 数组
jsx中允许插入数组，但是


 



