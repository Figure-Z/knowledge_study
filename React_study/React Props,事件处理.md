## React Props（是什么？）
props和state的主要区别是props是不可变的，而state是可以根据与用户交互来改变。
(state可以更新修改数据，props只能传递数据)

简单使用：name属性通过该props.name获取。
```js
function HelloMessage(props) {
    return <h1>Hello {props.name}!</h1>;
}
 
const element = <HelloMessage name="Runoob"/>;
 
ReactDOM.render(
    element,
    document.getElementById('example')
);
```
同时可以通过组件的defaultProps属性为props设置默认值。
```js
HelloMessage.defaultProps = {
  name: 'Runoob'
};//设置的默认值无法被改变
```
## state和props的组合使用
我们可以在父组件中设置 state， 并通过在子组件上使用 props 将其传递到子组件上。
```js
class WebSite extends React.Component {
  constructor() {
      super();
 
      this.state = {
        name: "百度",
        site: "https://www.baidu.com"
      }
    }
  render() {
    return (//只放在了div里面
      <div>
        <Name name={this.state.name} />
        <Link site={this.state.site} />
      </div>
    );
  }
}
 
 
 
class Name extends React.Component {
  render() {
//通过props将其放入了其他的标签
    return (
      <h1>{this.props.name}</h1>
    );
  }
}
 
class Link extends React.Component {
  render() {
    return (
      <a href={this.props.site}>
        {this.props.site}
      </a>
    );
  }
}
 
ReactDOM.render(
  <WebSite />,
  document.getElementById('example')
);
```
运行结果为：
![运行结果.png](0)

## React事件处理
React元素的事件处理和DOM元素类似，但语法略有区别，在React中时间绑定的属性名采用驼峰式写法。

HTML的绑定事件写法：
```html
<button onclick="activateLasers()">
  激活按钮
</button>
```

React中的绑定事件写法：
```HTML
<button onClick={activateLasers}>
  激活按钮
</button>
```

在React中另一个不同是，不能视同返回false的方式阻止默认行为，你不许明确使用preventDefault。

通常我们在 HTML 中阻止链接默认打开一个新页面
```html
<a href="#" onclick="console.log('点击链接'); return false">
  点我
</a>
```

React中的写法：
```js
function ActionLink() {
  function handleClick(e) {
    e.preventDefault();
    console.log('链接被点击');
  }
 
  return (
    <a href="#" onClick={handleClick}>
      点我
    </a>
  );
}
```











