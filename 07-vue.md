### es6
> forEach,map,filter,some,every,find,findindex区别
  + foreach 遍历数组,不能改变数组元素的值或者属性,没有返回值,不改变原数组
  + map 遍历数组,能给数组中元素添加属性,修改值,返回一个新的函数,不改变原数组
  + filter 遍历数组,筛选数组中符合条件的item,返回新的数组,不改变原数组
  + some 数组中是否有符合条件的元素,返回true和false
  + every 数组中的元素是否都匹配,返回true和false,当数组为空时,返回true
  + find  查找数组中是否有,找到就返回,往下不执行
  + findindex 查找数组中元素对应的下标,找到就返回,


 >``${}模板字面量
   + ``代替字符串中的引号,${}占位符,用作变量

> ...扩展运算符
   1. 用作展开运算符,展开数组
   2. 连接数组,代替cancat
   3. 在数组手部和尾部,可以把不定量的元素表示成...

> export与import
  + export default{}输出自定义模块内的变量,不输出外部就无法获取,可以不写大括号,只能使用一次,只能导出一个对象
    ```
    var user = {
        name: "tom",
        age : 12
    }
    export default user
    ```
  + export 必须使用{},可以向外导出多个成员,import接收时,也必须使用{}变量名字也要相同
  + import xxx from "模块文件目录",获取default输出的变量

> array.from 把一个类数组对象转换成数组  把字符串转换成数组

#### reduce 方法
> 一般用来数组求和乘积,还可以用在数组去重,计算数组中元素出现的次数
  + `array.reduce(function(pre,cut,index,array){},initValue)`function:array数组中每次要执行的回调函数,在函数里面执行,pre是函数返回值或者初始值,cut是当前值,index是当前值下标,initValue自己设定的初始值
  + initValue可以不设,如果不设initValue,从第二个数组开始,pre是第一个元素,cut是第二个元素
   ```
   var arr = [1, 2, 3, 4];
   var sum = arr.reduce(function(prev, cur, index, arr) {
        console.log(prev, cur, index);
        return prev + cur;
    })
    ------打印如下
    1. (1,2,1)
    2. (3,3,2)
    3. (6,4,3)
    只循环三次,因为第一次从`index=1`开始的
   ```  
  + initValue如果为0,则index=0,cut是从第一个元素开始循环
   ```
   var  arr = [1, 2, 3, 4];
    var sum = arr.reduce(function(prev, cur, index, arr) {
        console.log(prev, cur, index);
        return prev + cur;
    }，0) //注意这里设置了初始值0
    ----打印如下
    1. (0,1,0)
    2. (1,2,1)
    3. (3,3,2)
    4. (6,4,3)
    5. (10,5,4)
    循环了四次
   ```


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
  + {className:isActive(true和false)}对象绑定,true的时候绑定,能同时绑定多个className,{className:boolean,className:Boolean}
  + `<div :class=" num <= 10 ? 'on' : 'green'">`,三元运算符绑定
  + `<div style="color:'#ffff'">`颜色必须要用引号包括起来,否则会看成一个vue变量

#### vue使用原生js
> 现在vue中htmlz中传递$event到vue接收中,用e接收

#### 过滤器
> 只能在{{}}插值和v-bind表达式中使用

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
  1. 现在dom中声明一个值:text="text",然后在组件props:['text']中接收这个值,最后在template中调用这个值

> 父组件向子组件中传值
  1. 父组件data中声明一个变量text
  2. 在页面子组件中用属性绑定的形式,绑定这个值:text="text"
  3. 在子组件中prop接受这个值props:['text']
  4. 在template中使用这个值

> 修改父组件传递给子组件的值
  1. 先子组件接受props:['text']
  2. 需要在子组件中声明一个变量来接收要修改的值str = this.text
  2. 修改这个重新声明的变量
> 点击修改父组件传递给子组件的值
  1. 在子组件dom元素绑定的属性后加.sync
  2. 在子组件事件中,用this.$emit("update:属性名",修改的值)

> 点击子组件向父组件传值
  1. 先在js子组件中绑定一个事件,在方法中$emit("方法名",传递的值)
  2. 在html子组件中事件绑定的形式,绑定$emit传过来的方法名(:方法名="父组件的方法名"),值是父组件中的方法
  3. 在父组件中的方法中用一个变量来接收这个值

> 点击实现组件之间通信传值
  1. 声明一个 Vue(bus)实例
  2. 在组件1事件中用bus.$bus("方法名",参数)
  3. 在组件2created函数中bus.on("方法名",参数=>{return  })

###　＄refs
> 父组件获取子组件的变量和方法
1. 在子组件dom中 :ref="xxx"
2. 在父组件中用this.$refs.xxx.子组件中的变量或者方法

#### 声明周期函数
> created(){}
  在组件dom未渲染在页面上的时候调用,不能再函数里面使用dom节点(因为节点还没有渲染)

