

# html

##### 路径

网络路径

相对路径: (参照物:当前文件)

1. 在同一目录下: 直接引入,带上文件扩展名
2. 上一级目录: ../ (返回上一级目录,然后引入文件)
3. 下一级目录: / (进入到下一级文件,引入文件)



##### 标签属性

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

checked 默认选中



##### 表格

###### 语法

```html
<table>
	<tr>
		<th>表头内的文字</th>
		...
	</tr>
	<tr>
		<td>单元格内的文字</td>
		...
	</tr>
	...
</table>
```

###### 属性

cellspacing: 设置单元格与单元格边框之间的空白间距

cellpadding: 设置单元格内容与单元格边框之间的空白间距

###### 合并单元格

- rowspan 单元格所占行
- colspan 单元格所占列



##### 表单

###### input控件

![](https://i.loli.net/2019/07/22/5d3565442e57642802.png)

###### label标签

`label` 标签为 `input` 元素定义标注。

作用：用于绑定一个表单元素, 当点击 label 标签的时候, 被绑定的表单元素就会获得输入焦点。

`for` 属性规定 `label` 与哪个表单元素绑定。

```html
<label for="male">男</label> <input type="radio" name="sex" id="male" value="male" />
```

###### 下拉菜单

```html
<select>
	<option>选项1</option>
	<option>选项2</option>
	<option>选项3</option>
</select>
```

- `<select></select>`中至少应包含一对`<option></option>`。
- 在 `<option></option>` 中定义 `selected="selected"`属性时，当前项即为默认选中项。可以简写为`selected`

###### 补充属性

- `<fieldset>` `<legend>` 可以实现表单的分组。
- multiple 多文件上传 

##### 语法规范

- 注释不能嵌套
- 标签必须完整
- 标签可以嵌套，但要注意语义。
- 标签的属性必须加双引号
- 标签属性尽量使用小写



# css

##### 选择器

+兄弟选择器 :  选择的是下一个兄弟元素

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



span 等设置padding和margin样式,上下不生效,左右生效



嵌套崩塌: 给子盒子设置margin-top,会作用到父盒子上

解决办法: 给父盒子添加 overflow: hidden;给父亲添加border



###### 超出盒子文本显示为...    :

1. width 先指定文本盒子宽度

2. white-space: nowrap;  控制超出文本不换行

3. overflow: hidden;   溢出部分隐藏

4. text-overflow: ellipsis;  溢出部分以...显示

   

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
                *zoom:1;   针对IE6/IE7
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



##### 水平垂直居中

水平居中:

1. 行内块元素: 给父类设置text-align: center;
2. 块级元素: margin: 0 auto;

块级元素垂直居中:

1. 盒子宽高确定

```css
.box {
    	position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -25px;
        margin-top: -25px;
        width: 50px;
        height: 50px;
        }
```
```css
.box {
    	width: 100px;
        height: 100px;
        position: absolute;
        left: 0;
        top: 0;
        bottom: 0;
        right: 0;
        margin: auto;
        }
```



 2. 盒子宽高不定

```css
.box {
    	position: absolute;
        left: 50%;
    	top: 50%; 
        transform: translate(-50%, -50%);         
        background-color: green;
        } 
```



# git

![](https://user-gold-cdn.xitu.io/2019/1/23/168766ec478de231?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

##### 配置

- 已经配置的列表信息

  git config --list

- 配置用户名

  git config --global user.name "用户名"

- 配置邮箱

  git config --global user. email 邮箱地址



##### 上传笔记

- 打开要上传的文件夹,右键 git bash here
- git init (初始化本地仓库){只用做第一次}
- git add . (将所有文件添加到暂存区)
- git commit -m'提交信息' (将暂存区内容提交到本地仓库)
- git remote add origin [URL]{只用做第一次}
- git push origin master



# md语法

注意: 每个标记和文字之间要用空格隔开

##### 标题

#一级标题;###三级标题

##### 段落换行

在上一行结尾插入两个以上的空格后再回车

##### 引入```

```

```

##### 表格

| 属性      |     属性值 |     补充     |

| :-------- | ---------: | :----------: |

| font-size | 20000000px | 字号|

| font-size |       20px |     字号     |

| font-size |       20px |     字号     |

| font-size |       20px |     字号     |

**: 表示对齐方式**



##### 字体样式

_斜体_  : __

**加粗**  : ****

~~删除~~  : ~~~~



##### 超链接

[百度]~~没有空格~~(https://www.baidu.com/)

##### 图片

![图片丢失显示]~~没有空格~~(网络路径)

##### 行内代码

`html`



##### 列表

+-*后面加空格

列表嵌套只需缩进一个tab

# H5

##### 语义化标签

header; nav; section;  article; aside; footer

[HTML5元素周期表](http://www.html5star.com/manual/html5label-meaning/)

##### 多媒体标签

```html
<video src="" width="400" muted height="400" controls autoplay></video>
<!-- autoplay 自动播放
	controls 是否显示默认播放控件
	loop 循环播放
	preload 预加载，同时设置了autoplay，此属性将失效
	width 设置播放窗口宽度
    height 设置播放窗口的高度 
    muted 开启静音  视频自动播放就可以生效 -->

<audio src="" loop autoplay controls></audio>
```

##### 多浏览器兼容解决方案

```html
	<audio>
        <source src="song.mp3">
        <source src="song.wav">
        <source src="song.ogg">
    </audio>

    <video controls>
        <source src="movie.ogg">
        <source src="movie.mp4">
        <source src="movie.webm">
        您的浏览器不支持
    </video>
```

##### 新增input标签type

- `email` 限制用户输入必须为Email类型
- `tel` 手机号码
- `url` 限制用户输入必须为URL类型
- `number` 只能输入数字
- `search` 具有搜索意义的表单属性
- `range` 范围 滑动条
- `color` 拾色器
- `time` 时间
- `date` 选取日、月、年
- `datetime` 选取时间、日、月、年（UTC 时间）(移动支持)
- `datetime-local` 选取时间、日、月、年（本地时间）
- `month` 选取月、年
- `week` 选取周和年

##### 新增form表单元素

- `datalist` 数据列表 自动补全，常与`input`标签配合使用

实际开发中：需要自动补全的内容列表项可能很多，不可能挨个展示在页面中，一般是通过ajax局部页面刷新技术实现的。

```html
<input type=”text” list=”data”>
	<datalist id=”data”>
	<option>男</option>
	<option>女</option>
	<option>??</option> 
</datalist>
```

- `meter` 用来表示规定范围内的数量值，必须有已知范围

```html
<meter value="81" min="0" max="100" low="60" high="80"></meter>
```

- `progress` 进度条

```html
<progress value="22" max="100"></progress>
```

##### 新增表单属性

- `autofocus` 获取焦点
- `autocomplete` 自动完成，用于表单元素，也可用于表单自身(on/off)
- `form` 指定表单项属于哪个form，处理复杂表单时会需要 一般一个页面只有一个form
- `novalidate` 关闭验证，可用于form标签
- `required` 必填项
- `pattern` 正则表达式 验证表单
- `autocomplete` 是否保存用户输入值 默认为on，关闭提示选择off
- `formaction` 主要应用于表单内某元素提交地址与整个表单提交地址不同，进行单个地址覆盖 如：`<input type="submit" formaction="xxx.action">`

##### CSS兼容问题

```HTML
<!--[if gte IE 7]> <link rel="stylesheet" href="ie10.css"> <![endif]-->
<!--[if lte IE 8]> <script src="html5shiv.min.js"></script> <![endif]-->
```

##### web标签语义化

标签语义化的目的在于能够直观的认识标签和属性的用途和作用

好处：

- 使页面的内容结构化：结构更清晰，便于不同的屏幕设备解析；

- 有利于SEO：和搜索引擎建立良好的关系，有助于爬虫更多的有效信息；

- 便于团队开发和维护；



# CSS3

#### 私有化前缀

Chrome/IOS/safari:  -webkit-

Firefox:  -moz-

IE:  -ms-

Opera:  -o-

`Autoprefixer`插件

#### 选择器

##### 属性选择器

- `E[attr]` 选择包含attr属性的所有元素
- `E[attr=mydemo]` 选择属性attr的值等于mydemo字符的所有元素
- `E[attr*=mydemo]` 选择属性attr的值任意位置包含mydemo字符的所有元素
- `E[attr^=mydemo]` 选择属性attr的值开始位置包含mydemo字符的所有元素
- `E[attr$=mydemo]` 选择属性attr的值结束位置包含mydemo字符的所有元素



##### 伪类选择器

```css
a:link{} 		/*链接状态*/
a:active{}		/*点击时状态*/
a:visited{}		/*访问过状态*/
:checked		/*被选中状态*/
:focus			/*被聚焦状态*/
```



###### 结构伪类

- `E:first-child` 第一个子元素
- `E:last-child` 最后一个子元素
- `E:nth-child(n)` 第n个子元素
- `E:nth-last-child(n)` 同E:nth-child(n) 相似，只是倒着计算
- n是支持简单表达式的 (2n/even表示偶数;2n+1/odd表示基数/ -1n+x表示前x个属性)
- **注意: n 是从1开始的自然数 E:nth-child(0) 无效**
- **E:empty** 选中没有任何子节点的E元素；注意，无法选择有空格或者回撤的标签



###### 目标伪类

```html
<style>
  	li:target{
  		font-size: 30px;
  		color: blue;
  	}
  <style>
  <body>
  	<a href="#li3">点我</a> <!-- 点击a链接,链接跳转到li3的时候，li3的文字会显示为蓝色 -->
  	<li id="li3">li3</li>
  </body>
```

###### 伪元素

- `E::before`、`E::after` 默认行内元素 `content` 属性必须写
- `E::first-letter`文本的第一个字母或字
- `E::first-line` 文本第一行
- `E::selection` 被选中的文本



#### 透明

关于透明度：

1. opacity只能针对整个盒子设置透明度，子盒子及内容会继承父盒子的透明度
2. transparent 不可调节透明度，始终完全透明

一般元素透明使用 opacity, 制作制作遮罩层常用 rgba, 制作三角形常用  transparent



#### 阴影

##### 文本阴影

```css
text-shadow: h-shadow(x) v-shadow(y) blur(模糊半径) color(颜色)
```



##### 盒子阴影

```css
box-shadow: h-shadow(x) v-shadow(y) blur(模糊半径) spread(扩展范围,可省略) color(颜色) inset(是否内嵌,可省略)
```



#### 盒模型

- `content-box`: 对象的实际宽度等于设置的 width 值和 border、padding 之和 (默认方式)
- `border-box`： 对象的实际宽度就等于设置的 width 值，即使定义有 border 和 padding 也不会改变对象的实际宽度，即 ( Element width = width ),我们把这种方式叫做 css3 盒模型



#### 渐变

##### 线性渐变linear

```css
/*带to标准语法:*/     
background: linear-gradient(to bottom, red, yellow);
/*添加私有化前缀*/
background: -webkit-linear-gradient(top, red, yellow);
/*这两句代码表现效果相同*/
```

###### 使用角度

left	top	right	bottom

两两可以结合使用

###### 颜色百分比

```css
background: linear-gradient(to right, red 20%, yellow 60%)
/*前20%为第一个色值;60%以后用最后一个色值;百分比中间是渐变色*/
```

###### 重复渐变

```css
background: repeating-linear-gradient(to right, red 10%, green 20%);
/*渐变平均分配*/
```



##### 径向渐变radial

```css
/*radial-gradient径向渐变指从一个中心点开始沿着四周产生渐变效果*/
background: radial-gradient(circle at/*指定中心位置*/, shape size, start-color, ..., last-color);
```



#### 背景

##### background-size

设置背景图片的尺寸;`width`,`height`可以直接设置宽高,百分比;但是会拉伸图片

`cover`会自动调整缩放比例，保证图片始终填充满背景区域，如有溢出部分则会被隐藏。整个背景图片完整显示在背景区域.

`contain`会自动调整缩放比例，保证图片始终完整显示在背景区域。但是会有留白.

##### background-clip

设置背景区域裁剪

`border-box` 裁切边框以内为背景区域；_默认是裁剪边框_

`padding-box` 裁切内边距以内为背景区域；

`content-box` 裁切内容区做为背景区域；

##### background-origin

设置背景放置的起点

`border-box` 以边框做为参考原点；

`padding-box` 以内边距做为参考原点；_默认是padding-box_

`content-box` 以内容区做为参考点；



#### 过渡

##### transition

- `transition-property` 设置过渡属性,一般为all;

- `transition-duration` 定义过渡效果花费的时间;
- `transition-timing-function` 规定过渡效果的时间曲线。默认是 "ease";
- `transition-delay` 规定过渡效果何时开始;

```css
transition-timing-function: linear|ease|ease-in|ease-out|ease-in-out|cubic-
bezier(n,n,n,n);

/*简写:*/ transition: all 0.4s ease 1s/*过渡延时写在最后*/;
```



##### 2D变换(transform)

```css
transform: translateX(20px) translateY(10px);
/* 等同于上边的写法 */
transform: translate(20px, 10px);
/* 旋转 */
transform: rotate(45deg);
/* 缩放 */
transform: scale(0.8);
/* 拉伸 */
transform: skew(45deg, 30deg);
/* 同时实现位移,旋转,放大等,需要把他们写在一个transform里边 */
transform: translate(30px, 40px) rotate(135deg) scale(1.2);


transform-origin:/*更改元素变形的原点*/
```



#### 3D变换

##### 透视（perspective）

写法:

- 作为一个属性，设置给父元素，作用于所有3D转换的子元素(通常用这种写法)
- 作为transform属性的一个值，做用于元素自身

透视会产生“近大远小”的效果

通常和`transform-style: preserve-3d;`(开启3D舞台) 搭配使用



##### 3D呈现

设置内嵌的元素在 3D 空间呈现必须转换元素:

flat：所有子元素在 2D 平面呈现

preserve-3d：保留3D空间

3D元素构建是指某个图形是由多个元素构成的，可以给这些元素的父元素设置transform-style: preserve-3d来使其变成一个真正的3D图形。

##### backface-visibility

`backface-visibility: visible/ hidden`

设置元素背面是否可见



# JS

```javascript
//输出语句
console.log(); //在控制台打印信息
alert(); //弹出窗,不点确定会阻塞后面代码运行
prompt(); // 用户输入信息
document.write(); //在页面中写入信息
```

### 变量

#### 注意

变量必须先声明,再使用

```javascript
// 此时 b 不加引号,会被当做变量来解析,加上引号'b'被当做字符串解析
console.log(b); // 报错b is not defined 变量没有定义
```



#### 命名规则

1. 变量命名必须以字母或是下标符号”_”或者”$”为开头
2. 不能以数字开头
3. 严格区分大小写
4. 不能是 js 中的关键字和保留字
5. 建议用驼峰命名规则：getElement
6. 语义化,见名知意



### 数据类型

#### 基本数据类型

##### string字符串

```javascript
//字符串类型 用引号引起来  引号不能嵌套(单引号里边不能嵌套单引号)
//var str = '你好'你好'你好'; 错误示范

//转义字符
// \" 表示 ";  \' 表示 ';  \n 表示换行;  \r 表示回车;  \t 表示制表符;   \\ 表示\
console.log('你\\好'); //输出   你\好
```



##### number类型

###### 取值范围

- 最大值  `Number.MAX_VALUE`
- 最小值  `Number.MIN_VALUE`

如果取值超过了这个范围,则会返回infinity

- 无穷大（正无穷）：Infinity
- 无穷小（负无穷）：-Infinity

`typeof infinity` 的返回值是 number



###### NaN和isNaN()

`NaN`是一个特殊的数字 (表示not a number)

**注意** `typeof NaN` 的返回值是number,   说明`NaN`虽然没有数值,  但是它的数值类型还是number

undefined 和任何数值计算的结果为 `NaN`。`NaN` 与任何值都不相等，包括 `NaN` 本身。



`isNaN()` 用来判断括号里的值是不是 `NaN` 

```javascript
//任何不能被转换为数值的值，都会让这个函数返回 true
isNaN(NaN); // true
isNaN("blue"); // true
isNaN(123); // false
```



###### 浮点数

浮点数的运算是一个不精确的结果,不要用浮点数直接计算值



##### Boolean类型

true 和 false。主要用来做逻辑判断。



##### undefined类型

**声明**了一个变量，但是没有**赋值**（例如：`var a;`），此时它的值就是 undefined。

- Undefined 类型的值只有一个，就是 undefined
- 使用 `typeof`  检查一个 undefined 时，会返回 undefined



##### null类型

专门用来表示一个为空的对象（例如：`var a = null`）。注意，专门用来表示_空对象_。

null 类型的值只有一个，就是 null



##### 方法typeof()

获取变量的类型,返回小写

返回结果

- `typeof 数值` 的返回结果：number
- `typeof 字符串` 的返回结果：string
- `typeof 布尔型` 的返回结果：boolean
- `typeof undefined` 的返回结果：undefined
- `typeof null` 的返回结果：object



#### 引用(复杂)数据类型

##### 数组

```javascript
//表示一组数据,每一个元素可以是其他任意的数据类型
var arr = [1, 2, 3];
```



##### object对象

```javascript
//对象是一组由键-值组成的无序集合; 用来描述一个具体的,独一无二事物
var user = {
    name: '',
    age: 18,
    sex: '',
    skills: [],
    speak: function(){
        
    },
}
```



##### 函数

```javascript
function 函数名(形参1,形参2...){
    函数体
}
函数名(实参1,实参2...);//函数不调用,不执行
```



#### 类型转换

##### -->string

###### 1.拼接字符串

```javascript
var a = 123;
var b;
console.log(a + '');  //string类型的123
console.log(b + 'abc'); //undefined
```

###### 2.tostring()方法

```javascript
var a = 123;
var b = true;
var c;
console.log(a.toString()); // 123
console.log(b.toString()); // true
console.log(c.toString()); //报错

//注意：null 和 undefined 这两个值没有 toString()方法，所以它们不能用方法二。如果调用，会报错。
```

###### 3.使用string()函数

**_JS当中会执行的隐式转换方法_**

```javascript
var a;
console.log(String(123)); // '123'
console.log(String(true)); // 'true'
console.log(String(a)); // 'undefined'
console.log(String(null)); // 'null'
```



##### -->Boolean

使用Boolean()函数,将其他类型转换为布尔类型(隐式转换规则)

哪些情况会输出为false:

- ''  (空字符串)
- `NaN`
- undefined
- 0
- null



##### -->number

Number()函数 隐式转换采用此规则

```javascript
//string-->number
// 1. 如果字符串中是纯数字， 则直接将其转换为数字。
// 2. 如果字符串中有非数字的内容，则转换为 NaN。（ 此处可以看到 Number() 函数的局限性）
// 3. 如果字符串是一个空串或者是一个全是空格的字符串，则转换为 0。
console.log(Number('    ')); // 0
console.log(Number('  123')); // 123
console.log(Number('12  3')); // NaN
console.log(Number('你好')); // NaN

//undefined-->number
var a;
console.log(Number(a)); // NaN
```

###### parseInt()方法

parseInt()的作用是将字符串中的有效的整数内容转为数字。

```javascript
//1.只保留字符串开头的有效数字,后面的内容消失
console.log(parseInt("2019吃炸鸡"));  //打印结果：2019
console.log(parseInt("2019.11吃炸鸡"));  //打印结果仍是：2019（说明只会取整数）
console.log(parseInt("wo2019.11吃炸鸡"));  //打印结果：NaN

//如果对非string使用parseInt()或parseFloat()，它会先将其转换为 String然后再操作
console.log(parseInt(true)); // NaN
```

###### parseFloat()方法

parseFloat()的作用是：将字符串转换为浮点数。

```javascript
// 遇到 第二个小数点 也会停止
var a = "123.456.7px";
console.log(parseFloat(a)); // 打印结果：123.456
console.log(Number('100px')); // NaN
```



#### 算术运算符

![](https://i.loli.net/2019/07/02/5d1aafbcdb71f45710.png)



1. 当对非 Number 类型的值进行运算（包括`+`、`-`、`*`、`/`）时，会将这些值转换为 Number 然后再运算。

   ```javascript
   console.log(true + 1); // 2
   console.log(1 + null); // 1
   console.log(100 - '1'); // 99
   ```

2. 任何值和 `NaN` 做运算的结果都是 `NaN`。

3. 任何的值和字符串做加法运算，都会先**转换为字符串**，然后再做拼串操作。

   ```javascript
   console.log('1' + 2); //12
   console.log(1 + 2 + '1'); //31 从左往右执行
   ```

4. 任何值做-、\*、/运算时都会自动转换为 Number

   我们可以利用这一特点，为一个值`-0`、`*1`、`/1`来将其转换为 Number。原理和 Number()函数一样，使用起来更加简单。



#### 赋值运算符

`a = a + 2;`等同于 `a += 2;`



#### 自增和自减

两种: `++i`, `i++`

区别:（也就是说，表达式的值不同)

- `a++`的值等于原变量的值（a 自增前的值）
- `++a`的值等于新值 （a 自增后的值）



#### 比较运算符

```javascript
//通过比较运算符可以比较两个值之间的大小关系，如果关系成立它会返回 true，如果关系不成立则返回 false。
//1.对于非数值进行比较时，会将其转换为数字然后再比较。
console.log(true > 0); // 1>0 true
console.log(1 > '100'); // 1>100 false

//2.特殊情况：如果符号两侧的值都是字符串时，不会将其转换为数字进行比较。比较两个字符串时，比较的是字符串的Unicode 编码。【非常重要，这里是个大坑】因此：当我们在比较两个字符串型的数字时，一定一定要先转型，比如 parseInt()。
console.log('12' > '2'); // false 49>50

//3.任何值和 NaN 做任何比较都是 false。
```



```javascript
// ==这个符号并不严谨，会将不同类型的东西，转为相同类型进行比较（大部分情况下，都是转换为数字）
console.log("6" == 6); // 打印结果：true。这里的字符串"6"会先转换为数字6，然后再进行比较
console.log(true == "1"); // 打印结果：true

//undefined 衍生自 null，所以这两个值做相等判断时，会返回 true。
console.log(undefined == null); //打印结果：true。

//NaN 不和任何值相等，包括他本身。
console.log(NaN == NaN); //false


//如果要保证完全等于，我们就要用三个等号===。全等不会做类型转换。
```



#### Math对象

Math 和其他的对象不同，它不是一个构造函数，不需要创建对象。

| 方法              | 描述                                                         |
| :---------------- | :----------------------------------------------------------- |
| Math.abs()        | 返回绝对值                                                   |
| Math.floor()      | **向下取整**（向小取）               Math.floor(-2.6)的值为-3 |
| Math.ceil()       | **向上取整**（向大取）                                       |
| Math.round()      | 四舍五入取整（正数四舍五入，***负数五舍六入**）              |
| Math.random()     | 生成 0-1 之间的随机数               **[0,1)**                |
| Math.max(x, y, z) | 返回多个数中的最大值                                         |
| Math.min(x, y, z) | 返回多个数中的最小值                                         |
| Math.pow(x,y)     | 返回 x 的 y 次幂                                             |
| Math.sqrt()       | 对一个数进行开方运算                                         |

```javascript
//四舍五入取整
console.log(Math.round(2.499999999999999999999999999)); // 3
console.log(2.499999999999999999999999999 === 2.5); // true

//随机 5-10 范围的整数
//[0,6)  向下取整   [0,5]
console.log(Math.floor(Math.random() * 6) + 5);

//求任意范围内的随机数 x-y
console.log(Math.floor(Math.random() * (y-x+1)) + x);
```



#### Date对象

##### 创建

Date对象是js内置对象, 是一个构造函数, 首字母大写, 用来造(创建)对象

构造函数创建对象需要用 `new` 这个关键词:

写法一: `var date = new Date();`  (获取当前的时间对象)

写法二: 在参数中传递一个表示时间的字符串（兼容性最强） 

 `var date = new Date("2017/09/06 09:00:00");`



##### 方法

- `getDate()` **获取日 1-31**
- `getDay()` **获取星期 0-6**（0 代表周日，1 代表周一）
- `getMonth()` 获取月 0-11    **(0 代表一月）**
- `getFullYear()` 获取年份
- `getHours()` 获取小时 0-23
- `getMinutes()` 获取分钟 0-59
- `getSeconds()` 获取秒 0-59
- `getMilliseconds()` 获取毫秒 （1s = 1000ms）



##### 时间戳

`getTime()` 获取当前日期对象的时间戳

**时间戳**：指的是从格林威治标准时间的`1970年1月1日，0时0分0秒`到当前日期所花费的**毫秒数**（1 秒 = 1000 毫秒）。



#### 逻辑运算符

逻辑运算符有三个：

- `&&` 与（且）：两个都为真，结果才为真。
- `||` 或：只要有一个是真，结果就是真。
- `!` 非：对一个布尔值进行取反。

**注意:**

1. JS 中的`&&`属于**短路**的与，如果第一个值为 false，则不会看第二个值。

```javascript
//第一个值为true，会检查第二个值
true && alert("看我出不出来！！"); // 可以弹出 alert 框

//第一个值为false，不会检查第二个值
false && alert("看我出不出来！！"); // 不会弹出 alert 框
```

2. S 中的`||`属于**短路**的或，如果第一个值为 true，则不会看第二个值。

```javascript
//第一个值为false，会检查第二个值
false && alert("看我出不出来！！"); // 会弹出 alert 框
```

3. **非布尔值的与或运算**

```javascript
//非布尔值进行与或运算时，会先将其转换为布尔值，然后再运算，但返回结果是原值
var result = 5 && 6; // 运算过程：true && true;
console.log("result：" + result); // 打印结果：6（也就是说最后面的那个值。）
```

**与运算**的返回结果：（以两个非布尔值的运算为例）遇到`false` 就返回值

- 如果第一个值为 true，则必然返回第二个值（所以说，如果所有的值都为 true，则返回的是最后一个值）
- 如果第一个值为 false，则直接返回第一个值

**或运算**的返回结果：（以两个非布尔值的运算为例）遇到`true` 就返回

- 如果第一个值为 true，则直接返回第一个值
- 如果第一个值为 false，则返回第二个值



#### if语句

##### 条件判断语句

```javascript
if (条件表达式) {
	// 条件为真时，做的事情
}

//注意  if 后边的 括号 具备隐式转换的功能(转换为布尔值)
```

##### 条件分支语句

```javascript
//格式一
if (条件表达式) {
	// 条件为真时，做的事情
} else {
	// 条件为假时，做的事情
}

//格式二
if (条件表达式1) {
	// 条件1为真时，做的事情
} else if (条件表达式2) {
	// 条件1不满足，条件2满足时，做的事情
} else if (条件表达式3) {
	// 条件1、2不满足，条件3满足时，做的事情
} else {
	// 条件1、2、3都不满足时，做的事情
}
```



#### 三元运算符

```javascript
//语法
表达式    ?  如果表达式结果为 true 执行这里的代码   :  如果表达式结果为 false 执行冒号后面的代码;

//可以理解为 if else 的另一种写法
```



#### switch语句

switch 语句也叫条件分支语句。

```javascript
switch(表达式) {
    case 值1：
            语句体1;
        break;

    case 值2：
        语句体2;
        break;

    ...
    ...

    default：
        语句体 n+1;
        break;
}
```



#### for循环

```javascript
for(初始化表达式; 条件表达式; 更新表达式(步长)){
    语句...
}
```



#### while循环语句

##### while

```javascript
// 遍历 1-10;
var i = 1;
while (i <= 10) {
    console.log(i);
	i++;
}
```



##### do...while

```javascript
var i = 1;
do {
    console.log(i);
	i++;
} while (i <= 10)
```



##### 区别

这两个语句的功能类似，不同的是：

- while 是先判断后执行，而 do...while 是先执行后判断。

也就是说，do...while 可以保证循环体至少执行一次，而 while 不能。



#### break和continue

##### break

break 可以用来退出 switch 语句或**整个**循环语句（循环语句包括 for、while）

```javascript
 // 1---9999 中找到一个 被3 整除的数 打印出来
        for (var i = 1; i <= 9999; i++) {
            if (i % 3 === 0) {
                console.log('找到了', i);
                // 因为只需要找到一个 
                // 找到之后 ,需要让循环停止
                break;
            }
        }
```



##### continue

continue 可以用来跳过**当次**循环。

```javascript
 // 只打印 偶数
        for (var i = 1; i <= 10; i++) {
            if (i % 2 === 1) {
                continue;
            }
            console.log(i);
        }
```





#### 数组

`var arr = new Array();`

如果**参数为空**，则表示创建一个空数组；参数位置是**一个数值**时，表示数组长度；参数位置是**多个数值**时，表示数组中的元素。



##### push()

`push()`：向数组的**最后面**插入一个或多个元素，返回结果为**该数组新的长度**。

```javascript
var arr = [24, 12, 34];	
var b = arr.push(1);
console.log(b); //  push完之后  数组的长度 4
```



##### pop()

`pop()`：删除数组中的**最后一个**元素，返回结果为**被删除的元素**。 修改了原数组



##### shift()

`shift()`：删除数组中的**第一个**元素，返回结果为**被删除的元素**。修改了原数组



##### unshift()

`unshift()`：在数组**最前面**插入一个或多个元素，返回结果为**该数组新的长度**。插入元素后，其他元素的索引会依次调整。



##### concat()

`concat()`：连接两个或多个数组，返回结果为**新的数组**。（不会改变原数组）

```javascript
var nameArr1 = ["张三", "李四"];
var nameArr2 = ["王五", "赵六"];
var nameArr = nameArr1.concat(nameArr2);
console.log(nameArr); // ['张三','李四','王五','赵六']
console.log(nameArr1); // ['张三','李四']
console.log(nameArr2); // ['王五','赵六']
// 并未改变原数组，所以我要用一个新数组nameArr去接收合并后的数组，以便后续使用。
```



##### join()

`join()`：将数组转换为字符串，返回结果为**转换后的字符串**（不会改变原来的数组）。

补充：`join()`方法可以指定一个**字符串**作为参数，这个字符串将会成为数组中元素的**连接符**；如果不指定连接符，则默认使用 `,` 作为连接符

```javascript
var arr = [1, 2, 3];
var arrStr = arr.join("-");
console.log(arrStr); // 1-2-3
console.log(arr); // [1,2,3]
// 并未改变原数组
```



##### split()

`split()`：通过指定分隔符，如果省略，默认以逗号分隔，将字符串分割为字符串数组。

```javascript
var email = "abc@163.com;cc@126.com;frg@qq.com";
var emailArr = email.split(";");
console.log(emailArr); // ["abc@163.com", "cc@126.com", "frg@qq.com"]
var emailArr2 = email.split(";", 2);
var emailArr = email.split(";"); // ["abc@163.com", "cc@126.com"]
```



#### 数组排序

##### 冒泡排序

```javascript
var arr = [32, 41, 1, 40, 12, 5];
// 需要几个轮次 6个数排序 最大需要5轮
// 外层循环控制轮次
for (var i = 1; i < arr.length; i++) {
	for (var j = 0; j < arr.length - i; j++) {
		// 经过这样for循环,我们能找到本轮最大的数,并排在本轮尾部
		if (arr[j] > arr[j + 1]) {
			// 交换位置
			var temp = arr[j];
			arr[j] = arr[j + 1];
			arr[j + 1] = temp;
		}
	}
}
console.log(arr); // [1, 5, 12, 32, 40, 41]
```



##### 选择排序

选择排序是一种简单直观的排序算法。它的工作原理是每一次从待排序的数据元素中选出最小（或最大）的一个元素，存放在序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到全部待排序的数据元素排完。 选择排序是不稳定的排序方法。

```javascript
// 问题的关键,就是从 待排序的元素中如何找到最小值,放在起始位置
for (var i = 0; i < arr.length - 1; i++) {
	var minIndex = i;
	for (var j = i + 1; j < arr.length; j++) {
		if (arr[minIndex] > arr[j]) {
			minIndex = j;
		}
	}
	if (minIndex !== i) {
		// 交换位置
		var temp = arr[i];
		arr[i] = arr[minIndex];
		arr[minIndex] = temp;
	}
}
console.log(arr);
```



##### 插入排序

它的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。

插入排序的算法步骤如下：

- 从第一个元素开始，该元素可以认为已经被排序；
- 取出下一个元素，在已经排序的元素序列中从后向前扫描；
- 如果该元素（已排序）大于新元素，将该元素移到下一位置；
- 重复步骤 3，直到找到已排序的元素小于或者等于新元素的位置；
- 将新元素插入到该位置后；
- 重复步骤 2~5。

```javascript
var len = arr.length;
var j, temp;
for (var i = 1; i < len; i++) {
	j = i - 1;
	temp = arr[i];
	while (j >= 0 && arr[j] > temp) {
		arr[j + 1] = arr[j];
		j--;
	}
	arr[j + 1] = temp;
}
```



#### 函数

##### 创建

```javascript
//方式一: 具名函数
function 函数名(形参1,形参2...形参N){
		语句...
	}
        
//方式二: 匿名函数表达式
var 函数名  = function(形参1,形参2...形参N){
		语句....
	}

//方式三: 立即执行函数,函数定义完，立即被调用,
;(function () {
            alert('我是一个自执行函数');
        })()
//前面写  分号;  避免一些错误
```



##### 参数

_形参:_  声明形参就相当于在函数内部声明了对应的变量，但是并不赋值。

_实参类型:_  

函数的实参可以是任意的数据类型。

调用函数时解析器不会检查实参的类型，所以要注意，是否有可能会接收到非法的参数，如果有可能则需要对参数进行类型的检查。 

_实参的数量:_

调用函数时，解析器也不会检查实参的数量：

- 多余实参不会被赋值
- 如果实参的数量少于形参的数量，则没有对应实参的形参将是 undefined。



##### 返回值

return 的作用是结束方法。

注意：

- return 后的值将会作为函数的执行结果返回，可以定义一个变量，来接收该结果。
- 在函数中 return 后的语句都不会执行（函数在执行完 return 语句之后停止并立即退出）
- 如果 return 语句后不跟任何值，就相当于返回一个 undefined
- 如果函数中不写 return，则也会返回 undefined
- 返回值可以是任意的数据类型，可以是对象，也可以是函数。



#### 作用域

作用域指一个变量的作用范围。在 js 中，一共有两种作用域：

- 全局作用域
- 函数作用域

##### 全局作用域 

在全局作用域中：

- 创建的**变量**都会作为 window 对象的属性保存。
- 创建的**函数**都会作为 window 对象的方法保存。

全局作用域中的变量都是全局变量，在页面的任意的部分都可以访问的到。



##### 函数作用域

- 在函数体内部的 声明的变量
- 如果一个变量在函数体内部声明，则该变量的作用域为整个函数体，在函数体外不可引用该变量。

```javascript
var y = 10; // 全局变量
function foo() {
	var x = 1; //局部变量
	x = x + 1;
	console.log(y); // 10
}
foo();
console.log(x); // 报错
// 也就是说,函数体内部声明的,在函数体外部是不能使用的。
// 在全局作用域下声明的全局变量，可以在页面任意部分访问得到。
```



##### 上下级关系

当在函数作用域操作一个变量时，它会先在自身作用域中寻找，如果有就直接使用（**就近原则**）。如果没有则向上一级作用域中寻找，直到找到全局作用域；如果全局作用域中依然没有找到，则会报错 ReferenceError。

在函数中要访问全局变量可以使用 window 对象。 `window.a` 

```javascript
function foo() {
	var x = 1;
	function bar() {
		var y = x + 1; // bar可以访问foo的变量x!
		var z = 100;
	}
	var z = y + 1; // ReferenceError! foo不可以访问bar的变量y!
	function ins() {
		x++; // ins 可以访问foo的变量x
		y++; // 不可以访问 bar的变量y
		var z = 1000;
	}
	// 注意 bar 和 ins 中声明的 变量z 是相互独立的,互不影响
}
```



#### 声明提升

##### 变量声明提升

1. 使用 var 关键字声明的变量（ 比如 var a = 1），会在所有的代码执行之前被声明（但是不会赋值）
2. 但是如果声明变量时不是用 var 关键字（比如直接写 a = 1），则变量不会被声明提前。

```javascript
console.log(a); // 打印 undefined ,说明a已经被声明了,只是没有赋值
var a = 10;

//上面相当于:
var a;
console.log(a);
a = 10;



console.log(b); // b is not defined  没有声明提升
b = 2; // 此时 b 相当于 window.b (全局变量)
console.log(b); // 2
```



##### 函数声明提升

1. 使用函数声明的形式创建的函数 `function foo(){}`，会被声明提前。也就是说，整个函数会在所有的代码执行之前就被创建完成，所以我们可以在函数声明之前，调用函数。
2. 使用函数表达式创建的函数 `var bar = function(){}`，不会被声明提前，所以不能在声明前调用。很好理解，因为此时bar 被声明了，且为 undefined，并没有把 function(){} 赋值给 bar。

```javascript
foo(); //执行
bar(); //报错 此时  bar 为undefined
function foo() {
	console.log("我是foo函数");
}
var bar = function() {
	console.log("我是bar函数");
};
```

**注意:**  在函数里面也有声明提升的特性:

1. 使用 var 关键字声明的变量，会在函数中所有的代码执行之前被声明。
2. 函数声明也会在函数中所有的代码执行之前执行。
3. 在函数中，没有 var 声明的变量都是全局变量，而且并不会提前声明。



#### 栈内存和堆内存

JS 中，所有的**变量**都是保存在**栈内存**中的。

**基本数据类型**：

基本数据类型的值，直接保存在栈内存中。值与值之间是独立存在，修改一个变量不会影响其他的变量。

**引用数据类型**：

对象是保存到堆内存中的。每创建一个新的对象，就会在堆内存中开辟出一个新的空间，而**变量保存了对象的内存地址**（对象的引用）。如果两个变量保存了同一个对象的引用，当一个通过一个变量修改属性时，另一个也会受到影响。



#### 函数参数的数据类型

##### 基本数据类型作参数

基本数据类型作为参数传递，函数内部会创建该数据的副本，一切修改不会影响传进来的数据本身。

```javascript
var num = 2；
function ins (x) {
	x++;
}
// 调用ins方法
ins(num);
console.log(num); // 2
```

##### 复杂数据类型作参数

`var arr = [1, 2, 3, 4];`  

引用数据类型栈内存里边的 `arr` 保存的仅仅是一个地址,这个地址指向实际的数组(堆内存当中存放)

```javascript
function add(arr, n) {
	arr.push(n);
}
var arr = [2, 3];
// 调用add方法
add(arr, 4);	//这里的arr保存的就是一个地址,调用函数时改变了相同地址下的数组
console.log(arr); // [2,3,4]
```



#### 递归

当一个函数调用**自身**时，就称其为**递归**。

```javascript
function pow(x, n) {
	if (n == 1) {
		return x;
	} else {
		return x * pow(x, n - 1);
	}
}

alert(pow(2, 3)); // 8
```







#### 对象

对象的作用是：封装信息

对象具有特征（属性）和行为（方法）。

如果两个变量保存的是同一个对象引用，当一个通过一个变量修改属性时，另一个也会受到影响。



##### 创建对象

方法一: 借助构造函数

使用 new 关键字调用的函数，是构造函数。**构造函数是专门用来创建对象的函数**。

```javascript
var obj = new Object();
```

方法二:

使用对象字面量来创建一个对象：

```javascript
var obj2 = {
	name: "张三",
	age: 26,
	sex: "男",
	children: {
		name: "小明",
	},
	//我们还可以在对象中增加一个方法。以后可以通过obj2.sayName()的方式调用这个方法
	sayName: function() {
		console.log("smyhvae");
	}
};
```



##### 属性

###### 添加

```javascript
var obj = new Object();

//向obj中添加一个name属性
obj.name = "张三";


//对象的属性值可以是任何的数据类型，也可以是个  函数
obj.sayName = function() {
	console.log("myname");
};
console.log(obj.sayName); //没加括号，获取的是对象    如果加了括号就执行函数
```

**注意:**    对象里边属性是无序的



###### 获取

```javascript
var obj = new Object();

//向obj中添加一个name属性
obj.name = "张三";
//向obj中添加一个sex属性
obj.sex = "男";


// 获取对象中的属性，并打印出来
console.log(obj.sex); // 打印结果：男
console.log(obj.color); // 打印结果：undefined

//如果获取对象中没有的属性，不会报错而是返回 undefined。
```



###### 删除

语法:   `delete obj.name`



##### 遍历对象

```javascript
// for in 循环 遍历对象 
for (var key in user) {
	// key  指的是 你遍历到的 每个 属性名
		console.log(key); // name  age...
		console.log(user.key); // undefined ,没有key 属性 ,,  . 后边跟的 字符,不会被当做变量解析
	// 属性名是动态的(或者说想让属性名被当做变量解析,那你需要使用[])
		console.log(user[key]);
	}
```



#### 构造函数

构造函数习惯上首字母大写,需要使用 new 关键字来调用

```javascript
// 自定义构造函数 取 创建一个对象
        function Student(name, sex) {
            this.level = '七年级';
            this.school = '不凡';
            this.name = name;
            this.sex = sex;
            this.say = function () {
                // 在new 的时候,这里边的 this  不会被解析
                alert(this.name);
            }
        }

        var user1 = new Student('小明', '男');

        // 函数不调用时,this  指向不明确 ,函数执行时,this 指向才会确定 ,通常指向调用者
        console.log(user1.say);
        user1.say(); // this指向user1   就是 . 前边的那个对象
```

`this` 指向:

- 以函数的形式调用时，this 永远都是 window。比如`fun();`相当于`window.fun();`
- 以方法的形式调用时，this 是调用方法的那个对象
- 以构造函数的形式调用时，this 指向 new 出来的那个实例对象



##### `new` 流程

- 在函数中 创建了一个空对象 {}
- 将函数中`this` 指向创建出来的 {}
- 执行函数中的代码（包括设置对象属性和方法等）
- 将新建的对象作为返回值返回



#### JSON对象

JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。

它使用文本表示一个 JS 对象的信息，本质是一个字符串

```javascript
// 对象类型是不能通过网络进行传输的,只能是文本形式
var movie = {
	title: "我不是药神",
	casts: [{
			name: "徐峥",
			avatar: "http://xxxx.jpg",
			age: 45,
		},
        {
			name: "黄渤",
			avatar: "http://xxxx2.jpg",
			age: 42,
		},
	],
	pubDate: "2017-10-1",
	rate: 5,
};
console.log(movie)
// 1. 通过JSON.stringify(jsonObj) ==> 可以把json类型的对象转换为文本
var jsonStr = JSON.stringify(movie);
console.log(jsonStr);

//2. 将json字符串转换为对象
var movieStr = '{"name":"张三","age":20}';
// JSON.parse  ==> 字符串转换为对象
var movieObj = JSON.parse(movieStr);

// 对象和json类型的对象都可以通过 JSON.stringify() 转换为字符串


// 注意
var str = '{a: "Hello", b: "World"}';
// 这样直接在对象两边加上引号变成的字符串没有办法转换成对象,因为属性名没有引号""
// console.log(JSON.parse(str)); // 报错
```



#### 数组高级api

##### reverse()

反转数组，返回结果为**反转后的数组**（会改变原来的数组）

```javascript
var arr = ["a", "b", "c", "d", "e", "f"];

var result = arr.reverse(); // 将数组 arr 进行反转

console.log(arr); //["f", "e", "d", "c", "b", "a"];
```



##### sort()

对数组的元素进行从小到大来排序（会改变原来的数组）

无参数:

```javascript
//字符串
var arr = ["e", "b", "d", "a", "f", "c"];
console.log(arr.sort()); // a ,b ,c ...

//数字
var arr1 = [5, 2, 11, 3, 4, 1];
console.log(arr1.sort());//[1, 11, 2, 3, 4, 5];

//不带参，则默认按照Unicode 编码，从小到大进行排序。
```



有参数:

在 sort()添加一个回调函数，来指定排序规则

```javascript
var arr = [5, 2, 11, 3, 4, 1];

// 自定义排序规则
var result = arr.sort(function(a, b) {
	return a - b; // 升序排列
	// return b - a; // 降序排列
});

console.log(arr); // [1,2,3,4,5,11]
console.log(result); // [1,2,3,4,5,11]
```

**浏览器根据回调函数的返回值来决定元素的排序：（重要）**

- 如果返回一个大于 0 的值，则元素会交换位置
- 如果返回一个小于 0 的值，则元素位置不变
- 如果返回一个 0，则认为两个元素相等，则不交换位置



##### slice()

`slice()`：从数组中提取指定的一个或者多个元素，返回结果为**新的数组**（_不会改变原来的数组_ ）。

备注：该方法不会改变原数组，而是将截取到的元素封装到一个新数组中返回。

语法: 

```javascript
新数组 = 原数组.slice(开始位置的索引, 结束位置的索引); //注意：包含开始索引，不包含结束索引
```

```javascript
var arr = ["a", "b", "c", "d", "e", "f"];

var result1 = arr.slice(2); //从下标为2值开始提取
var result2 = arr.slice(-2); //提取最后两个元素
var result3 = arr.slice(2, 4); //提取从下标为2到下标为4之间的值（不包括下标为4的值）
var result4 = arr.slice(4, 2); //空

console.log(result1); //["c", "d", "e", "f"];
console.log(result2); //["e", "f"];
console.log(result3); //["c", "d"];
console.log(result4); //[];
```



##### splice()

替换或者删除

语法: 

```javascript
新数组 = 原数组.splice(起始索引index, 需要删除的个数, 第三个参数, 第四个参数...);
//三个及之后的参数，表示：向原数组中添加新的元素，这些元素将会自动插入到开始位置索引的前面。
```

```javascript
var ar5 = ["a", "b", "c", "d", "e", "f"];
console.log(arr.splice(1, 2)); // [b,c]  删除的那些元素组成的数组
console.log(arr); // ["a", "d", "e", "f"]

//从第index为1的位置开始删除元素,一共删除三个元素。并且在 index=1 的前面追加两个元素
console.log(arr.splice(1, 2, "x")); // ["d", "e"]
console.log(arr); // ["a", "x", "f"]
```



##### indexOf() 和 lastIndexOf()

获取数据索引

- indexOf(value)：从前往后索引，获取 value 在数组中的第一个下标。
- lastIndexOf(value) ：从后往前索引，获取 value 在数组中的最后一个下标。

```javascript
//我们可以判断某个值是否在指定的数组中。如果没找到则返回-1。
var arr = ["a", "b", "c", "d", "c", "d", "c"];

console.log(arr.indexOf("c")); //从前往后，找第一个"c"在哪个位置,2,找到之后就停止
console.log(arr.lastIndexOf("d")); //从后往前，找第一个"d"在哪个位置,5
```



#### forEach遍历数组

```javascript
// forEach 可以遍历数组
// 回调函数内  第一个参数 表示遍历到的元素 ,第二个参数表示其对应的下标
arr.forEach(function (item, index) {
            console.log(index, item);
        });
```



#### 字符串方法

**charAt()** 获取相应位置的字符
**charCodeAt()** 指定位置字符 的 Unicode 编码
**indexOf()** 返回字符在字符串中的位置
**lastIndexOf()**
**concat()** 连接字符串
**slice()** 提取字符串的某个部分
**substr()** 截取字符串  				 **substr(起始位置,[取的个数])**
**toUpperCase()** 全部转换大写字母
**toLowerCase()**

