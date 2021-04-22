# CSS 

## 目录

```markdown
1.CSS是什么
2.CSS怎么用（快速入门）
3.CSS选择器（重点+难点）
4.美化网页（文字，阴影，超链接 ，列表渐变）
5.盒子模型
6.浮动
7.定位
8.网页动画（特效效果）
```

### 什么是CSS和发展史

```markdown
1. Cascading Style Sheet层叠级联样式表
    a. CSS：表现（美化网页）字体，颜色，边距，高度，宽度，背景图片，网页定位，网页浮动
2. 发展史：
    i. CSS1.0
    ii. CSS2.0　DⅣ（块）+CSS,HTML与CSS结构分离的思想，网页变得简单，SEO
    iii. CSS2.1　浮动，定位
    iv. CSS3.0　圆角，阴影，动画浏览器兼容性～
```

### CSS的快速入门及优势

建议程序格式

<img src="D:\JAVAMD\CSS.assets\image-20200807182225190.png" alt="image-20200807182225190" style="zoom: 50%;" />

规范：<img src="D:\JAVAMD\CSS.assets\image-20200807182318856.png" alt="image-20200807182318856" style="zoom: 33%;" />

练习时可直接在html文件的head下用

```css
<style>css程序</style>
```

css优势

```mark
a. 内容和表现分离
b. 网页结构表现统一，可以实现复用
c. 样式十分的丰富
d. 建议使用独立于html的cs文件
e.利用SEO，容易被搜索引擎收录
```

### 四种CSS的导入方式

行内样式：

```html
<--!在标签元素内，编写一个style属性，编写样式即可-->
    <h1 style="color:red">
        内容
    </h1>
```

内部样式：

```html
在head内写<style>css代码</style>
```

外部样式：

```html
１、编写css文件
2、在html代码中，打入关联语句
第一种写法链接式：
	<link rel="stylesheet" href="css/style.css">
第二种写法导入式：
    <style>
        @import url("css/style.css")
    </style>
```

各种导入方式的优先级:就近原则

## 选择器

- 选择器作用：

- - 作用：选择页面上的某一个或者某一类元素

### 标签选择器

- 标签选择器，会选择到页面上所有的这个标签的元素 
- 格式：**标签类型{}**

```css
h1{color:"red";}
```

### 类选择器

格式：对应已定义的class，  **.class名{}**

```html
定义：class="映上"
选择器：.映上{
	color:"red";
}
```

好处：可以多个标签归类，是同一个 class，可以复用

### id选择器

格式：对应已定义的id，  **#id号{}**

```html
定义：id="映上"
选择器：#映上{
	color:"red";
}
```

好处：id全场唯一

### 三种基本选择器的优先级问题：

- 不遵循就近原则，固定的id选择器 class选择器>标签选择器

### 层次选择器

- 后代选择器：

- - 在某个元素的后面 祖爷爷 爷爷  爸爸 你
  - 格式： **基本选择器 p{}**

```css
/*后代选则器,选择body括号内的所有p标签*/ 
body p
{background:red;}
```

- 子选择器:
  - 只选择儿子
  - 格式： **基本选择器>p{}**

```css
/*子选择器,选择body括号内的p标签，不包括P标签括号内的*/ 
body>p
{background:red;}
```

- 相邻兄弟选择器:
  - 同辈,一个
  - 格式： **基本选择器+p{}**

```css
/*相邻兄弟选择器，只有一个相邻向下*/
.active+p{
    background:red;
}
```

- 通用选择器：
  - 当前选中元素的向下的所有兄弟元素
  - 格式：**基本选择器~p{}**

```css
/*相邻兄弟选择器，当前选中元素的向下的所有兄弟元素*/
.active~p{
    background:red;
}
```

### 结构伪类选择器

- 两个好理解的结构伪类选择器：

```css
<!--        选择ul下的第一个li元素-->
        ul li:first-child
        {
            background:red;
        }
<!--        选择ul下的最后一个li元素-->
        ul li:last-child
        {
            background:blue;
        }
```

- 两个复杂的结构伪类选择器：

```css
/*    定位到父元素，选择当前的第一个元素，而且必须为当前元素才生效*/
p:nth-child(1)
{
    background: green;
}

/*选中父元素，选择当前p元素的第二个*/
p:nth-of-type(2)
{
    background: aqua;
}
```

### 属性选择器-重要、常用

- 格式：

- - **元素名[属性条件（可用正则表达式）]{css程序};**

```css
a[hrep$=jpg]{
    background:yellow;
}
```

- =绝对等于	*=包含	^=开头为	$=结尾为

### span标签及字体样式

**span标签：重点要突出的字，使用span套起来，约定俗成**

字体样式：

```markdown
font-family:字体

font-size：字体大小

font-weight：字体粗细

color：字体颜色
```

可以直接一起写：

```css
p{font:oblique bolder 16px "楷书";}
```

### 文本样式

- 文本颜色：

```css
p[class=fff]
    {
        color:green;
    }
```

```css
/*颜色
单词
RGB 0-f
RGBA 0-f*/
p[class=fff]
{color:green;}
```

