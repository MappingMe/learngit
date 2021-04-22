# JavaScript

## JavaScript是什么

```mark
1. UI框架：
    ○ Ant- Design：阿里巴巴出品，基于 React的U框架
    ○ Elemental、 IvIew、ice：饿了么出品，基于vue的Ul框架
2. 什么是javaScript：
    a. JavaScript是一门世界上最流行的脚本语言
3. ECMAScript:
    a. ECMAScript它可以理解为是 JavaScript的一个标准,最新版本已经到es6了,但是大部分浏览器还只停留在支持es5代码上。
4. javaScript作用：
    a. “JavaScript是一种属于网络的脚本语言，常用来为网页添加各式各样的动态功能，为用户提供更流畅美观的浏览效果。它可以使网页具有交互性；可以处理表单，检验用户的输入，并提供及时反馈节省用户时间；还可以根据用户的操作，动态的创建页面。”
```

## 基本使用Hellowrold

```markdown
1. 内部引入：
    a. <script>~</script>
    b. 说明：可写在head中，或body的底部。
2. 外部引入：
    a. 生成相应的script文件，在HTML中写入<script src="文件路径"</script>
3. 有时在script中会有type="text/javascript",默认便是这个，不用自己写。
4. 注释：
    a. JavaScript内的注释和Java的一样
5. 弹窗测试代码：
    a. alert('helloworld');
```

## 数据类型快速浏览

1. 定义变量：
    a. 变量类型(var) 变量名  = 变量值;
2. 数值:
	a. js不区分小数和整数，同意用Number
        123//整数
        123123.1//浮点数123.1
        1.123e3//科学计数法
        -99复数
        NaN// not a number 
        Infinity//表示无限大
        NaN与所有的数值都不相等，包括自己，只能通过一个方法isNaN进行判断
3. 字符串:
    a. 单双引号括起来都可以
4. 布尔值：
    a. true false
5. 逻辑运算：
	&& 两个都为真结果为真   ||一个为真结果为真	！真即假，假即真
6. 比较运算符：
    = 赋值运算符
    **== 等于（类型不一样，值一样，也会判断为true）**
    === 绝对等于
7. 浮点数问题：
	console.log(1/3)===(1-(2/3)),结果为false
	可以使用（Math.abs（1/3-（1-2/3））<0.00000001进行判断
8. null和 undefined
    a. null 空
    b. undefined 未定义
9. 数组：
    a. Java的数组必须是相同类型的对象，JS中不需要这样！
    c**. 取数组下标：如果越界了，就会：undefined**
10. 对象：
    a. **对象是大括号，数组是中括号。**
    b. **每个属性之间使用逗号隔开**，最后一个不需要添加
        var person={
        name="映上",
        age:3,
        tags:['js','java','web']
        }

## 严格检查模式和局部变量

```markd
1. 'use strict':
    a. 使用严格检查模式，预防的javascript的随意性导致产生的一些问题
    b. 前提：IEDA需要设置支持ES6语法；必须写在javascript的第一行
2. 局部变量：
    a. 局部变量建议都使用let去定义
```

## 字符串类型详解

```mark
	1. 正常字符串我们使用单引号，或者双引号包裹
	2. 转义字符\：
	3. 多行字符串编写：`多行文本`
	4. 引用变量： `文本${变量名}`
	5. 字符串长度属性：str. length
	6. 字符串的可变性，不可变;
    7. 大小写转换方法：
    	str.toUpperCase(); 
    	str.toLowerCase();
	8. 获取字符串中的字符位置：
		a. student.indexOf('t');
	9. 截取字符串：
		a. substring(开始坐标，截取长度)
```

## 数组类型详解

1. Aray可以**包含任意的数据类型**
2. 长度:
    a. 假如给**arr.length赋值**，数组大小就会发生变化~如果赋值过小,元素就会丢失
3. indexof，通过元素获得下标索引:
    arr.indexof(2)---->1
4.	lice() 截取Array的一部分,返回一个新的数组,类似于String中的substring 
5. push(),pop()  尾部
    push():压一个元素到尾部
    pop():从尾部弹出一个元素
6. unshift(),shift() 头部
    unshift()压一个元素到头部
    pop():从头部弹出一个元素
