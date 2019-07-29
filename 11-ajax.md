### ajax
> 异步请求,不用刷新页面,就能完成数据交互,主要用在中后台管理系统,或者数据交互页面
1. 创建对象`var xhr = new XMLHttpRequest()`
2. 设置请求方法和地址`xhr.open(options.type,url)`
3. 监听请求发生变化
   ```
   xhr.onreadystatechange = function () {
        if (xhr.readyState == 4 &&　xhr.status == 200) {
            console.log(xhr.responseText)
        }
    }
    ```
    + `xhr.responseText`是string类型的对象,需要用`JSON.parse()`转化成对象,才能取到里面的值
4. 发送请求 
  + `get`  请求 `xhr.send(null)`
  + `post` 请求 提交的参数是字符串形式,通过contenttype,会转换成对象
         ```
         xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded")
         xhr.send('提交的参数,键值对的形式''name=name')
        ```
> 发送请求和监听是异步执行,顺序没有前后
### 路由接收反应请求
+ 只需要返回数据或者返回成功失败的状态码,不需要跳转渲染页面

### js控制跳转路径
`window.location.href = "/login"`  这个url是跳转的路径,不是渲染的模板

###　jquery的ajax
```
$.ajax({
    url:'',
    type:'',//默认get
    data:$('form').serialize()//参数,对象类型,jquery会解析;`$('form').serialize()`字符串类型,经历过encodeURIComponent()编码了
    //请求发送之前执行的函数
    beforeSend(xhr){
        //可以用来验证表单
    },
    success(res){
        //res是对象,不是原生的ajax的字符串类型对象
    }
})
```
#### 提交form时
+ `$.ajax`会帮我们格式化表单(`input`需要有`name`属性)  `$('form').serialize()`

### 跨域
+ 服务器nginx转发(后端配置)
+ 客户端用webpack配置(前端常用,打完包webpack就不存在了)
+ cors