- 文本居中：
  - 格式：text-align:排版，居中

```css
text-align:center
```

- 段落首行缩进：

```css
text-indent:2em(两个字段)
```

- 行高：

```css
height:300px;
line-height:300px;
说明：行高和块的高度，就可以上下居中
```

- 划线：

```css
text-decoration:underline/line-through/overline(下中上划线)
○ 超链接标签默认有下划线，去除：
text-decoration:none;
```

- 文本图片水平对齐：

```css
img,span{
    vertical-align:middle;
}
```

### 文本阴影和超链接伪类

超链接伪类：

```html
<style>
   	/*默认*/
    a{}
    /*鼠标悬浮的状态*/
    a:hover{}
    /*鼠标按住未释放的状态*/
    a:active{}
    /*已点击过后的状态*/
    a:visited{}
   
</style>
```

文本阴影：

```css
格式：/*text-shadow:阴影颜色，水平偏移，垂直偏移，阴影半径*/
#price{
    text-shadow:red 10px 10px  10px;
}
```

### 盒子模型及边框使用

什么是盒子：<img src="D:\JAVAMD\CSS.assets\image-20200807201924933.png" alt="image-20200807201924933" style="zoom:50%;" />

​				margin：外边距 padding：内边距 border：边框

border边框：

```css
border:1px solid red;
```

- 边框的粗细 边框的样式：solid 实线 dashed 虚线 边框的颜色

  圆角边框:格式：border-radius:10px

### display和浮动

回忆块元素和行内元素：

块级元素：独占一行  h1~h6 p div 列表...

行内元素：不独占一行 span a img strong...

- display使用：

- - display:

  - - block(块元素) 
    - inline(行内元素） 
    - inline-block(是块元素，但是可以内联，在一行!)

  - 说明：这个也是一种实现行内元素排列的方式，但是我们很多情况都是用foat，因为还在标准文档里面。

- loat使用：

- - float:

  - - right:右浮动
    - left：左浮动

### overflow及父级边框場陷问题

- overflow用法：

  ![image-20200807212339252](D:\JAVAMD\CSS.assets\image-20200807212339252.png)

- overflow:hidden：

- - 当父元素设置了height值时，则设置overflow:hidden后，子元素超出父元素部分隐藏
  - 当父元素的高度是靠子元素撑开的时候，子元素浮动时，则在父元素使用overflow:      hidden可以清除浮动，使得父元素的高度依旧是靠子元素撑开。

- clear说明：![image-20200807213303893](D:\JAVAMD\CSS.assets\image-20200807213303893.png)

- 父级边框塌陷问题解决：

  - 增加父级元素的高度：![image-20200807213327512](D:\JAVAMD\CSS.assets\image-20200807213327512.png)

  - 增加一个空的dⅳ标签，清除浮动：![image-20200807213343519](D:\JAVAMD\CSS.assets\image-20200807213343519.png)

- - 在父级元素中增加一个      overflow:hidden；

  - - 父类添加一个伪类：after：![image-20200807213417011](D:\JAVAMD\CSS.assets\image-20200807213417011.png)

- 什么是伪类和伪元素：

- - 不专业的说带冒号的就是伪类或者伪元素了。作用就是提供一些特定的效果，比如未访问过的链接visited这些。
  - 伪元素的作用就是为你提供一些方便，如果有3行字，第一行要有不一样的效果，直接是<p>第一行第二行第三行</p>，然后定义      p:first-line就可以了。

- 小结：

  - 浮动元素后面增加空div:简单，代码中尽量避免空div

  - 设置父元素的高度:简单，元素假设有了固定的高度，就会被限制

  - overflow:简单，下拉的一些场景避免使用

  - 父类添加一个伪类：after（推荐）写法稍微复杂一点，但是没有副作用，推荐使用！

- display和overfloat的对比：

- - display：

  - - 方向不可以控制

  - float：

  - - 浮动起来的话会脱离标准文栏流，所以要解决父级边框塌陷的问题

### 相对定位：

- - 相对定位：position:relative；

  - - 相对于原来的位置，进行指定的偏移，相对定位的话，它任然在标准文档流中，原来的位置会被保留

- 例子：![image-20200807213632684](D:\JAVAMD\CSS.assets\image-20200807213632684.png)

### 绝对定位和固定定位

- 绝对定位：

- - 没有父级元素定位的前提下，相对于浏览器定位。

  - 假设父级元素存在定位，我们通常会相对于父级元素进行偏移

  - 在父级元素范围内移动

  - 说明：

  - - 相对于父级或浏览器的位置，进行指定的偏移，绝对定位的话，它不在在标准文档流中，原来的位置不会被保留

- 固定定位fixed：

- - 格式：

  - - position:fixed;

- 绝对定位、固定定位的区别：

- - 都会出现在相对于浏览器的位置，但绝对定位会随着滚动条发生位移，固定定位不会。

### z-index及透明度

- 背景透明度；

- - 格式：opacity:      0~1;

- z-index：默认是0，最高无限

- - 作用：<img src="D:\JAVAMD\CSS.assets\image-20200807213718407.png" alt="image-20200807213718407" style="zoom: 50%;" />