7. 排序 sort()
    例：arr=['a','c','b'];arr.sort();arr=['a','b','c']
8. 元素反转 reverse():
    例：arr=['a','c','b'];arr.reverse();arr=['b','c','a']
9. 数组拼接 concat() :并没有修改数组，只是会**返回一个新的数组**
10. 连接符 join() :
    a. 打印拼接数组，使用特定的字符串连接

## 对象类型详解

1. JavaScript中的**所有的键都是字符串，值是任意对象**！
2. 什么是对象:
    Js中对象，**{…}表示一个对象，键值对描述属性xxxx:xxxx，多个属性之间使用逗号隔开，最后一个属性不加逗号！**
3. 使用一个不存在的对象属性，不会报错！ 会打出undefined
4. 动态的删减属性,通过 delete删除对象的属性:
    delete person.name;
    返回：true
5. 动态添加,直接给新的属性添加值即可:
    person.name='映上';
    返回：true
6. **判断属性是否在某个对象当中 'xxx' in xxx**:(继承过来的也可以)
    'name' in person
    返回：true/false
    a. 
7. 判断一个属性是否是这个对象自身拥有的 hasOwnProperty(继承过来的不可以):
    person.hasOwnProperty('toString');
     返回：false

## 分支和循环详解

```javascript
//if判断:
    var age=3;
    if(age>3){
        alert(true);
    }else{
        alert(false);
    }
//while循环
    while(age<100){
        age+=1;
        console.log(age)
    }
//for循环
    for(int i=0;i<10;i++){

    }
//forEach循环
    var age=[10,10,99,99,22];
//函数
    age.forEach(function(value){
        console.log(value);
    })
//forIn循环(遍历age的值赋给num，也可遍历对象)
    for(var num in age){
    }
```

## Map和set集合

map集合，以键值对的方式存储数据

例：

```javascript
var map=new map([['tom',90],['john','80']]);//创建map集合
map.get('tom');//通过key获得value
map.set('admin',1234);//新增或修改
map.delete('tom');//删除键值对
```

Set:无序不重复集合：

例：

```javascript
set.add(2);//添加
set.delete(1);//删除
set.has(3);//判断是否包含某个元素
```

## iterator迭代

遍历数组、map集合、set集合,for of打印具体的值，for in 打印下标

```javascript
for(var x of array){
    
}
for(var map of array){
    
}
for(var set of array){
    
}
```

## 函数及其参数

```javascript
1. 方法和函数的区别:
    a. 方法是在对象里面的,函数不是.
2. 定义函数格式一:(不需要返回值)
    a. fuction 函数名 (参数){函数体};
    例：
    function abs(x){
        if(x>0){
            return x;
        }
    }
    一旦执行到 return代表函数结束，返回结果！如果没有执行 return，函数执行完也会返回结果，结果就是 undefined
3. 定义函数方式二：
        3. 定义函数方式二：
    a. var abs = function(x){函数体};
    function(x){…}是一个匿名函数，但是可以赋值给var abs；
4. 调用函数：
    abs(10);
    参数问题：JavaScript可以传任意个参数，也可以不传参数~
5. 假设不存在参数，如果规避？
    a. 使用typeof x =='number'来判断，用throw 抛出异常。
6. arguments
        i.  是JS免费赠送的一个关键词：
    a. 代表，传递进来的所有的参数，是一个数组
问题：、arguments包含所有的参数，我们有时候想使用多余的参数来进行附加操作。需要排除已有参数
7. rest。ES6引入的新特性，获取除了已经定义的参数之外的所有参数
    a. 格式：
        i. function abs (a,b,…rest){};(rest参数只能写在最后面，必须用…标识)

```

## 变量的作用域、let、 const详解

1. 在 javascript中，var定义变量实际是有作用域的。
   假设**在函数体中声明，则在函数体外不可以使用**-（中非要想实现的话，后面可以研究一下闭包）

2. 假设，内部函数变量和外部函数的变量，重名：假设在 javascript中函数查找变量从自身函数开始，由呐内”向"外“查找。假设外部存在这个同名的函数变量，则内部函数会屏蔽外部函数的变量。 
3. 提升变量的作用域：
	function qj(){
		var x='x'+y;     ==>   x undefinet
		var y='y';
	}
	说明：js执行引擎，**自动提升了y的声明，但是不会提升变量y的赋值**
	杰伦：这个是在 javAscript建立之初就存在的特性。养成规范：所有的变量定义都**放在函数的头部**，不要乱放，便于代码维护；
