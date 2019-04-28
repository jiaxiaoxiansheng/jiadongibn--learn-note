### HTML与CSS
1. 让鼠标变成小手样式，cursor:pointer。input原本的边框消失outline：none。表单value值：设置默认值和placeholder类似。
2. .让一个元素里面的内容不蔓延到边框或者padding中，用background-clip：padding-box（在padding和内容区显示）/margin-box（在内容、border、padding中显示）/content-box（只在内容区域显示），设置banner图片上的分页器时就需要
        、、、
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
        、、、
. 嵌套崩塌：给子类设置margin-top，但是作用在了父类元素上，解决办法，设置overflow
. 如果背景图片是整个网页，用img元素，width设置100%，背景图片上的样式用绝对定位，数值使用百分比（或者给父类设置绝对定位，子类用margin：0auto）；也可以给元素设置一个Z-index提高元素的优先级；不能设置版心的元素，绝对定位时都要用百分比
. 绝对定位和浮动都会是元素脱离文档流（margin、独占一行、块状标签独占一行、行内元素可以同一行显示，如果不够会自动换行、自上而下的展示等这些特性都不起作用），宽度会被默认撑开
. background：颜色 URL 平铺 位置；border：宽度 样式 颜色
. 透明度:background-color:rgba(0,0,0,0.5);opacity:0.5
. 如果一个a标签里面有一个图片一行文字![a里面有图片和文字]（C:\Users\贾小先生\Desktop\笔记1.jpg）
. 如果鼠标悬停在一个元素上面，图片发生变化，可以把大的图片或者阴影设在最上面的元素上，用背景颜色或者背景图片，父类设置被覆盖的图片
. 当把一个元素转换成行内块元素后，和文字对齐，要在行内块元素中设置vertival：middle
. 如果在hover时要改变图片，hover时的权重要大于上面设置图片时的权重