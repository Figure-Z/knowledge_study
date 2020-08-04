## React组件
创建react组件的方式有很多种接下来先看一个示例。
封装一个输出"Hello World!"的组件。
```js
function HelloMessage(props) {
    return <h1>Hello World!</h1>;
}
 
const element = <HelloMessage />;
 
ReactDOM.render(
    element,
    document.getElementById('example')
);
```