> mounted(){}
 在组件dom渲染成html后调用,能使用dom节点

 > updated(){}
  在页面更新的时候

#### .sync修饰符
> 用在要传递值的组件dom中,然后在组件中使用`this.$emit("update:属性名",修改的值)`,可以修改传递的值

#### 动态路由
> 所有路由只匹配一种模式,(所有路由的页面结构都一样,在这个结构下,可以根据路由传递的参数,区别是哪个路由,获取不同路由的值),能够传递参数,称为动态路由

1. 创建通用的组件页面,在router路由中引入
2. 在appVue中使用,有几个id,使用几次
3. 在组件页面,根据不同的id获取不同的值

> $route是个当前的路由对象,$router是全局创建的路由实例,

#### query传值
> 动态路由只能传递一个值`'/path/:id',query`可以传递多个值,在都没dom的linkTo中可以直接写`'/path?id=1&name=张三'`(能传递多个值),在页面created可以通过`this.$route.query`获取
> `:to="{name:'path',params:{id:1}}"`,也可以用来传值,不仅是动态路由

#### js操作路由跳转的方式
`this.$router.push('/path')`,`this.$router.push({name:name,params:{id:id}})`,`this.$router.push({name:name.id})`path不能带参数,识别不出来,要在后面直接加上
> 只有name的时候开始不写/
#### 在app.vue中to的写法
> 路径为path
1. `to='/path'`
2. `:to="{name:'path',params:{id:1}}"`(使用这种场景,要传递值,动态路由)
3. `:to="{name:'/path/id'}"`(场景,要传递值(id为传递的值);嵌套子路由:id为子路由路径)

### 路由之间传值
```
js---要传递的值
this.$router.push({
        name: `index`,
        params: {
          page: '1', code: '8989'
        }

js-----接收值
this.page = this.$route.params.page
this.code = this.$route.params.code
```

#### 嵌套路由
> 嵌套路由中的path:不写/,直接写,需要在router.js的routes中的父级路由中写children(是个数组,可以有多个孩子)
```
routes:[
  {
    path:'/',
    component: '/'
    children:[
      {
        path:'/',
        component:'/'
      }
    ]
  }
]
```
> 父级和子级路由在同一个页面显示

#### matched
> 用来面包屑导航

### 路由守卫
> 路由守卫函数中必须执行next(),否则路由不跳转
#### 全局守卫
> 写在main.js中
```
router.beforeEach(to,from,next) => {
  //可以判断路由元信息meta,matched匹配的是路由记录,可能有多个
  if(to.matched.some(ele => ele.meta.xxx == xxx)){
      
  }
  next()
}
```
#### 路由守卫
> 写在router.js需要使用的路由中
```
routes:[
  {
    path:'/'
    component:''
    beforeEnter(to,from,next) => {

    }
  }
]
```
#### 组件守卫
> 写在组件的js中
```
beforeRouteUpdate(to,from,next)=>{
  //在组件被复用时调用
}

beforeRouteLeave(to,from,next)=>{
  //在离开组件页面时调用
  //可以用来提醒用户在离开时,注意保存
}
```

### 滚动行为
> 写在router.js中,和routes:[]平级
```
scrollBehavior(to,from,savePosition){
  return new Promise((resolve,reject) => {
    setTimeout(()=> {
      resolve({x:0,y:0})
    })
  })
}
```

### 路由懒加载
> 当打包构建应用时，JavaScript 包会变得非常大，影响页面加载。如果我们能把不同路由对应的组件分割成不同的代码块，然后当路由被访问的时候才加载对应组件，这样就更加高效了
> 在router.js的routes中component: ()=> import('@/路径')


#### vue中this.$textTick()方法
> 延时执行
使用场景
1. vue改变dom结构后使用this.$textTick()来实现dom数据更新后延迟执行的代码
2. vue声明周期钩子函数created函数中,要改变dom元素必须在this.$textTick()中


### vuex
> store用来存放数组的全局数据库
#### state
> 要存放的数据,能在所有页面通过`this.$store.state`访问到
```
----store.js中
state:{
  age: 18
}

----页面.js中
computed:{
  return this.$store.state
}
```
#### mutations
> 用来修改state中数据,任何地方要修改数据都要通过mutations
1. 在mutations中设置一个方法,来修改数据,方法中有个参数state,就是store中的state
2. 在要修改的页面通过`this.$store.commit('方法名')`来调用这个方法
> mutations直接修改的state的值,所有页面中调用的这个值,也会发生改变,解决办法,在要求的页面,重新赋值给一个变量`this.age = this.$store.state.age`,点击修改这个新的变量`this.age += 5`,其他页面的值不会发生改变
+ mutations里面不能执行异步操作,比如ajax请求或者定时器
+ 在页面中提交mutation方法是可以带有参数`this.$store.state.commit('方法名',val)`
+ 只能有一个形参,如果要提交多个参数,形参可以是对象`{age:10,name:'Bob'}`,store.js中接收参数时,一种接收一个参数val,使用时用`val.age`或者`val.name`,另一种接收一个对象,利用解构赋值(解构赋值名字顺序都必须相同)`{age,name}`

