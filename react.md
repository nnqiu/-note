react

```
js部分：first-引入JSX语法糖对应的解析JS，以及react.js库
<Script src="react.js"></Script>
<Script src="JSXTransformer.js"></Script>/*注意，0.14之后，依赖库已经改为browser.js*/
然后写JSX的Script标签内的type要改
<Script type="text/jsx">/*注意，0.14之后，标签已经改为text/bable*/
    var Hello = React.createClass({
        render: function(){
            /*添加组件属性，有一个地方需要注意，就是 class 属性需要写成 className ，for 属性需要写成 htmlFor ，这是因为 class 和 for 是 JavaScript 的保留字。然后，属性名都是驼峰命名法*/
            return <div className="fontcolor">Hello {this.props.name}</div>
        }
    });
    ReactDOM.render(
        <Hello name="World" ></Hello>,
        document,getElementById('example');
    );
</Script>
```

```
1. JSX 实际上是一种语法糖，写法类似原生的HTML 嵌套一些JS 变量，其中的JS 变量部分需要用一对大括号包括（如视频里的`{this.props.name}`）。JSX 最终会由解析器编译成真正的JS（视频里没讲到的是，JSX 并不是必须的，需要渲染的内容完全可以直接用JS 写）；
2. JSX 中如果要为标签设置类属性，其名称应为`className`；因为`class`是JS 里的关键字（JSX 只是语法糖，最后要被编译成JS，所以要考虑JS 的语法约束）；
3. JSX 中为标签设置样式属性，属性值应为一个对象；由于对象的字面量形式包括一对大括号，所以实际写法应该是`style={{color: "red", fontSize: '16px'}}`。注意到这里定义字体大小用的是`fontSize`而不是`font-size`，因为JS 操作CSS 属性名就是以驼峰形式的。
```

1.类form结构，以及自定义html标签，这些统称为react Components，这并不是html标签，只是react Components的实例，通过调用ReactDOM.render(，)方法,第一个参数是需要渲染的react Components，第二个参数是渲染完以后需要呈现的Element位置自定义的Components通过调用React.createClass()方法创建，参数是JS的object，

```
var Hello = React.createClass({
  render: function() {
    return <div>Hello {this.props.name}</div>;
  }

});

ReactDOM.render(
  <Hello name="World" />,
  document.getElementById('container')
);
```

{}表示其中要执行JS表达式的值this是指当前Components的实例，props表示使用react Components时，在其上添加的属性的集合，key值和定义时候的值相同例如{this.props.name}的值为World，和定义的name值相同class 在ES6中，是一个关键字，用来声明一个类，在之前的ES5等标准中，是一个保留字，所以，在react中，不能再标签上直接写class，因为其是JS运行环境。声明css样式可以使用className。在react中行内样式不是 用字符串的形式表示，需要用样式对象来表示。eg：style={{color:'red'}},写法符合驼峰标示。

组件定义：React.createClass组件使用：React.render(组件&props, 插入element)JSX语法：css类：className行内样式: style={{color: 'red'}} 或 style={object} (object = {color: 'red',fontSize: '16px'})\\CSS 属性名就是以驼峰形式的jsx参数：{this.props.(你定义的参数id)}



react核心

1.props

2.state

react网页源码结构

```
<!DOCTYPE html>
<html>
  <head>
    <script src="../build/react.js"></script>
    <script src="../build/react-dom.js"></script>
    <script src="../build/browser.min.js"></script>
  </head>
  <body>
    <div id="example"></div>
    <script type="text/babel">
      // ** Our code goes here! **
    </script>
  </body>
</html>
```

<script>标签最后一个type属性text/babel（因为react独有jsx语法，跟javascript不兼容）

代码使用库

react.js是react核心库

react-dom.js是提供与DOM相关的功能

Brower.js是将jsx语法转化为js语法(耗时，实际上线应放到服务器完成)

```
$ babel src --out-dir build
```

以上代码可将src目录的js文件进行语法转换，转码后的文件全部放在build子目录

##### React Components Life

Mounted React.renderComponent

Update 重新渲染

Unmounted 移除DOM

hoop函数   will did 

Mounting阶段  component	WillMount(Mounting前被调用)

