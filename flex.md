# flexbox 灵活的盒子容器

在不同方向排列元素

重新排列元素的显示顺序

更改元素的对齐方式

动态的将元素装入容器

# 避免使用flexbox

整体页面布局

完全支持旧浏览器的网页

#### 排列方向

flex-direction:  

- `row`（默认值）：主轴为水平方向，起点在左端。

- `row-reverse`：主轴为水平方向，起点在右端。

- `column`：主轴为垂直方向，起点在上沿。

- `column-reverse`：主轴为垂直方向，起点在下沿。

  ​

flex-wrap:

`nowrap`（默认）：不换行

`wrap`：换行，第一行在上方。

`wrap-reverse`：换行，第一行在下方。



flex-flow:

`flex-flow`属性是`flex-direction`属性和`flex-wrap`属性的简写形式，默认值为`row nowrap`。



justift-content: 定义了项目在主轴上的对齐方式

- flex-start`（默认值）：左对齐
- flex-end`：右对齐
- center`： 居中
- space-between`：两端对齐，项目之间的间隔都相等。
- space-around`：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。



align-items属性  在交叉轴对齐

- `flex-start`：交叉轴的起点对齐。
- `flex-end`：交叉轴的终点对齐。
- `center`：交叉轴的中点对齐。
- `baseline`: 项目的第一行文字的基线对齐。
- `stretch`（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。



align-content

定义多根轴线的对齐方式,如果只有一根轴线，该属性不起作用

- `flex-start`：与交叉轴的起点对齐。
- `flex-end`：与交叉轴的终点对齐。
- `center`：与交叉轴的中点对齐。
- `space-between`：与交叉轴两端对齐，轴线之间的间隔平均分布。
- `space-around`：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
- `stretch`（默认值）：轴线占满整个交叉轴。







order:  定义项目排列顺序  order: 0

​              数值越小排列越靠前



flex-grow:  定义项目的放大比例  如果都1为均分



flex-shrink:  定义项目的缩小比例    如果空间不足将缩小



flex-basis:   在分配多余空间之前项目占据主轴空间,计算主轴是否有多余空间默认auto





`flex`属性是`flex-grow`, `flex-shrink` 和 `flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选。





`align-self`属性允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`。



































