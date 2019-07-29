## node
### node指令
> cls清除命令窗口
### express
+ 通过应用生成器安装
  - npm install express-generator -g
  - express --view=ejs myapp   选择ejs的模板,能直接写html
  - cd myapp 进入文件
  - npm install 安装依赖
  - npm start 运行
### 占位符与值
 + `<%= user.text %>`  `res.render('success',{user});`
 + 值必须写在渲染的页面上
 + routes路由
   - 路由通过get方法拦截请求地址,然后返回对应的模板
    ```
    //'/login'是服务器拦截的url地址
    router.get('/login', function(req, res, next) {
        //'login'服务器要在游览器上渲染的模板
    res.render('login');
    });
    ```
    - 如果网络请求是`post`,需要用`post`方法拦截,要对应
    - `get`方法请求,传递的值在`req.query`中
    - `post`方法,传递的值在`req.body`中
+ 为了防止登录页面,每次刷新页面都`form`提交请求,需要重定向`form`的地址,根据不同的结果渲染不同的模板
+ 登录页面必须是在用户登录后才能进入,用户登录以后,服务器会给用户一个`sessionId`,存在`cookie`中,根据`sessionId`可以判断用户是否已经登录

### 路由
+ 路由地址`/ajax/index`表示查找的是`ajax`路由中内容
+ `/login`是`index`路由中的内容,,由`app.js`中设置,`/`和`ajax`名字只能使用一次