​                           component	DidMount(Mounting后被调用)

```
var Hello = React.createClass({
    getInitialState:function(){
       alert('init')
       return{
        opacity:1.0;
        fontSize:'12px'
      }
  }
    render:function(){
      return <div style={{opacity:this.state.opacity,fontSize:this.state.fontSize}}>hello{this.props.name}</div>
    }
    componentWillMount:function(){
      alert('will')
    }
    componentDidMount:function(){
      alert('did')
      var self = this;
      window,setTimeOut(function(){
      self.setState({
      opacity:0.5,
      fontSize:'44px'
    },1000)
})
    }
});
React.render(<Hello name='world'/>)
document.getElementById('container')




```

Update阶段      component	WillUpdate

​                           component	DidUpdate

Unmount阶段  component	WillUnmount

```
var tipE = ReactDOM.findDOMNode(this.refs.tip);
```

```
React.render换成ReactDOM.render
```

```
stopPropagation()停止事件冒泡
preventDefault()停止事件默认行为
React.findDOMNode(this.fess.<ref属性的值>): 索引子组键的dom元素
```



Demo1

	<!DOCTYPE html>
	<html>
	
	<head>
		<meta charset="UTF-8">
		<title></title>
		<script type="text/javascript" src="js/react.js" ></script>
		<script type="text/javascript" src="js/react-dom.js" ></script>
		<script type="text/javascript" src="js/browser.min.js" ></script>
	</head>
	<body>
		<div id="example"></div>
		<script type="text/babel">
			ReactDOM.render(
				<h1>HelloWorld</h1>,
				document.getElementById("example")
			);
		</script>
	</body>
	</html>
React.render(html,)方法将模板转为HTML语言，并插入指定的dom结点

Demo2

		<div id="example"></div><script type="text/babel">
			var names = ['Alice', 'Emily', 'Kate'];
			ReactDOM.render(
				<div> 
				{
					names.map(function (name, index) {
						return <div key={index}>hello,{name}!</div>
					})
				}		
				</div>,
				document.getElementById('example')
			);
		</script>
JSX语言,允许HTML与JavaScript的混写，遇到HTML标签用HTML规则解析，遇到代码块(以{开头)使用js解析



Demo3


			ReactDOM.render(
				<div>{arr}</div>,
				document.getElementById("example")
			);	
div的变量是一个数组时，会展开这个数组的所有成员

Demo4 组件

			var HelloMessage = React.createClass({
	        render:function(){
					return <h1>Hello {this.props.name}</h1>;
				}
			});
			
			ReactDOM.render(
				<HelloMessage name="quiunan" />,
				document.getElementById('example')
			);
将代码封装成组件，在html插入该组件，React.createClass()用于生成一个组件类，

插入<HelloMessage/>时自动生成HelloMessage实例

所有组件都必须有自己的render方法，用于输出组件

注意，组件类的第一个字母必须大写，否则会报错，比如`HelloMessage`不能写成`helloMessage`。另外，组件类只能包含一个顶层标签，否则也会报错。

Demo5 

this.props.children 表示组件的所有子节点

当前组件没有子节点：undefined

只有一个子节点：数据类型object

有多个子节点：数据类型array

React.Chirdren.map 遍历子节点

Demo6

PropTypes 属性，检验组件实例是否符合要求

getDefaultProps 方法，设置组件属性的默认值

this.props 一旦定义就不再改变

Demo7获取真实的dom节点

虚拟dom插入真实dom，从组件获取真实dom的节点，ref属性

this.refs.[ref的name]——返回这个真实的DOM节点



Demo8 this.state

this.state 会随着用户互动而产生变化的特性

Demo9

hadleChange:function(){

​     this.setState({value:event.tatrget.value})

}

Demo10组件的生命周期

Mounting:已插入真实DOM

Updating:正在被重新渲染

Unmounting:已移除真实Dom

- componentWillMount()
- componentDidMount()
- componentWillUpdate(object nextProps, object nextState)
- componentDidUpdate(object prevProps, object prevState)
- componentWillUnmount()


- componentWillReceiveProps(object nextProps)：已加载组件收到新的参数时调用
- shouldComponentUpdate(object nextProps, object nextState)：组件判断是否重新渲染时调用

























































