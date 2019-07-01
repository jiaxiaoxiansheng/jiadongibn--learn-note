###Dom操作
####dom
+ dom:文档对象模型，把HTMl中的一切成为节点，元素节点，注释节点，文本节点（空格和换行)
+ dom是在js中，要注意html中的变量类型在js中转换，字符串？变量

####节点获得
+ ID类名获得，class类名获得和标签类名获得（获得的是数组，要取出节点）

####节点间的获取
+ 节点间获取是属性的形式   节点.xxx
+ 父节点获取：节点.parentNode,一个节点只有一个父节点
+ 兄弟节点、孩子节点存在游览器兼容问题，嫡出能在ie5678上使用（嫡出在ie5678获得的是元素节点，在火狐获得是任何节点），庶出在ie10以及火狐谷歌游览器上使用（庶出在火狐只能获得是元素节点，在ie5678不能使用），解决兼容，`this.previousElementSibling || this previouSibling`
+ 兄弟节点：上一个兄弟节点previoSibling（嫡出），previousElementSibling（庶出），下一个兄弟节点nextSibling，nextElementSibling
+ 孩子节点：第一个孩子节点firstChild/firstElementChild
&emsp;&emsp;&emsp;&emsp;下一个孩子节点nextChild/nextElementChild
&emsp;&emsp;&emsp;&emsp;所有孩子节点childNode(嫡出)，childNode.nodetype=1，也可以只获得子元素节点
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;/children（庶出）

####节点的操作（增删改查）
+ 节点的操作是函数或者方法node.xxx()
+ 创建一个新的节点：document..createElement();创建的新的节点必须插入到网页中，才能显示
+ 插入节点：父节点.append（要插入的节点），同一个节点不能反复插入
&emsp;&emsp;&emsp;&emsp;父节点.insertBefore(要插入的节点，参考节点)，如果参考节点为空，则插入到最后面
+ 删除节点：父节点.removeChild（删除的节点）
+ 复制节点：要复制的节点.cloneNode（true（深层复制）/false（只复制元素节点本身））

####节点的属性操作
+ 节点属性操作，节点.属性（'字符串'），因为类别或者类名在js中都是字符串形式
+ 获取节点在HTML中的类名:节点.getAttribute('要获取类的类别class/ID')
+ 重新设置类名:节点.setAttribute('要设置的类别'，'要设置的类名')，重新设置类名，会替换元素本身的类名
+ 删除类名：节点.removeAttribute('要删除的类别')，只能根据类别删除，不能依据类名

####节点内容操作
+ innerText/content,节点.innerText给节点插入文本内容（代码也是文本显示）
+ innerHtml：节点.innerHtml，插入可执行的标签，标签样式能被解析，用来动态生成网页标签


####案例中问题
+ lock上锁：先声明一个布尔lock，如果想让某个执行，就设置lock为true，否则设为false
+ 需要增加类名时，需要把标签原本的类名和想添加的类名拼接
+ 排他思想:先把所有的全部删除，最后给需要的单独添加
+ 判断字符串中是否有某个字符时，需要把字符串转换成数组判断，字符串'zzzaaa'中也是有aaa的，判断的并不是某个字符串是否是aaa
+ 动态生成ul中的li时，需要的innerHtml是所有的li的字符串
+ 给标签绑定事件时，可以在标签中用属性的方式绑定onclick=function()
+ 在给一个标签设置多个类名，多个css样式时，可以用三元运算符，成立就有多的css，不成立有统一的css

