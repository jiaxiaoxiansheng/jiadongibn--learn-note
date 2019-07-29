### flex
#### 容器上的属性(父级)
> `flex-direction`定义主轴的排列方向
> `flex-wrap`是否换行
  1. `nowrap`不换行,都在一行排列,会改变宽高
  2. `wrap`换行,不改变宽高,第一行在上面
  3. `wrap-reverse`换行,第一行在上面

> `flex-flow`是`flex-direction`和`flex-wrap`;默认值是`row`和`nowrap`

> `justify-content`项目在主轴的排列方向
  1. `flex-start`让项目元素左对齐
  2. `flex-end`右对齐
  3. `center`居中对齐
  4. `space-around`每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍
  5. `space-between`项目两端对齐,中间的项目等分

> `align-items`项目在交叉轴的对齐方式
    1. `center`居中(row时,上下方向居中)
    2. `flex-end`终点对齐(row时,下对齐)
    3. `flex-start`起点对齐(row时,上对齐)
    4. `stretch` 默认值,项目未设置高度时,默认占满整个容器

> `align-content`定义多个交叉轴的对齐方式,如果交叉轴上有两行

#### 项目上的属性(自己)
> `flex-grow`项目放大比例,默认为0,即使有空间也不放大
  + 如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍

> `flex-shink`项目缩小比例,默认为1,即空间不足,缩小该项目
  + 如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小

> `flex-basis`属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小

> `flex`flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选
  + 该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)

> `align-self`align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。