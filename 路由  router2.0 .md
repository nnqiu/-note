# 路由  router2.0 

1.安装  $ npm  install -S react-router



2.import  {Router}  from  'react-router'   路由器Router就是react的一个组件



3.

```
import  {Router,Route,hashHistory}  from  'react-router'
render((<Router history={hashHistory}>
            <Route>
                <Route path='/' component={App}/>
                //访问跟路由 
                <Route path='/repos' component={Repos}/>
                <Route path='/about' component={About}/>
            </Route>
        </Router>
),
document.getElementById('app'));
```

*路由的切换由url的hash变化决定，即url的#发生变化

  访问‘/’我们看到的就是  http://www.abc.com/#/

 访问‘/repos’我们看到的就是  http://www.abc.com/#/about

*嵌套路由

```
let routes = <Route path='/' component={App}>
    <Route path='/repos' component={Repos}/>
    <Route path='/repos' component={Repos}/>
</Route>
<Route routes={routes} history={browserHistory}
```

父组件 App里面的{this.props.children}就是子组件

# path属性

Route组件的path属性，不管路径是否匹配，总会加载指定组件

```
<Route path="inbox" component={Inbox}>
   <Route path="messages/:id" component={Message} />
</Route>
```

/inbox/messages/:id

```
<Route component={Inbox}>
  <Route path="inbox/messages/:id" component={Message} />
</Route>
```

/inbox/messages/:id

#### 两种方法  都加载 <Inbox></message></Inbox>

# 通配符

path属性可以使用通配符

1  :paramName

​     :paramName 匹配URL的一个部分，直到下一个/ ？ #

​     this.props.params.paramName

​     <Route path='/hello   /:name   '>

2  ()   表示URL的这个部分是可选的

​    <Route path='/hello   (/:name)   '>

3   *  匹配任意字符  直到模式里面的下一个字符为止，匹配方式是非贪婪模式

​     <Route path='files  /*.*'>

4    **   匹配任意字符  直到下一个/ ？ #为止，匹配方式是贪婪模式

​      <Route path=' /**/*.jpg '>

# IndexRoute 组件

和同级子组件放在一起 默认情况下加载，相当与index.html

```
<Router>
  <Route path="/" component={App}>
    <IndexRoute component={Home}/>
    <Route path="accounts" component={Accounts}/>
    <Route path="statements" component={Statements}/>
  </Route>
</Router>
```

# Redirect 组件

路由的跳转  用户访问一个路由，自动跳转另一个路由

<Route path='index' component={Index}>

​         <Redirect from='message/:id' to='/message/:id'/>

<Route/>

访问/index/messages/5  跳转到/messages/5

# IndexRedirect 组件

访问根路由的时候 用户重定向到某个子组件

```
<Route path="/" component={App}>
  ＜IndexRedirect to="/welcome" />
  <Route path="welcome" component={Welcome} />
  <Route path="about" component={About} />
</Route>
```

访问App根路由自动重定向到子组件welcome

# Link  就是a标签  接Router状态

render() {

​      return  <div>

​      <ul role='nav'>

​          <li><Link to='/about'  activiStyle={{color:"red"}}>about</Link></li>

​       </ul>

​       </div>

}

Link===>a标签

activeStyle===>style

# 路由器钩子

Enter  Leave用户进入或者离开路由触发

# History

browserHistory   #

hashHistory     #

createMemoryHistory    创建一个内存中的history对象

















