# html

##### 路径

网络路径

相对路径: (参照物:当前文件)

1. 在同一目录下: 直接引入,带上文件扩展名
2. 上一级目录: ../ (返回上一级目录,然后引入文件)
3. 下一级目录: / (进入到下一级文件,引入文件)



##### 属性

###### a属性

target: "_self"(在当前页面跳转链接)

​			"_blank"(在新标签中打开链接)



##### from表单

###### 标签

form action="" method=""

action: 表单提交地址

method: 表单提交方式

1.get: 地址栏会显示,不安全,容量有限,用于获取信息.	

2.post: 地址栏不会显示信息,相对安全,提交的数据量没有上限,一般用于保存数据.



###### 控件属性

disabled 禁用

readonly 只读

placeholder 占位符提供可描述输入字段预期值的提示信息

autofocus 元素应该自动获得焦点

multiple 多文件上传 

checked 默认选中



# css

##### 特性

层叠性: 设置的所有样式共同作用的效果,样式冲突时,选择器权重高的生效

继承性: 文本相关的一些属性可以继承[](https://www.cnblogs.com/thislbq/p/5882105.html)



##### 属性值单位

em: 基于当前字体的倍数;

%: 通常是相对于父类的百分比;



##### 背景属性

background:  颜色   地址     no-repeat     center;    缩写尽量写在前面,防止样式被覆盖

background-position:   第二个值不写默认center



##### 盒模型

display: none;   隐藏元素,不会占据位置

visibility: hidden;  隐藏元素,依旧占据位置,相当于透明

鼠标悬停可见,只需将不可见标签display为其原本类型



overflow: hidden;  文本溢出部分隐藏

overflow: auto;   根据文本情况,自动添加滚动条

overflow: scroll;  添加两个滚动条



如何让超出盒子的文本显示为...    :

1. width 先指定文本盒子宽度

2. white-space: no wrap;  控制超出文本不换行

3. overflow: hidden;   溢出部分隐藏

4. text-overflow: ellipsis;  溢出部分以...显示

   

span 等设置padding和margin样式,上下不生效,左右生效



嵌套崩塌: 给子盒子设置margin-top,会作用到父盒子上

解决办法: 给父盒子添加 overflow: hidden;给父亲添加border



##### 行内块

当你使用一个 行内块元素撑起块状元素 高度的时候 ,会有一个空白节点

vertical-align:  调整行内和行内块元素垂直对齐方式.



##### 浮动

浮动之后会变成块元素,当一个块级元素浮动以后，宽度会默认被内容撑开,不会继承父类的宽度.所以当漂浮一个块级元素时我们都会为其指定一个宽度

当一个元素浮动以后，其下方的元素会上移。元素中的内容将会围绕在元素的周围。文字环绕效果



浮动的影响:  浮动之后脱离文档流,不能撑起父盒子的高度;  高度崩塌

清除浮动:

1.给父盒子指定宽度

2.给父盒子overflow: hidden;

缺点：内容增多的时候容易造成不会自动换行导致内容被隐藏掉，无法显示要溢出的元素

3.浮动元素后面添加一个空div,给他设置 clear: both

4.单伪元素清除

``` css
 .clearfix:after {
                content:"";
                height:0;
                line-height:0;
                display: block;
                visibility: hidden;
                clear: both;
            }
        .clearfix:after {
                *zoom:1;        针对IE6/IE7
            }
```
原则:要浮动都浮动,



##### 定位

特性:

1.脱离文档流,不再占据位置

2.元素转变为块级元素(除了relative)

3.宽度由内容撑开,不是父类的100%,通常要自己给定



relative: 

1.层级提升,元素特性不改变;宽度不由内容撑开;也不脱离文档流;也不会变成块级元素

2.绝对定位的参照物相对于视口或者是离它最近的祖先定位元素进行定位

3.子绝父相,相对定位没有副作用



sticky:粘性定位



z-index:

1.设置元素堆叠顺序,拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面   

2.元素可拥有负的 z-index 属性值 

3.z-index 仅能在定位元素上奏效

4.z-index写的再大也不会超过父类元素



##### 三角形
``` css
.box {

            width: 0;

			width: 100px;

            height: 100px;

            background-color: red;

            \* 背景色蔓延到 padding 和 border 区域 \*

            background-clip: content-box; \* 规定背景的绘制区域 \*

            border: 100px solid;

            border-color: transparent transparent blue transparent;

            border-bottom-width: 400px;

        }
```
原理: 给盒子设置大的边框,然后让盒子的宽高为0;然后让不需要的边框设置透明



##### 杂类

cursor: pointer; 让鼠标经过盒子时显示小手;

vertical-align:  调整图片相对图片的位置

伪类  :focus  输入框获取焦点

+兄弟选择器 :  选择的是下一个兄弟元素

