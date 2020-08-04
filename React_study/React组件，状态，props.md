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

```