4. 全局函数：定义在script下的函数
5. 全局对象 window：	Javascript实际上**只有一个全局作用域，绑定在window下**，任何变量（函数也可以视为变量），假设没有在函数作用范围内找到，就会向外查找，如果在全局作用域都没有找到，报错【 RefrenceError】
6. 由于我们所有的全局变量都会绑定到我们的 window上。如果不同的js文件，使用了相同的全局变量，冲突->如果能够减少沖突？
 ---**把自己的代码全部放入自己定义的唯一空间名字中**，降低全局命名冲突的问题
	var yingshang={};//唯一全局变量
7. 局部作用域let：
	问题：变量除了在函数体内声明的都是全局变量，容易发生冲突问题，**定义let关键词**
8. 常量 const：
	定义常量

## Data的基本使用

```javascript
var now = new Date();//Sat Jan 04 2020 10:47:06 GMT+0800（中国标准时间）
now.getFullYear();//年
now.getMonth();//月
now.getDate();//日
now.getDay();//星期几
now.getHours();//时
now.getMinutes();//分
now.getSeconds();//秒

now.getTime();//时间戳 全世界通用 1970 1.1 0：00：00  毫秒数
new Date(1234443555);//时间戳转成时间
```

## JSON对象

1. json是什么:![image-20200808123944881](D:\JAVAMD\JavaScript.assets\image-20200808123944881.png)

2. javascript与JSON:
   1. 在 JavaScript一`切皆为对象,任何js支持的类型都可以用JSON来表示；

3. JSON字符串和JS对象的转化：

<img src="D:\JAVAMD\JavaScript.assets\image-20200808124044115.png" alt="image-20200808124044115" style="zoom:50%;" />

## 操作BOM对象

1. 什么是BOM对象：
   1. BOM是浏览器对象模型，是用于描述这种对象与对象之间层次关系的模型，浏览器对象模型提供了独立于内容的、可以与浏览器窗口进行互动的对象结构。BOM由多个对象组成，其中**代表浏览器窗口的Window对象是BOM的顶层对象**，其他对象都是该对象的子对象。

2. window 

3. 1. 代表 浏览器窗口：
   2. 方法和属性：window.alert(); window.innerHeight; window.innerWidth;

3. Navigator（不建议使用）
   1. Navigator,封装了浏览器的信息,大多数时候，我们不会使用navigator对象，因为会被人为修改，不建议使用这些属性来判断和编写代码

4. screen:

5. 1. 代表屏幕的尺寸：screen.width  screen.height

5. location（重要）：

1. 1. location：代表当前页面的URL信息；

![image-20200808125314215](D:\JAVAMD\JavaScript.assets\image-20200808125314215.png)

6. document（DOM）:

1. 1. 代表当前页面，HTML DOM文档树；
   2. 更改网站标题 ：document.title="***";
   3. 获取cookie: document.cookie 劫持cookie原理:获取你的 cookie上传到他的服务器

7. history:

8. 1. 代表浏览器的历史纪录

## DOM节点操作

1. 浏览器网页就是一个Dom树形结构！

2. 1. 更新：更新Dom节点
   2. 遍历dom节点：得到Dom节点
   3. 删除：删除一个Dom节点
   4. 添加：添加一个Dom节点

### 获得dom节点

- 通过标签类型：document.getElementsByTagName();

- 通过ID：document.getElementsById();

- 通过Class名：document.getElementsByClassName();
  - 说明：这是原生代码，之后我们尽量都是用JQuery

### 更新DOM节点

- 操作文本：

- ```javascript
  id1.interText='456';  // 修改文本的值
  id1.interHTML='<strong>123</strong>' //可以解析HTML文本标签
  ```

- 操作CSS3：

  ```javascript
  id1.style.color='yellow';//属性使用 字符串 包裹
  id1.style.fontSize='20px';//转驼峰命名
  ```

- 注意：

- - script需要放在body的最后面，不可放在head;否则会发生id未定义的错误

### 删除DOM节点

1. 删除节点步骤：先获取父节点，再通过父节点删除自己

例：

```javascript
var self=document.getElementById('p1');//获得要删除的节点
var father=p1.parentElement;//获得要删除节点的父节点
father.removeChild(self);
//		c. 注意：删除多个节点的时候，children是时刻都在变换的，删除节点的时候要注意~
```

### 创建和插入DOM节点

- interHTML：

- - 我们获得了某个Dom节点，假设这个dom节点是空的，我们通过      innerHTML就可以增加一个元素了，但是这个DOM节点已经存在元素了，我们就不能这么干了！会产生覆盖

- 追加：

- - 格式：DOM节点.appendChild(DOM节点);

```javascript
var js=document.getElementById('p1');
var list=document.getElementById('p2');
list.appendChild(js);//追加到后面
```

- 创建一个新的节点，实现插入：
  - 创建一个空白的新标签：格式=>createElement(标签类型)
  - 用追加实现插入

- js动态实现style编写：

```javascript
var newStyle=document.createElement("style");
newStyle.innerHTML="p{background-color:green}"
document.getElementsByTagName("head")[0].appendChild(newStyle);
```

## 表单

1. 获取和更改输入框的值：

```javascript
input_text.value//得到输入框的值
input_text.value='123'//修改输入框的值
```

2. 对于单多选框：

```javascript
//对于单选框，多选框等等固定的值，
boy_radio.value//只能取到当前的值;
boy_radio.checked//查看返回的结果，如果为true，则被选中
boy_radio.checked=true;//赋值
```

3. 表单提交验证：

1. 表单绑定提交事件：

2. 1. 格式：

   2. 1. <form action<> onsubmit="return 验证方法()">

   3. 作用：

   4. 1. 通过验证方法来验证表单，确定发不发送

1. 前端密码MD5加密：

   1. 方法一：

   2. 1. pwd.value=md5(pwd.value)
      2. 缺点：在提交的一瞬间密码会变长，且加密性不够。

   2. 方法二（推荐）：

```javascript
<input type="hidden" id="md5-password" name="password">
    md5pwd.value=md5(pwd,value);
