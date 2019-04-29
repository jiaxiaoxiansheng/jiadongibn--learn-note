### HTML与CSS
+ 让鼠标变成小手样式，cursor:pointer。input原本的边框消失outline：none。表单value值：设置默认值和placeholder类似。

+ 嵌套崩塌：给子类设置margin-top，但是作用在了父类元素上，解决办法，设置overflow

+ 如果背景图片是整个网页，用img元素，width设置100%，背景图片上的样式用绝对定位，数值使用百分比（或者给父类设置绝对定位，子类用margin：0auto）；也可以给元素设置一个Z-index提高元素的优先级；不能设置版心的元素，绝对定位时都要用百分比

+ 绝对定位和浮动都会是元素脱离文档流，宽度会被默认撑开，不会再占据原先的位置，绝对定位时，一般要给其父类设置一个相对定位

+ 文档流：margin、独占一行、块状标签独占一行、行内元素可以同一行显示，如果不够会自动换行、自上而下的展示等这些特性都不起作用

+ background：颜色 URL 平铺 位置；border：宽度 样式 颜色

7. 透明度:background-color:rgba(0,0,0,0.5);opacity:0.5

+ 如果一个a标签里面有一个图片一行文字![a里面有图片和文字]（C:\Users\贾小先生\Desktop\笔记1.jpg）给元素设置一个padding，然后把图片设置背景图片，用背景图片位置，或者给背景图片设置一个div，用绝对定位

* 当把一个元素转换成行内块元素后，和文字对齐，要在行内块元素中设置vertival：middle

* 如果在hover时要改变图片，hover时的权重要大于上面设置图片时的权重



### 经常碰到的一些网页结构模式
+ 注意观察页面中的公共样式，写在统一的css文件中，引用css文件时要注意类名的设置，防止重复，调用权重高设置的样式

+ 头部导航栏：用无序列表，下划线写在li中，宽度为4em

+ 如果鼠标悬停在一个元素上面，图片发生变化，可以把大的图片或者阴影设在最上面的元素上，用背景颜色或者背景图片，父类设置被覆盖的图片

+ 让一个元素里面的内容不蔓延到边框或者padding中，用background-clip：padding-box（在padding和内容区显示）/margin-box（在内容、border、padding中显示）/content-box（只在内容区域显示），设置banner图片上的分页器时就需要
        ```
             .ban .ban-dot .dot-items{
	                      float: left;
	                      width: 10px;
	                      height: 10px;
	                      margin-top: 5px;
	                      margin-left: 5px;
	                      border: 5px solid transparent;
	                      background-clip: padding-box;
	                      border-radius: 50%;
	                      background-color: white;
                         }
        ```



### JavaScript基础知识

+ DOM（document object model）文档对象模型；BOM（browser object model）游览器对象模型

+ 引入：三种引入位置，body/head/外部链接

+ 变量：是一个存储数据的容器，使用必须要先声明，通常设置一个初始值；命名：驼峰命名法，不能使用保留字和关键字（编译时会执行）

+ 基本数据类型：number：NaN一种不能被计算的数值
                string：必须要用引号（单引号和双引号包括起来的都是字符串），单引号里面可以包括双引号，反之不成立；字符串用+，表示字符串之间的拼接，其余运算时是NaN
                boolean：true和false
                undefined：定义了的变量，但是没有设置初始值

+ 复杂数据类型 ：array数组：[1,2,'string',[1,2]]；var arr = []
                  object：var object {
                      key : value,
                      key : value,
                  }
                  faunction函数：function  foo（）{}

+ 比较运算符：语法 表达式1 运算符 表达式2；
              ===严格等于 类型和数值都要相等；
              字符串与number之间的比较`console.log('123'==123)`会把字符串变成number123，再比较  存在隐式转换

+ 算数运算符：+ 如果两个都是number直接运算，如果一个number一个string，则将number转化成string执行拼接 
              —  * /：都会把字符串转换成number再做运算

+ 赋值运算：a +=/a = a+1/a ++/++a，都是a = a+1
            a++和++a：共同：都实现了+1
                      不同：++a返回值是 +1之后的值11；a++返回值是 +1之前的值10
