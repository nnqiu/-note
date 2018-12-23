# ajax

1.所有数据请求和管理都存放在唯一的一个跟组件里面集中发生请求，从服务器端获取的数据都放在这个组件的state里面，通过props把数据传给子组件

2.多个容器组件，两种，一种展示型组件 一种容器性组件

展示型组件没有任何状态  数据从容器组件获取，容器组件发送ajax请求

3.把所有网络请求交给redux处理

# 标准的组件结构

```
 class  definition
     costructor
           event  handlers
     component  lifecycle  event
     getters
     render
 Person.defaultProps = {
  name:'Guest'
}
 proptypes.propTypes = {
  name: React.propTypes.string//验证接受的props是否为正确的属性
}
```



一定要写propTypes   Person.propTypes = { name: React.PropType.string}

如果一个props不是requied，一定在getDefaultProps中设置它

React.propTypes主要用来验证组件接受到的props是否为正确的数据类型，如果不正确 console.log 中就会出现对应的warning，出于性能方面的考虑，这个api只在生产环境下使用

shape() arrayOf()

propsType: {

​        myObject: React.PropTypes.shape({

​        text:React.PropTypes.string

​        numbers: React.PropTypes.arrayOf(React.PropTyes.number),

})

}



# Render()计算和条件判断



### 1.组件的state中不能出现props

​     constructor (props) {    this.state = {}}

### 2.保持this.state简洁 不要有计算过程

### 3.能用三元就不用if 直接在render里面

{this.name ==='abc' ?<div>:<div>}

### 4.不要把dispaly logic写在comWillReceiveProps或comWillMount中



react 进行局部刷新以保证性能