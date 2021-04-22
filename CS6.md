# nCS6

## 	1、let和const的认识

## 	2、模板字符串

```javascript
<script>
    var person={
        name:"何高宇",
        address:"湛江",
        link:"yingshang.com"  
    };
    var address="我叫"+person.name+"在"+person.address+"学习";
    var address1=`我叫${person.name}在${person.address}学习`;
    console.log(address);
    console.log(address1);
</script>
```

## 	3、默认参数

```javascript
<script>
    var sum = function (a=100,b=199){
    return a+b;
}
</script>
```

## 	4、箭头函数

```javascript
var sum = function(a,b){
    return a+b;
}
var sum = (a,b)=>{
    return a+b;
}
var  sum = (a,b)=>return a+b;
规律：
1、去掉function
2、括号后面加上箭头
3、若方法中只有一条return语句，可以之间省去大括号，直接加上return语句
```

## 	5、Symbol

格式：Symbol("描述")

```javascript
let name=Symbol("小明")
```

功能：返回一个独一无二的值，括号里面是对值得描述，用于区分。	

注意：用作属性对象得时候，用对象[]取出。

```javascript
let people{};
people[name]="小明";
```

Symbol.for("name"):

​    在一个单独的内存里面，找寻是否有name标记的symbol，如果有则返回该值，没用则创建并返回

```javascript
let yellow=Symbol.for("Yellow");
let yellow1=Symbol.for("Yellow");
yellow1===yellow  //false

let yellow2=Symbol.for("Yellow");
yellow2===yellow1 //true
```

Sysbol.keyFor("key"):

​      根据赋予的变量名查找是否有相同的

## 6、ES6的map和set

map的迭代：

```javascript
for(var [key,value] of myMap){}

for(var[key,value] of myMap.entries){}//安装插入顺序迭代

for(var key of myMap.keys()){}

for(var value of myMap.values){}

myMap.forEach(function(value,key){},myMap)
```

map对象的操作：

​	可以和Array对象转化，自身克隆合并

set：

和array对象转化，

两个set的并、交、差集合：

```javascript
var a = new Set([1, 2, 3]);
var b = new Set([4, 3, 2]);
var union = new Set([...a, ...b]); // {1, 2, 3, 4}
var intersect = new Set([...a].filter(x => b.has(x))); // {2, 3}
var difference = new Set([...a].filter(x => !b.has(x))); // {1}
```

## 7、Reflect and Proxy

Proxy:对某个对象进行代理，代理拦截其一些方法

Reflect:Object中的一写方法，对对象本身进行操作

## 8、拓展字符串操作

- 子串的识别：
  - **includes()**：返回布尔值，判断是否找到参数字符串。
  - **startsWith()**：返回布尔值，判断参数字符串是否在原字符串的头部。
  - **endsWith()**：返回布尔值，判断参数字符串是否在原字符串的尾部。
  - 注意：只可返回布尔，若要返回地址得用indexOf

- 字符串重复：
  - repeat()：返回新的字符串，表示将字符串重复指定次数返回。
- 字符串不全：
  - **padStart**：返回新的字符串，表示用参数字符串从头部（左侧）补全原字符串。
  - **padEnd**：返回新的字符串，表示用参数字符串从尾部（右侧）补全原字符串。

## 9、数组操作

Array.of():将参数里面的所有值作为元素形成数组

Array.from()：将可迭代对象转化成数组

转换可迭代对象：map，set，string

flat()：嵌套数组转化成一维数组

flatMap():先对数组中元素进行处理再执行flat方法

## 10、	Class类

类定义：

- 匿名类：

  ```javascript
  //匿名类
  let example = class{
  	constructor(a){
  		this.a=a;
  	}
  }
  //类的声明
  let Example = class Example{
      constructor(a){
          this.a=a;
      }
  }
  ```

- 静态属性：Example.prototype.a=2;