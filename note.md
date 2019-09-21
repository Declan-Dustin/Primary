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



# markdown语法

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