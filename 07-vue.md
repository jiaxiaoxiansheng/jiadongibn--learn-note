### es6
> forEach,map,filter,some,every,find,findindex区别
  + foreach 遍历数组,不能改变数组元素的值或者属性,没有返回值
  + map 遍历数组,能给数组中元素添加属性,修改值,返回一个新的函数
  + filter 遍历数组,筛选数组中符合条件的item,返回新的数组
  + some 数组中是否有符合条件的元素,返回true和false
  + every 数组中的元素是否都匹配,返回true和false
  + find  查找数组中是否有,找到就返回,往下不执行
  + findindex 查找数组中元素对应的下标,找到就返回

 >``${}模板字面量
   + ``代替字符串中的引号,${}占位符,用作变量

> ...扩展运算符
   1. 用作展开运算符,展开数组
   2. 连接数组,代替cancat
   3. 在数组手部和尾部,可以把不定量的元素表示成...

> export与import
  + export default{}输出自定义模块内的变量,不输出外部就无法获取
  + import xxx from "模块文件目录",获取default输出的变量

### vue
> computed 计算属性,根据data中的值,变化而变化,如果值没有变化,则不调用,computed是根据缓存绑定的
> methods 方法: data中的值不发生变化,也会调用
调用methods可以传参调用,调用自身methods中的方法this.$options.methods(computed,watch).
> watch: 监听data值发生变化,函数名必须和变量名称相同

> 事件修饰符
   + .stop阻止事件冒泡
   + .prevent阻止默认事件发生
   + .self触发事件元素是当前自身
   + .once点击事件只触发一次

> 表单事件修饰符
   + .lazy当input输入框焦点发生变化时执行
   + .number把数值转化成number
   + .trim去除首尾的空格,中间的不能去除

> class与style绑定
  + {className,isActive(true和false)}对象绑定,true的时候绑定,`<div :class=" num <= 10 ? 'on' : 'green'">`,三元运算符绑定
  + `<div style="color:'#ffff'">`颜色必须要用引号包括起来,否则会看成一个vue变量

#### vue使用原生js
> 现在vue中htmlz中传递$event到vue接收中,用e接收

#### vue组件以及传值
> 声明组件:全局声明,局部声明
> 组件data中的属性,不能在dom中直接使用
  1. 局部声明: 
     ```
     components:{
                "son":{
                    data(){
                        return {
                            text: "这是text文字"
                        }
                    },
                    props:["title"],
                    template:"<div>{{text}}{{title}}</div>"
                }
            }
     ```
   2. 全局声明
     ```
     Vue.component("self-node",{
            template: "<div></div>"
        })
     ```
> prop传值
  1. 现在html中声明一个值,然后在组件prop中接收这个值,最后在template中调用这个值

> 父组件向子组件中传值
  1. 父组件data中声明一个变量
  2. 在页面子组件中用属性绑定的形式,绑定这个值
  3. 在子组件中prop接受这个值
  4. 在template中使用这个值

> 修改父组件传递给子组件的值
  1. 需要在子组件中声明一个变量来接收要修改的值
  2. 修改这个重新声明的变量
> 点击修改父组件传递给子组件的值
  1. 在子组件dom元素绑定的属性后加.sync
  2. 声明一个Vue(bus)实例,在子组件事件中,用bus.$emit("update:属性名",修改的值)

> 点击子组件向父组件传值
  1. 先在js子组件中绑定一个事件,在方法中$emit("方法名",传递的值)
  2. 在html子组件中事件绑定的形式,绑定$emit传过来的方法名,值是父组件中的方法
  3. 在父组件中的方法中用一个变量来接收这个值

> 点击实现组件之间通信传值
  1. 声明一个 Vue(bus)实例
  2. 在组件1事件中用bus.$bus("方法名",参数)
  3. 在组件2created函数中bus.on("方法名",参数=>{return  })


#### 声明周期函数
> created(){}
  在组件dom未渲染在页面上的时候调用,不能再函数里面使用dom节点(因为节点还没有渲染)

> mounted(){}
 在组件dom渲染成html后调用,能使用dom节点

#### .sync修饰符
> 用在要传递值的组件dom中,然后在组件中使用bus.$emit("update:属性名",修改的值),可以修改传递的值