```

 说明：在password中不用加name属性，在md5-password中加入，这样请求就只会捕捉到md5-password。

## JQuery

### JQuery选择器

1. 选择器：

   <img src="D:\JAVAMD\JavaScript.assets\image-20200808152830391.png" alt="image-20200808152830391" style="zoom:50%;" />

2. 格式：$('选择器').事件;

> [选择器参考文档](onenote:https://d.docs.live.net/4e489f56363392dd/文档/高宇 的笔记本/狂神说Java/JavaScrip最新教程通俗易懂.one#JQuery选择器&section-id={B6A230CE-2E18-40C1-9FD5-F03634ED9460}&page-id={E0FF5F6F-685A-4F39-85A4-58EA2DF26715}&object-id={982AE74F-B5AC-478A-ACCB-369C63BE007D}&2E) ([Web 视图](https://onedrive.live.com/view.aspx?resid=4E489F56363392DD!203&id=documents&wd=target(狂神说Java%2FJavaScrip最新教程通俗易懂.one|B6A230CE-2E18-40C1-9FD5-F03634ED9460%2FJQuery选择器|E0FF5F6F-685A-4F39-85A4-58EA2DF26715%2F)))

### JQuery事件

1. 当网页加载完毕之后，响应事件

2. 1. 格式：$(function() {        } );

2. 鼠标事件:<img src="D:\JAVAMD\JavaScript.assets\image-20200808153301186.png" alt="image-20200808153301186" style="zoom:50%;" />

### 操作Dom元素

- 节点文本操作：

  ```javascript
  $('#test-ul li[name=python]').text();//获得值
  $('#test-ul li[name=python]').text('设置值');//设置值
  ```

- css操作：使用css事件，参数为键值对

```javascript
$('#test_ul li[class=li2]').css({"font-family":"楷书","color":"red"});
```

- 元素的隐藏和显示：

1. - 本质：display:none

2. ```javascript
   $('#test-ul li[name=python]').show()
   $('#test-ul li[name=python]').hide()
   ```

3. 