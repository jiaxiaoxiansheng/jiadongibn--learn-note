### JS第二天笔记
+ getTime（）时间戳，获得距离1970年1月1日0时0分的毫秒数，Math.random()取随机数，Math.pow()取几次方
+ 逻辑运算符:且&&：碰到假返回，返回值是布尔值或者操作值  
             &ensp;&ensp;示例：exp1 && exp2  
             &emsp;&emsp;解析： 如果 exp1 能被转换为 false，则返回 exp1；如果exp1 能被转换为   true，则返回 exp2。  
               或||：碰到真返回  
               逻辑或 ||  
             示例：exp1 || exp2  
             解析： 如果 exp1 能被转换为 false，则返回 exp2；如果exp1 能被转换为   true，则返回 exp1。  
+ 数据类型之间的转换，能转换成false的值有null，0，NaN，空字符串（''）undefined
+ if语句（）具有隐式转换，在判断条件时，要注意把数值型字符转换成number类型计算（parseInt，parseFloat）
+ 三元运算符：语法格式：条件？条件成立为true，执行这里的代码：否则执行这里的代码
                 `var a = 3>5?5*3:5*2`输出为10
+ for循环
   ```
      for (var i = 0; i < 100; i++) {
			// var i = 0:声明一个i变量
			// i < 100：循环条件，变量申明之后执行这个条件，如果成立，则执行console.log(i)，不成立则循环结束
			// i++：执行完console.log(i)，执行这个，让数值+1；然后再执行循环条件
			// console.log(i);
		}
		console.log(i);//输出100,判断99小于100，然后执行大括号里面代码，再执行i++；判断100<100，不成立则循环结束
		```