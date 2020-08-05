## React组件
创建react组件的方式有很多种接下来先看一个示例。
封装一个输出"Hello World!"的组件。
```js
function HelloMessage(props) {
    return <h1>Hello World!</h1>;
}
 
const element = <HelloMessage />;//用户自定义组件
 
ReactDOM.render(
    element,
    document.getElementById('example')
);
```
可以看出我们可以通过函数的方法来定义组件。
```js
function HelloMessage(props) {
    return <h1>Hello World!</h1>;
}
```
同样也可以使用ES6的class来定义一个组件
```js
class Wwlcome extends React.Component{
    render(){
	return <h1>Hello World!</h1>;
    }
}
```
需要注意的是自定义的React类名必须以大写字母开头，且组件类只能包含一个顶层标签，否则也会报错。
## 向组件传递参数
在react中向组件传递参数，可以使用this.props对象。
```js
function HelloMessage(props) {
    return <h1>Hello {props.name}!</h1>;//通过对象来获取参数
}
 
const element = <HelloMessage name="Runoob"/>;//在自定义组件中对props.name进行赋值。
 
ReactDOM.render(
    element,
    document.getElementById('example')
);
```
需要注意的是，在添加属性是class要写成className，for属性需要写成htmlFor。
## 复合组件
在react中可以通过创建多个组件来合成一个组件。即吧组件的不同功能点分离开。
```js
function Name(props) {
    return <h1>网站名称：{props.name}</h1>;
}
function Url(props) {
    return <h1>网站地址：{props.url}</h1>;
}
function Nickname(props) {
    return <h1>网站小名：{props.nickname}</h1>;
}
function App() {
    return (
    <div>
        <Name name="百度" />
        <Url url="http://www.baidu.com" />
        <Nickname nickname="Baidu" />
    </div>
    );
}
 
ReactDOM.render(
     <App />,
    document.getElementById('example')
);
```
## React State(状态)
React把组件看成是一个状态机，通过与用户的交互，然后渲染UI，让用户界面和数据保持一致。
React里，只需要更新组件的state，然后根据新的state重新渲染用户界面。
添加一个类构造函数来初始化状态 this.state，类组件应始终使用 props 调用基础构造函数。
```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
 
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>现在是 {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
 
ReactDOM.render(
  <Clock />,
  document.getElementById('example')
);
```
## 将生命周期方法添加到类中
在具有很多组件的时候，销毁时释放资源是很重要的一件事情。
在每一个组件第一次加载到DOM中的时候，都会想着生成定时器，React中称为挂载，而当它被移除的时候，同时也想着清楚定时器，这被称为卸载。
```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
 
  componentDidMount() {//组件加载时
    this.timerID = setInterval(
      () => this.tick(),
      1000
    );
  }
 
  componentWillUnmount() {//组件销毁时
    clearInterval(this.timerID);
  }
 
  tick() {
    this.setState({
      date: new Date()
    });
  }
 
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>现在是 {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
 
ReactDOM.render(//主入口
  <Clock />,
  document.getElementById('example')
);

```
componentDidMount()方法
componentWillUnmount() 方法
被称作生命周期钩子。

在组件输出到DOM后会执行componentDidMount()钩子，我们就可以在这个钩子上设置一个定时器。this.timerID为定时器的ID我们可以在componentWillUnmount()钩子中卸载定时器。