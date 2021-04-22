# HTML5

## 目录

**初始HTML**－**网页基本标签**－**图像、超链接、网页布局**－**列表、表格、媒体元素**－**表单及表单应用**－**表单初级验证**

## 初识HTML

- 什么是HTML:
  - Hyper Text Market Language（超文本标记语言）
  - **超文本包括：文字、图片、音频、视频、动画等**。

- HTML发展史：
  
  <img src="D:\HTML5.assets\image-20200807162512291.png" alt="image-20200807162512291" style="zoom:50%;" />
  
- HTML5的优势：
  - 世界知名浏览器厂商对HTML5的支持
  - 市场的需求
  - 跨平台

- W3C标准：

- - W3C：

  - - World       Wide Web Consortium（万维网联盟）
    - 成立于1994年，Web技术领域最权威和具影响力的国际中立性技术标准机构

  - W3C标准包括：

  - - 结构化标准语言（HTML、XML）
    - 表现标准语言（CSS)
    - 行为标准（DoM、       ECMAScript）

- HTML基本结构:

  ```html
  <html>
      <head>
          <title>网页头部</title>
      </head>
      <body>
          主体部分
      </body>
  </html>
  说明:<body>、</body>等成对的标签，分别叫放和合标签单独呈现的标签（空元素），如<h/>；意为用/来关闭空元素
  ```

  ## 网页基本信息

- HTML的注释怎么写：

- <!-- 注释 -->

- 网站基本信息使用和说明

```html
<!--DOCTYPE:告诉浏览器，我们要使用什么规范。默认为html。-->
<!DOCTYPE html>
<html lang="en">
<!--head标签代表网页头部-->
<head>
    <!-- meta描述性标签，它用来描述我们网站的一些信息  -->
    <!--   meta一般用来做SEU -->
    <meta charset="UTF-8">
    <meta name="keywords"content="何高宇，山东大学">
    <meta name="description"content="何高宇是山东大学的一名学生">
    <!-- title网页标题 -->
    <title>我的第一个网站</title>
</head>
<!--body标签代表网页主体-->
<body>
HelloWorld!!
</body>
</html>
```

## 网页基本标签

```html
<!--标题标签-->
<h1>一级标签</h1>
<h2>二级标签</h2>
<!--段落标签-->
<p>醉卧沙场君莫笑</p>
<!--水平线标签-->
<hr/>
<!--换行标签-->
醉卧沙场君莫笑</br>
<!--字体样式标签-->
<strong>粗体:醉卧沙场君莫笑</strong>
<em>斜体:古来征战几人回</em>
• 注释和特殊符号
    ○ 空格：
        § &nbsp; 空格
    ○ 格式：
        § &---；
```

## 图形标签

- 添加图片的格式：

  ​	<img src="D:\HTML5.assets\image-20200807162527330.png" alt="image-20200807162527330" style="zoom:50%;" />

  - 说明:	src:图片地址（必填）：../--上一级目录    		○ alt：图片加载失败返回的文字（必填）

## 超链接标签及应用

- 链接标签（页面间链接）：

  - 格式:<img src="D:\HTML5.assets\image-20200807162543281.png" alt="image-20200807162543281" style="zoom:50%;" />

  - 说明:

    	§ href：必填，表示要跳转到那个页面
      	§ target：窗口打开位置
      	    □ _self:在本窗口打开（默认）

- 锚链接（实现页面间跳转）：

  - 条件:需要一个标记和可以跳转标记的链接

  - 格式:

    ```html
    <!--使用name作为标记-->
    <a href name="top">顶部</a>
    <!--跳转-->
    <a href #top>回到顶部</a>
    ```

    

## 块元素与行内元素

```markdown
• 块元素：
    ○ 无论内容多少，该元素独占一行
    （p、h1-h6.）
• 行内元素：
    ○ 内容撑开宽度，左右都是行内元素的可以在排在一行
    （a. strong. em)
```

## 列表标签

有序列表代码及其效果图

<img src="D:\HTML5.assets\image-20200807162616034.png" alt="image-20200807162616034" style="zoom:50%;" />![image-20200807162623585](D:\HTML5.assets\image-20200807162623585.png)

无序列表代码及其效果图：

<img src="D:\HTML5.assets\image-20200807162616034.png" alt="image-20200807162616034" style="zoom:50%;" />![image-20200807162623585](D:\HTML5.assets\image-20200807162623585.png)![image-20200807162632305](D:\HTML5.assets\image-20200807162632305.png)

自定义列表：dl:标签   dt：标签名称  dd：列表内容

![image-20200807162632305](D:\HTML5.assets\image-20200807162632305.png)

## 表格元素

基本结构：单元格	行	 列	跨列	跨行

