###入口函数

+ `$('document').ready(function(){})`,是DOM结构绘制完毕后就执行,可以编写多个
+ `$(function(){})`

###事件绑定
+ Js:  .onclick = function(){ }:原生js中处理事件都是属性
+ Jquery:   click(function(){  });jquery中处理事件是方法()

###选择器
####基本选择器
####层级选择器
+ '>':所有的子元素(亲儿子)
+ '空格':所有的后代选择器
+ '+':紧挨着的下一个元素
+ '~':后面所有的兄弟元素
####过滤选择器
+ $('node:eq(index)'):选择第index-1匹配的元素
+ $('node:gt(index)'):选择序号大于index的所有元素
+ $('node:lt(index)'):选择序号小于index的所有元素
+ $('node:first'):选择第一个元素
+ $('node:last'):选择最后一个元素
####属性选择器
+ $("node[属性名='属性值']"):选择具有这个属性,并且属性值一样的元素
####筛选选择器
+ 筛选选择器都是方法
+ $('node').eq(index):查找第index-1匹配的元素
+ $('node').children('xx')查找孩子为xx的所有元素
+ $('node').siblings():查找所有兄弟元素,不包括自己
+ $('node').parent('xx'):查找id为xx的父元素,亲的
+ $('node').find('xx'):查找孩子(子子孙孙)为xx的所有元素
+ $('node').next():查找为node的下一个兄弟
+ $('node').nextAll();$('node').nextEnd()
+ $('node').parent():查找node的所有父元素
+ $('node').parentAll();$('node').parentEnd()
+ $('node').prev():查找为node的上一个元素
####属性
+ $('node').attr('class')获取node的class的类名
+ $('node').attr('class','xx')设置node的class类,会覆盖之前的
+ $('node').attr('class')删除node的class类
+ $('node').text()获取node中的text;dom中时innerText
+ $('node').text('xx')设置text
+ $('node').html()获取node中的标签
+ $('node').html('xx')设置node中的html,会被解析,自动生成,原有的标签会被覆盖;dom中innerHtml
+ $('node').val()获取表单中的值
+ $('node').val('xx')设置表单中的值为xx
+ $('node').prop()获取表单的选中状态
+ $('input:checked'):选择表单中被选中的那个表单
####jquery节点操作
+ `var node = $(“#box1”).html（“<li>我是li</li>”）`创建jquery元素
+ append()插入元素,在最后面
+ appendTo(xx)把元素插入到xx中去
+ after(xx)在xx之后插入
+ before(xx)在xx之前插入
+ prepend(xx)在元素xx第一个子元素之前插入

####dom与jQuery相互转换
+ dom--->jQuery:  dom--$(dom)
+ jQuery--->dom: jQuery('node')--->$('node')[0]

####清空
+ $('node').empty()清空里面所有元素,包括文本
+ $('node').html()清空里面的标签
+ $('node').remove()清空所有,包括自己

####动画
+ $('node').show(function(){},时间),展示动画,hide隐藏动画
+ $('node').slideDown()动画滑入;slideUp滑出
+ $('node').fadeIn()动画淡入;fadeOut淡出;fadeTo改变元素透明度
+ $('node').animate(style,function(){})自定义动画:style是执行动画是要改变的css,function动画执行完毕执行的函数

####位置操作
+ $('node').position()获取相对最近的具有相对定位的父元素(left,top)
+ $('node').offset()获取或者设置相对文档的位置(left,top)
+ $('node').scroll(xx)获取或者设置元素垂直方向的滚动位置,
+ $('node').scroll(0):设置屏幕滚动位置为0,就是回到顶部;
+ $('node').scroll():获取现在屏幕滚动到那个位置,屏幕垂直方向上卷进去多少

####on绑定事件
+ $('node').on(事件,data,function(){})
+ $('ul').on('click',function () {})

####事件委托
+ $('ul').on('click','li',function () {}):可以用作事件委托,给ul绑定事件,自动生成的li也会绑定上click事件,(要给具有所有子元素的父元素绑定事件)
+ event.target:当前触发事件的元素,不一定是this,可以获取当前触发事件的对象
```
$('ul').click(function () {
   alert($(event.target));//可以获取当前点击的元素
})
```

####jQuery中event事件
+ event.currentTarget:和this一样,指向dom对象
+ event.target:当前触发事件的元素,不一定是this,可以获取当前触发事件的对象
+ event.stopPropagation()阻止冒泡事件,只让当前元素的事件执行,不让父元素执行
+  $('input').keyup(function(){}),监听键盘,然后执行方法;event.keyCode键盘按键代码;event.type事件类型

####each
+ $('li').each(function (index,ele) {}):遍历所有的li,ele当前正在遍历的li元素,index当前正在遍历的对象下标

####插件使用
+ 先引入依赖库jQuery库,再引入核心库,自己要使用的,如果核心库改变了css,还要引入css库

####案列中的问题
+ 回调函数中的this指向的是当前调用的dom对象,要注意当前函数中的this是否是想使用的this
+ jQuery对象是一个伪数组,具有length属性,并不具有数组的方法,也不能把通过jQuery转dom方式,把jQuery转换成dom数组
+ 设置input的选中状态,要使用prop设置('checked','true')true选中,false未选中,不能通过attr设置checked类

