# React

ReactDOM.render(<h><h>,document.getElementById(example)),//将h1插入example节点

es6是es5的语法糖，两者只是写法不同，编译方式相同，es6编译成es5执行

从组件获取真实dom节点需要ref

一个组件一个状态机  

创建组件

1.createClass   es5    export default React.createClass{}

2.类继承React.Component  es6   class CommentItem extends React.Component{}

#### 挂载：

虚拟dom插入到真实dom这一过程叫做挂载 setState（{}）

挂载过程中react提供了多个生命周期函数 ，用来帮助用户识别挂载的进度

this:  es5自动把组件的this（也就是 组建的实例化）绑定的函数的this中



#### react实例的主要属性：props state refs， setState（｛｝）



var xingyifei = function(a) {b}
var xingyifei = (a) => {b}

更新虚拟dom要使用 setState({})

setState({key: value})

key:state里面的key，value 要覆盖的新值





如何运行react es6

1.安装nodejs境到电脑中

2.运行cmd控制台 进入到该项目中

3.进入项目后运行npm install等待……

4.运行npm start，启动项目

两个input  插入的位置 插入的值

一个button开始插入





变量HelloMessage是一个组件类，自动生成HelloMessage的一个实例

组件都有自己的render方法，用于输出组件

this.prop.children 读取组件的子节点

this.prop 一旦定义就不再改变的属性



#### PropTypes  组件类属性

组件的子节点的文本输入框 必须获取真实的dom节点 文本必须有ref属性

this.refs.ref的名字.focus() 获取输入的值

#### this.state

状态机 读取随用户互动而产生变化的特性

获取状态 调用this.render方法

挂载

this.setState({})  修改 状态值 每次修改后用this.render方法渲染组件





### 一个react组件生命周期

#### 实例化  存在期   销毁期



### 组件声明周期  React Component

### mounting  已插入  挂载的时候

### updating   正在被渲染  渲染时候

### unmounting  已移除

随着组件props或state发生改变其dom发生改变dom发生改变，一个组件就是一个状态机



一个react组件的生命周期分为三部分: 实例化 存在期 销毁时



当组件在客户端被实例化第一次被创建

#### 1.getDefaultProps   

#### 对于每个组件来说这个方法只调用一次 返回的对象可以设置默认的props值

#### 2.getInitialState  

#### 每个组件实例都会调用初始化每个实例的state

修改state会重新渲染组件，依次调用

1、shouldComponentUpdate
2、componentWillUpdate
3、render
4、componentDidUpdate

#### 3.componentWillMount 

#### 首次渲染之前调用 再render方法调用之前修改state的最后一次机会

#### 4.render

创建虚拟dom 这是唯一一个必须的方法

1. this.props  this.state访问数据
2. 可以返回null false 和任何react组件
3. 只能出现一个顶级组件，不能返回一组元素
4. 不能改变组件的状态
5. 不能修改dom的输出

#### 5.componentDidMount

#### 此时已经渲染出真实dom，通过this.getDOMNode()访问真实DOM

添加组件属性   class   className

​                         for   htmlFor

不能在render里面修改state

##### constructor(props,context)

创建组件的时候调用一次

##### componentWillMount()  

 组件挂载之前调用 在组件挂载之前调用一次 在这个函数里面调用setState，本次render函数可以看到更新后的state，并且只渲染一次

##### componentDidMount() 

父组件发生render子组件调用，这里使用refs

##### 1.componentWillReceiceProps(nextProps)

父组件给子组件，父组件发生render的时候子组件会调用



#### 2.bool  shouldComponentUpdate(nextProps,nextState)

组件挂载之后每次调用setState会调用此方法判断是否需要重新渲染，增加渲染效率，默认返回true，需要重新render

返回false可以提前退出更新路径

##### 3.void componentWillUpdate(nextProps,nextState)

shouldComponentUpdate返回true或者调用forceUpdate之后componentWillUpdate会被调用

##### void componentDidUpdate()

除了首次render之后调用componentDidMount,其他renderz结束之后调用这个

componentWillMount   cpmponnentDidMount  挂载的时候被调用

componentWillUpdate   componentDidUpdate  每次渲染之后调用





ReactElement render()

核心函数  不能在render函数里面修改state



void componentWillunmount()   卸载时候被调用  注册的事件在这里删除







# 更新方式

在react中，触发render的4条路径

##### 假设shouldComponentUpdate默认返回true的方式

1.首次渲染Initial Render

2.调用this.setState(不是一次setState触发一次render  react可能会合并操作，再一次性进行render )  有可能多次setState进行一次render

3.父组件发生更新（prop发生改变）就算props没有改变或者父子组件之间没有数据交换也会触发render

4.调用this.forceUpdate



虚拟dom插入文档变成真实dom 有时需要组件获取真实dom的节点，这时就要ref属性

this.refs.ref的name  获取真实dom 必须等虚拟dom插入文档以后才能使用这个属性







#### 组件已经渲染好并且用户可以与它进行交互

#### 1、componentWillReceiveProps

#### 2、shouldComponentUpdate

#### 3、componentWillUpdate

#### 4、render

#### 5、componentDidUpdate



# 一、实例化 mount

#### 当组件在客户端被实例化第一次被创建时

#### 1.getDefaultProps               

###### 每个组件类只调一次 返回的对象可以设置默认的prop值

#### 2.getInitialState                   

###### 每个组件实例只调一次 初始化每个实例的state

#### 3.componentWillMount

###### 渲染之前使用  修改state的最后一次机会

#### 4.render

###### 创建虚拟dom    1.this.props和this.state访问数据

######                              2.可以返回null false 或者任何react组件

######                              3.只有一个顶层组件

######                              4.不能改变组件的状态

######                              5.不能修改dom的输出                  

#### 5.componentDIdMount   

###### 此时渲染真实dom



#### 当组件在服务器端被实例化第一次被创建时

#### 1.getDefaultProps

#### 2.getInitialState

#### 3.componentWillMount

#### 4.render

5.componentdidMout不会在服务器端被渲染的过程中调用



# 二、存在期

#### 1、componentWillReceiveProps

父给子组件的方法，更新state以触发render方法重新渲染组件

#### 2、shouldComponentUpdate

判断是否需要重新渲染 false就不会往下进行以及render

#### 3、componentWillUpdate

重新渲染之前

#### 4、render

#### 5、componentDidUpdate

熏染之后调用修改dom



# 三、销毁时

comPonentWillUnmount react完成组件时，这个组件必须从dom中卸载销毁才能执行完成所有的清理和销毁工作





## 