```html
<table border="1px">
    <tr>
        <td colspan="2" (跨两列）rowspan（跨两行）="2">1-1</td>
        <td>1-2</td>
    </tr>
    <tr>
        <td>2-1</td>
        <td>2-2</td>
    </tr>
</table>
```

## 媒体元素

video:格式：

```html
<video src="../resources/video controls autoplay"></video>
说明：
	src=资源路径
	controls：控制条
	autoplay：自动播放
```

autio:音频

<img src="D:\HTML5.assets\image-20200807162654844.png" alt="image-20200807162654844" style="zoom:50%;" />

## 页面结构分析

```markdown
header 标题头部区域的内容（用于页面或页面中的一块区域）
footer 标记脚部区域的内容（用于整个页面或页面的一块区域）
section Web页面中的一块独立区域
article	独立的文章内容
aside 相关内容或应用（常用于侧边栏）
nav	导航类辅助内容
```

## iframe内联框架

```markdown
• 用途：作为容器可装载网址、链接
<iframe src="https://www.baidu.com" frameborder="0" name="jaoe" width="1000px" height="800px">
</iframe>
说明：src：途径
	name：代号名字
iframe容器内没有内容，但当点击跳转时，百度网址会在iframe内打开。
```

## 初识表单pos和get提交

```html
<form method="post" action="result. html">
    <p>名字：< input name="name"type="text"></p>
	<P>密码：<input name="password" type="password"></p>
	<input type="submit" name="Button"value="53">
	<input type="reset" name="Reset" value="重填">
</form>
说明：
    ○ method：规定如何发送表单数据
    ○ action：表单提交的位置，可以是网站，也可以是一个请求处理地址
    ○ get方式提交：我们可以在url中看到我们提交的信息，不安全，高效post：比较安全，传输大文件
    ○ form 元素的 name 属性提供了一种在脚本中引用表单的方法。
	○ input必须要name属性才可以传输
```

## 表单元素框

表单元素：



<img src="D:\HTML5.assets\image-20200807162716705.png" alt="image-20200807162716705" style="zoom:50%;" />

### 文本框

例子：

```html
<p>
    <input type="text" name="username" maxlength="8" size="30"value="映上">
</p>
```

### radio单选框

```html
○ 需要用同一个name去命名单选框的元素，否则会出现两个都可以选的情况。
例子：
<p>性别：
    <input type="radio"value="boy"name="sex">男
    <input type="radio"value="girl"name="sex">女
</p>
<!--单选框标签：
input type="radio"
value:单选框的值
name:表示的组
-->
```

### 按钮

```html
<!--按钮
       input type"button"普通按钮
       input type="image"图像按钮
       input type="submit"提交按纽
       input type="reset"重置按钮
 -->
<input type="button"name="btn1" vaue="点击变长">
<input type="image" src="../resources/image/1.jpg">
<input type="submit">
<input type="reset">
```

### 多选框

```html
<input type="checkbox" value="sleep" name="hobby">睡觉
<input type="checkbox" value="code" name="hobby">敲代码
说明：显示的值在外面填写，checked默认选中
```

### 列表框、下拉框

```html
<p>
    <select name="列表名字">
       <option value="china">中国</option>
       <option value="us" selected>美国</option>
    </select>
</p>
说明：selected：默认在第一位
```

### 文本域

```html
<!--
    作用：可以输入大量文本信息
    参数：cols="50" rows="10"
    -->
<p>反馈：
    <textarea name="textarea" cols="50" rows="10">
    文本内容
    </textarea>
</p>
```

### 文件域

```html
<!-- 
	input type="file" name="files"
	作用：可以上传文件，在表单内使用
-->
<p>
    <input type="file" name="files"
    <input type="button" value="上传" name="upload">
</p>
```

### 搜索框

```html
<p>
    搜索：
    <input type="search" name="search">
</p>
```

### 滑块

```html
<！--滑块input type=range-->
<p>音量
<input type="range" name="voice" min="0" max="100" step="2">
</p>
    说明：最大、最小值、每次移动间隔。
```

### 邮件验证

```html
<！--邮件验证-->
<p>邮箱:
<input type="email" name="email">
</p>
```

### 网络地址URL验证

```html
<!--URL-->
<p>
    URL:
    <input type="url" name="url">
</p>
```

### 数字验证

```html
<!--数字-->
<p>数字：
   <input type="number" name="num" max="100" min="0" step="2">
</p>
```

### 表单元素修饰

- readonly 只读

- disabled 禁用

- hidden  隐藏

- pleaceholder:

- - 输入框内的提示信息；

- required:

- - 输入框内必须要填信息，非空判断；

- pattern：

- - 通过正则表达式自己添加验证

增强鼠标可用性：

```html
<p>
    <!--增强鼠标的可用性-->
    <label for="mark">点击可输入框</label>
    <input type="text">
</p>
```

