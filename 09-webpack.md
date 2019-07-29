### entry
> 入口,是src下的任意文件

### output输出
> 输出到的目标文件名
> 打包生成的文件
1. `'bundle.js'`把入口文件打包成`bundle.js`文件
2. `'[name].js'`根据入口文件的名称打包生成`name.js`
3. `'[name].[chunkhash].js'`根据哈希值生成,用来缓存


### 打包css,图片,文字
1. 先安装插件
2. 修改webpack-config.js中的rule


### 管理输出
#### 写多个入口,动态生成多个bundle.js
1. 修改webpack-config.js入口和出口
2. 在index.js中使用
3. 修改index.html中的js引入

#### HtmlWebpackPlugin
> 自动生成`index.html`,不用每次修改引入的js,`webpack`为自动引入修改
1. 安装
2. 在`webpack-config.js`引入

#### CleanWebpackPlugin
> 清理`dist`下多余的生成的`bundle.js`文件
> 中文文档有误
```
const {CleanWebpackPlugin} = require('clean-webpack-plugin');
plugins: [
        new CleanWebpackPlugin(),
        new HtmlWebpackPlugin({
        title: 'Output Management'
        })
    ],
```

### 开发
#### source map
> 在开发时,提示错误代码在哪个文件,第几行
在`webpack-config.js`中`devtool: 'inline-source-map'`

#### 热加载  webpack-dev-server 
每次更改文件都必须从新打包一次，很麻烦 
启用热加载能够帮助我们监听代码的变化自动进行打包代码

### tree shaking (压缩输出) 中文官网是错误的
webpack在打包的时候默认删除文件中未使用的部分。
如 在index.js的同级新建math.js 里面有两个函数  
如果只引入cube  那么在打包的时候square也是会被打包进`bundle.js`的  如果不需要square不想被导入 需要在webpack.config.js里面加入
`mode: 'development'`
```html
<script>
export function square(x) {
    return x * x;
  }
  
  export function cube(x) {
    return x * x * x;
  }
</script>
```