###闪现,匀速,缓动动画
1. 动画原理:
   + 物体运动:起点,终点,步长(速度)
   + 盒子终点位置:起点 + 步长
2. 三种动画都需要设置定位,才能生效,确定是对谁的定位
3. 闪现动画:直接设置left或者top的值
 `node.style.left = "xxxpx"`
4. 匀速动画:
  + 声明:start,step,cha
        - 起点: 盒子现在left和top的值`box.offsetLeft/Top`
        - 步长: 自己设置(盒子走的速度),要注意正负值,可能是往回走
        - 差值: 终点 - 起点
  + 清除定时器,防止当定时器未执行完时,又执行了定时器,引起冲突      
  + 设置定时器
        - 判断差值和步长
        - 设置清除定时器
  ```
  var timer = null;
  function average(ele,target){
      var start,step,cha;
      clearInterval(timer);
      timer = setInterval(function(){
          step = target > start ? 10 : -10;
          cha = target - start;
          start = ele.offsetLeft;
          if(Math.abs(cha) < Math.abs(step)){
              clearInterval(timer);
              ele.style.left = target + "px";
          }
          ele.style.left = start + step +"px";
      },17)
  } 

  ```
5. 缓动动画
  + 缓动原理:让运动的速度随着距离越近,变得越小
  + 声明:start,step
     - step:(target-start)/10:保证最后距离小于1
  + 清除定时器
  + 设置定时器
     - 判断Math.abs(step)的绝对值是否小于1,在往回走的时候是小于0的
     - 如果小于0,让step向下取整,大于0,向上取整
     - 设置清除定时器的条件
  ```
  var timer = null;
  function average(ele,target){
      var start,step;
      clearInterval(timer);
      timer = setInterval(function(){
          step = (target - start) / 10;
          start = ele.offsetLeft;
          if(Math.abs(step < 1)){
             step = step > 0 ? Math.ceil(step) : Math.floor(step)
          }
          if (step+start === target){
              clearInterval(timer);
              ele.style.left = target + "px";
          }
          ele.style.left = start + step +"px";
      },17)
  }
  ```

###offset家族
> 家族成员: `offsetWidth` `offsetHeight` `offsetLeft` `offsetTop` `offsetParent`
1. `offsetWidth`和`offsetHeight`:获取盒子的宽高 + padding + border
2. `offsetLeft` `offsetTop`:检测距离有定位的父盒子的左/上的距离,如果父级没有定位,则以`body`为准,只读,不能赋值
3. `offsetParent`:检测父系盒子中带有定位的父盒子节点

###事件对象event
获取event的写法 `event || window.event`
`event`可以获取发生在事件中的元素,键盘按键状态,鼠标位置,鼠标按钮的状态
1. `event.target`事件源,兼容写法:`event.target || event.srcElement`;可用来事件委托
2. `event.pageX/Y`:获取鼠标点击的相对于页面的位置(包括scroll的部分)
3. `event.clientX/Y`:获取鼠标点击的相对于可视区域的位置
4. `event.screenX/Y`:获取鼠标点击的相对于屏幕的位置
5. `event.offsetX/Y`表示鼠标指针位置相对于触发事件对象的位置
6. `event.type`	事件的类型

7. `event.button` 鼠标点击的按键(只认识三个键) 可在 `onmousedown` 事件中测试
+ === 0 您点击了鼠标左键
+ === 1 您点击了鼠标中键
+ === 2 您点击了鼠标右键

###事件委托
> 事件原理:通过监听父元素,来给子元素绑定事件(真正触发事件的元素)
> 由于事件的冒泡机制,可以使用事件委托给元素添加事件,多用于ul自动生成的li,然后监听li事件
```
$("ul").onclick = function (e){
				e = event || window.event;
				// 获取目标元素
				var target = e.target || e.srcElement;
				if(target.tagName === "LI"){
					target.style.color = "red";
				}
			}
```

###阻止冒泡
> `event.stopPropagation`:存在兼容
> 兼容写法:`event.stopPropagation ? stopPropagation() : event.cancelBubble = true`

###案例中的问题
1. `ondragstart="return false"`设置img标签中这个属性,可以防止图片被拖拽
2. `onmousedown`鼠标按下的事件
3. `onmousemove`鼠标拖拽的事件
4. `onmouseup`鼠标抬起事件

###`client`家族
> 家族成员`clientWidth` `clientHeight` `clientLeft` `clientTop`

#### `clientWidth` `clientHeight`
+ 检测盒子的宽高:盒子自身的宽高+padding,内容不溢出
+ offsetWidth:盒子自身宽高+padding+border
+ scrollWidth:内容宽高+padding,内容溢出,显示内容宽高
+ document.documentElement.clientWidth  获取游览器可是区域宽高

#### `clientTop` `clientLeft`		只读
> 表示内容区域左上角相对于整个元素左上角的位置   实际上就是border的宽度

### 获取元素样式

> 内嵌样式  行内样式  可通过 `ele.style.styleName`获取
>
> 内联样式和外联样式可通过以下方式获取
```
function getStyle(ele,styleName){
	if(ele.currentStyle){
		return ele.currentStyle[styleName];
	}else{
		return window.getComputedStyle(ele,null)[styleName];
	}
}

```
### 去对象属性,如果该属性是变量,需要用[]的形式获取
```
var abc = "name";
var user = {
	name:'张三',
	age:20
}
console.log(user[abc]);
console.log(user.name)

```

### 在动态生成的标签中添加点击事件

>` pageStr += '<li '+(i==1?'class="active page-items"':'class="page-items"')+' onclick="initPage('+i+',this)">'+i+'</li>'`
+ `(i==1?'class="active page-items"':'class="page-items"')`: 给生成的某个li添加动态样式
+ ` onclick="initPage('+i+',this)"`: 动态添加点击事件,`this`点击的标签