#### action
1. 与mutations相似
2. 能执行异步操作
3. 提交的是mutations中的方法(在action中处理,处理完之后dispatch给mutations,让它去存储)
```
----actions中
//content是一个对象{commit,dispatch,state},也可以用解构赋值形式书写,当只用到commit时,可以只用{commit}来代替content
actions: {
    change(content,val){
      setTimeout(() => {
        content.commit('change',val)
      },1000)
    }
  }

-----页面中
methods:{
  add(){
    this.$store.dispatch('change','Bob')
  }
}
```
4. 调用时传值,和mutations相同,只有一个形参,传递多个值时,要用对象写法


#### getters
> getters方法中是要返回值的 return
> getters调用值,返回值,调用state中数据,在getters中修改并不会改变state中的值,也就不会在其他页面同步改变修改的值
> mutations也可以调用state中的数据,但是要想修改state中的值必须使用mutations,getters不可以
```
---store.js
getters:{
  edit(state){
    //return state.address
    return state.address+'zheng'
  }
}

---页面中
computed:{
  edit(){
    return this.$store.getters.edit
  }
}
```

### vuex辅助函数写法
> 首先引入import{}from 'vuex'
1. mapState
  ```
  ...mapStation({
    age:'age'//第一种,'age'直接找到state中的age变量
    age:state => state.age//第二种
    age(state){
      return state.age + this.str//第三种,这里可以和路由中的属性做操作,这种有this,其它没有,能操作`this.$route`
    }
  })
  ```

2. mapGetters
  ```
  ...mapGetters({
    ages:'age'//'age',这个找到 的是store.js中getters中的方法,ages是自己随意定义的
  })
  ```

3. mapMutations
  ```
  //第一种写法
  ...mutations(['add'])//'add',找到的是mutations中的add,click方法名字也要是这个add `@click='add(val)'`,val是要传递的值
   //第二种写法
   ...mutations({
     adds:'add'//'add'是mutation是中的方法add,adds是自己定义de,也是在`@click='adds(val)'`传值,val是传递的值
   })
   ```

#### vuex辅助函数区别
> 辅助函数(mutations和actions)传值是在dom的`@click='add(val)'`传递;普通的mutations和actions是在js中直接传值`this.$store.commit('add',val)`
> 辅助函数都是函数形式,常规函数操作采用调用属性的形式获取值(this.$store)

### vuex模块化
1. 如果模块中没有使用命名空间,且模块中有相同名字的mutation函数,dom中执行mutation函数,会同步执行所有模块中函数名相同的函数,启明命名空间后,会给mutation是也模块化
2. 模块化,只有state是模块化,mutations,actions,getters都不是模块化
3. 启用命名空间以后,mutation,action写法,要在各自方法前面写上所属模块`this.$store.commit('a/addNum')`,`this.$store.dispatch('a/addNum',val)`
4. getters写法 `this.$store.getters['a/getNum']`
> module后mutation用法
  + `this.$store.commit('a/addNum',val)`a是代表哪个模块

#### 模块化启用命名空间后辅助函数写法
先引入
1. mapState
  ```
  ...mapState(){
    //这一种不能使用,找不到值
    //num:'num'
    num : state => state.$store.a.num
    num(state){
      return state.$store.a.num
    }
  }
  ```
2. mapGetters
  ```
  ...mapGetters({
    //在前面加上所属模块
    getNum:'a/getNum'
  })
  ```
3. mapMutations
  ```
  ...mapMutations({
    //在前面加上所属模块
    addNum:'a/addNum'
  }) 
  ```
4. mapActions
  ```
  ...mapActions({
    //在前面加上所属模块
    changeNum:'a/changeNum'
  })
  ```

### vuex使用module
1. 在main.js同级创建一个store文件,文件中创建一个`index.js`文件
```
import Vue from 'vue'
import Vuex from 'vuex'
import car from './modules/car'

Vue.use(Vuex)

export default new Vuex.Store({
    modules: {
        car,
    }
})
```
2. `index.js`同级创建一个module文件夹,里面是要创建的module.js文件
3. 把`module.js`文件引入到`index.js`中
4. 删除原本的`store.js`文件
5. 修改`main.js`中store的引用,修改了文件位置

#### vuex中mutation和getters使用
1. 如果操作的是vuex中的数据则使用,mutation,getters,actions方法
2. getters不能传值,不是方法,可以让数据随着变化,用在computed中
3. mutation:方法,能传递值,通过某个操作事件来修改vuex的值


### vant插件中的问题
> 替换原有的样式,需要写在`<style lang='scss'>`不能写在带有`scope`中