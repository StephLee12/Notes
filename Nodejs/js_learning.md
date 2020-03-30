- [JavaScript Rookie Learning](#javascript-rookie-learning)
  - [JS的同步和异步](#js%e7%9a%84%e5%90%8c%e6%ad%a5%e5%92%8c%e5%bc%82%e6%ad%a5)
    - [JS的单线程](#js%e7%9a%84%e5%8d%95%e7%ba%bf%e7%a8%8b)
    - [JS的同步 异步](#js%e7%9a%84%e5%90%8c%e6%ad%a5-%e5%bc%82%e6%ad%a5)
    - [JS的异步机制](#js%e7%9a%84%e5%bc%82%e6%ad%a5%e6%9c%ba%e5%88%b6)
    - [JS异步编程](#js%e5%bc%82%e6%ad%a5%e7%bc%96%e7%a8%8b)
      - [回调函数](#%e5%9b%9e%e8%b0%83%e5%87%bd%e6%95%b0)
      - [Promise](#promise)
  - [Quick Start](#quick-start)
    - [Basic Grammer](#basic-grammer)
      - [Case](#case)
      - [Loop](#loop)
      - [Map](#map)
      - [Iterable](#iterable)
    - [Data Type and Variable](#data-type-and-variable)
      - [String](#string)
      - [Array](#array)
      - [Object(对象)](#object%e5%af%b9%e8%b1%a1)
    - [Function](#function)
      - [Define a function](#define-a-function)
      - [Function Domain](#function-domain)
      - [Method](#method)
    - [Arrow Funtion](#arrow-funtion)
    - [Object](#object)
      - [Standard Object](#standard-object)
      - [Date](#date)
      - [JSON](#json)
    - [OOP](#oop)
    - [Explorer Object](#explorer-object)
      - [DOM](#dom)
      - [Form(表单)](#form%e8%a1%a8%e5%8d%95)
      - [File](#file)
      - [AJAX(Asynchronous JavaScript and XML)](#ajaxasynchronous-javascript-and-xml)
  - [jQuery](#jquery)
    - [Selector(选择器)](#selector%e9%80%89%e6%8b%a9%e5%99%a8)
      - [Descendant Selector(层级选择器)](#descendant-selector%e5%b1%82%e7%ba%a7%e9%80%89%e6%8b%a9%e5%99%a8)
      - [Find and Filt(查找和过滤)](#find-and-filt%e6%9f%a5%e6%89%be%e5%92%8c%e8%bf%87%e6%bb%a4)
    - [jQuery_DOM](#jquerydom)
    - [Event](#event)
    - [AJAX](#ajax)
  - [Error Handling](#error-handling)
  - [underscore](#underscore)
    - [Collections(集合类)](#collections%e9%9b%86%e5%90%88%e7%b1%bb)
    - [underscore_array](#underscorearray)
  - [Node.js](#nodejs)
    - [Basic Module](#basic-module)
      - [fs](#fs)
      - [stream](#stream)
      - [http](#http)
      - [crypto](#crypto)
    - [Web开发](#web%e5%bc%80%e5%8f%91)
      - [koa](#koa)
        - [Express](#express)
        - [koa 1.0](#koa-10)
        - [koa2](#koa2)
          - [Handling URL](#handling-url)
          - [Nunjucks](#nunjucks)
          - [MVC(Modek-View-Controller)](#mvcmodek-view-controller)
      - [mysql](#mysql)
      - [Use ORM Sequelize](#use-orm-sequelize)
      - [Build Model](#build-model)
    - [WebSocket](#websocket)
    - [REST(Representational State Transfer)](#restrepresentational-state-transfer)
      - [Write REST API](#write-rest-api)

# JavaScript Rookie Learning

## JS的同步和异步

### JS的单线程

👉 JS引擎是一个事件驱动的执行引擎，**事件驱动**和**计通中套接字的select好像**

👉 JS是**单线程的**，即同一时间有多个任务，这些任务需要排队，前一个任务执行完才能执行下一个。

```javascript
// 同步代码
function fun1() {
  console.log(1);
}
function fun2() {
  console.log(2);
}
fun1();
fun2();

// 输出
1
2
```

输出会依次输出1,2，代码依次执行，执行完``fun1()``,才会执行``fun2()``。但如果``fun1()``中的代码执行的是**读取文件或AJAX操作**(耗时)，这样会造成执行效率很低。

但是JS单线程是必要的，作为浏览器的脚本语言，主要实现与用户的交互，可以对DOM进行操作。如果是多线程，一个线程要删除一个DOM结点，另一个线程要在该结点中添加内容，会出现矛盾。

### JS的同步 异步

👉 同步任务——**主线程上排队执行的任务，只有前一个任务执行完毕，才能继续执行下一个任务**。如打开网站时，网页的渲染过程，就是一个同步任务

👉 异步任务——**不进入主线程，而进入任务队列的任务，只有任务队列通知主线程，某个异步任务可以执行了，且主线程空闲，该任务才会进入主线程**。如打开网站时，图片的加载，音乐的加载，就是异步任务。如下``setTimeout()``就是一个异步任务

```javascript
function fun1() {
  console.log(1);
}
function fun2() {
  console.log(2);
}
function fun3() {
  console.log(3);
}
fun1();
setTimeout(function(){
  fun2();
},0);
fun3();

// 输出
1
3
2
```

### JS的异步机制

👉上面说的任务队列，虽然任务会被加入进队列，**但任务不是先进先出的，因为先进的任务完成的时间可能晚于后进的任务**。实际上它是一个**事件队列**，当一个异步任务完成之后，在任务队列里添加一个事件(表示该异步任务完成)

👉 如文件读取操作，这是一个异步任务，会被添加到任务队列，IO完成后，就会添加表示该异步任务完成的事件

👉 某一异步任务对应的事件添加到队列后，就可以进行执行栈，但是主线程可能还在执行同步任务，只有当主线程空闲时，才会读取任务队列，**读取里面的事件，排在前面的事件会被优先处理**，如果该任务指定了回调函数，那么主线程处理该事件时，就会执行回调函数中的代码，

👉 主线程在任务队列中读取任务是不断循环的，执行栈清空后，会在任务队列读取新任务，如果没有任务(是指该任务还没有被事件触发)，就会等待，直到有新的任务，称为**任务循环**，又因为每个任务都是由一个事件触发的，也称为**事件循环**

### JS异步编程

#### 回调函数

👉 在使用AJAX时候用的很多

```javascript
var req = new XMLHttpRequest();
req.open("GET",url);
req.send(null);
req.onreadystatechange=function(){}
```

``req.send()``方法是AJAX发送请求，是一个异步任务。``req.onreadystatechange()``是事件回调，借由``send()``方法发送请求得到响应之后触发的**请求完成事件**，将回调函数推入事件队列等待执行

👉 但回调这种方法不太符合思考的链式(顺序)思维，会出现**回调地狱**

#### Promise

👉 [看B乎](https://zhuanlan.zhihu.com/p/26523836)

👉 基本用法

```javascript
let p = new Promise((resolve, reject) => {
  // 做一些事情
  // 然后在某些条件下resolve，或者reject
  if (/* 条件随便写^_^ */) {
    resolve()
  } else {
    reject()
  }
})

p.then(() => {
    // 如果p的状态被resolve了，就进入这里
}, () => {
    // 如果p的状态被reject
})
```

👉 第一段代码调用了``Promise``构造函数，第二段调用了``promise``实例的``then()``方法

关于第一段代码

- 构造函数接受一个函数作为参数
- 调用构造函数得到实例``p``的同时，作为参数的函数会立即执行
- 参数函数接收两个**回调函数的参数``resolve``和``reject``**
- 在参数函数被执行的过程中，如果在其内部调用``resolve``,会将实例``p``的状态变成``fullfilled``，若调用的是``reject``,会将实例``p``的状态变成``rejected``

关于第二段代码

- 调用``then()``可以为实例``p``**注册两种状态函数
- 当实例``p``的状态是``fullfilled``，触发第一个函数执行
- 实例``p``的状态是``rejected``，触发第二个函数执行

👉 基本工作模式

- 将异步过程转化成``Promise``对象，对象有三种状态``pending fullfilled rejected``,初始的状态都是``pending``,而且只能由``pending``向其他两种状态转化
- 通过``then()``注册状态的回调函数
- 已完成的状态能够触发回调

## Quick Start

### Basic Grammer

👉 赋值语句 ``var x = 1``

👉 注释``//``,块注释``/* */``

#### Case

```javascript
    var age = 20;
    if (age >= 18){
        alert('adult')
    } else{
        alert('teenager')
    }
```

#### Loop

```javascript
    var x = 0;
    var i;
    for(i=1; i <= 10000; i++){
        x += i;
    }
    x = 0;
    var n = 99;
    while(n>0){
        x += n;
        n -= 2;
    }
```

#### Map

```javascript
    var m = new Map([['Micheal',95],['Bob',75],['Tracy', 85]]); // 相当于一个二维列表
    m.get('Michael')
```

```javascript
    var m = new Map();
    m.set('Micheal',95)
```

#### Iterable

Array,Map都属于可迭代的类型

对于可迭代的类型可以使用``for ... of ```循环来遍历(Python使用``for ... in ```)

也可以用``iterable``内置的``forEach``方法，**它接收一个函数，每次迭代就自动回调该函数

```javascript
    var a = ['A','B','C'];
    a.forEach(function (elem,index,arr) {
        //function中是arr回调函数的三个参数
        //elem 是当前元素的值
        //index 是当前索引
        //arr 指向array对象本身
        console.log(elem + ',index = ', + index);
    })
```

### Data Type and Variable

👉 比较运算符中判断相等用 ``===``，``!==``

👉 获取一个对象的属性用 ``对象变量.属性名``的方式

#### String

👉 获取字符串长度``s.length``

👉 字符串是不可变的，不能对某个索引赋值

#### Array

👉 获取数组长度``arr.length()``

👉 可以通过索引修改array

👉 获取array切片``arr,slice(a,b) //a-b 左闭右开``

👉 ``push()``在array尾部添加元素，``pop()``将array最后一个元素删除掉

👉 ``unshift()``在array头部添加元素，``shift()``删除array的第一个元素

👉 ``concat()``将两个array拼接

```javascript
    var arr = [1,2,3];
    var add_arr = arr.concat([4,5,6]);
```

👉 ``join()``将array中的每个元素用指定的字符串连接起来，然后返回连接的字符串

```javascript
    var arr = ['A','B',1,2];
    arr.join('-')
```

#### Object(对象)

```javascript
    var persion ={
        name : 'Bob',
        age : 20,
        city : 'Linyi'
    }
```

### Function

#### Define a function

```javascript
    function abs(x) {
        if(x >= 0) {
            return x;
        } else {
            return -x;
        }
    }
```

下面这一种方式类似于lambda表达式,``function (x) {...}``是一个匿名函数，这个匿名函数赋值给了变量``abs``，所以通过变量``abs``就可以调用该函数。

👉注意要在函数体末尾加上``;``，表示赋值语句的结束

```javascript
    var abs = function (x) {
        if (x >= 0){
            return x;
        } else{
            return -x;
        }
    };
```

👉 function中有一个``arguments``关键字，常用来判断参数的传入个数``arguments.length``

👉 为了获得要传入参数之外的参数，引入了``rest``

```javascript
    function foo(a,b, ...rest){
        console.log(rest);
    }
```

#### Function Domain

👉 全局变量被绑定到``window``这个object上

👉 关于局部作用域的变量，在``for``循环等语句块中无法定义此种变量，因此引入了``let``

```javascript
    function foo() {
        var sum = 0;
        for (let i = 0 ; i < 100; i++) {
            sum += i;
        }
        return sum;
    }
```

#### Method

```javascript
    var att = {
        name: 'Steph',
        birth: 2000,
        age: function() {
            var y = new Date().getFullYear();
            return y - this.birth; //this指向的是att这个对象
        }
    };
    //age()就是一个方法
    att.age(); //调用
```

### Arrow Funtion

👉 相当于匿名函数

```javascript
var fn = x => x* x; //等价于下面的函数
function (x) {
    return x * x;
}
```

### Object

#### Standard Object

```javascript
    typeof 123; // 'number'
    typeof NaN; // 'number'
    typeof 'str'; // 'string'
    typeof true; // 'boolean'
    typeof undefined; // 'undefined'
    typeof Math.abs; // 'function'
    typeof null; // 'object'
    typeof []; // 'object'
    typeof {}; // 'object'
```

👉 用``parseInt()``或``parseFloat()``来转换任意类型到``number``

👉 用``String()``来转换任意类型到``string``,或直接调用某个对象的``toString()``方法

👉 判断某个全局变量是否存在用``typeof windows.myVar === 'undefined'``

#### Date

```javascript
    var now = new Date();
    now; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
    now.getFullYear(); // 2015, 年份
    now.getMonth(); // 5, 月份，注意月份范围是0~11，5表示六月
    now.getDate(); // 24, 表示24号
    now.getDay(); // 3, 表示星期三
    now.getHours(); // 19, 24小时制
    now.getMinutes(); // 49, 分钟
    now.getSeconds(); // 22, 秒
    now.getMilliseconds(); // 875, 毫秒数
    now.getTime(); // 1435146562875, 以number形式表示的时间戳
```

#### JSON

👉 JSON是一种数据交换格式

👉 JSON实际上是JavaScript的子集，JSON中的数据类型有以下几种：``number boolean string null array object``

👉 JSON的字符集必须是UTF-8。为了统一解析，JSON的字符串必须用双引号，``object``的key也必须用双引号

👉 JavaScript内置了JSON解析，要把任何JavaScript对象变成JSON，把这个对象序列化成一个JSON格式的字符串，通过网络传递给其他计算机。收到JSON格式的字符串，反序列化为JavaScript对象

```javascript
    var xiaoming = {
    name: '小明',
    age: 14,
    gender: true,
    height: 1.65,
    grade: null,
    'middle-school': '\"W3C\" Middle School',
    skills: ['JavaScript', 'Java', 'Python', 'Lisp']
    };
    var s = JSON.stringify(xiaoming,null,' ');//序列化 第二个参数null可以传入函数，这样对象的每个key-value会被函数优先处理
    console.log(s);
```

👉序列化后的JSON字符串如下图所示![序列化](Captures\1.PNG "序列化")

👉关于反序列化

```javascript
    JSON.parse('[1,2,3,true]'); // [1, 2, 3, true]
    JSON.parse('{"name":"小明","age":14}'); // Object {name: '小明', age: 14}
    JSON.parse('true'); // true
    JSON.parse('123.45'); // 123.45
```

👉下面这段代码要注意看![2](Captures\2.PNG "2") 注意匿名函数怎么用的 ``JSON.parse()``可以接收一个函数

### OOP

👉 与经典面向对象编程语言如Python，Java不同的是，JavaScript没有类和实例的概念(**在ES6之后引入了``class`` **)，所有的对象都是实例，继承关系只是**把一个对象的原型(prototype)指向另一个对象**

```javascript
    var Student = {
        name: 'Robot',
        height: 1.2,
        run: function () {
            console.log(this.name + ' is running...');
        }
    };

    var xiaoming = {
        name: '小明'
    };

    xiaoming.__proto__ = Student;//将xiaoming的原型指向Student
```

👉 但是在写代码的时候别**直接用``obj.__proto__``去改变一个对象的原型，可以用``Object.create()``方法传入一个原型对象，并创建一个该原型的新对象

```javascript
    // 原型对象:
    var Student = {
        name: 'Robot',
        height: 1.2,
        run: function () {
            console.log(this.name + ' is running...');
        }
    };

    function createStudent(name) {
        // 基于Student原型创建一个新对象:
        var s = Object.create(Student);
        // 初始化新对象:
        s.name = name;
        return s;
    }

    var xiaoming = createStudent('小明');
    xiaoming.run(); // 小明 is running..
```

👉 创建对象也可以用函数的方法，但是在调用的时候在函数前面添加``new``关键字，前面说过``new``是将任何一种数据类型转换为``object``

👉内心OS：没有class 继承起来 也太麻烦了吧

👉 用``class``创建对象

```javascript
    class Student {
        constructor(name) {
            this.name = name;
        }

        hello() {
            alert('Hello, ' + this.name + '!');
        }
    }
    var xiaoming = new Student('小明');
    xiaoming.hello();
```

### Explorer Object

👉 ``windows``对象不仅充当全局作用域，而且表示浏览器窗口，有``innerWidth innerHeight``属性(像素为单位)，可以获取浏览器窗口的内部宽度和高度。**内部宽高是指除去菜单栏、工具栏、边框等占位元素后，用于显示网页的净宽高**。有``outerWidth outerHeight``属性获取整个浏览器窗口的整个宽高

👉 ``navigator``对象表示浏览器的信息

```javascript
    navigator.appName //浏览器名称
    navigator.appVersion //浏览器版本
    navigator.language //浏览器语言
    navigator.platform // 操作系统类型
    navigator.userAgent //浏览器设定的User-Agent字符串
```

👉 ``screen``对象表示屏幕的信息 ``screen.size``表示屏幕的大小

👉 ``location``对象表示当前页面的URL信息，通过``location.href``获取。

👉 ``document``对象表示当前页面。HTML在浏览器中以DOM形式表示为**树形结构**，``document``对象就是整个DOM树的根结点

``document.title``是从HTML中``<title>xxx</title>``读取的

要查找DOM树的某个结点，即要从树根``document``对象开始查找，最常用的查找是根据**ID和Tag Name**

```html
<dl id="drink-menu" style="border:solid 1px #ccc;padding:6px;">
    <dt>摩卡</dt>
    <dd>热摩卡咖啡</dd>
    <dt>酸奶</dt>
    <dd>北京老酸奶</dd>
    <dt>果汁</dt>
    <dd>鲜榨苹果汁</dd>
</dl>
```

用``document.getElementById()``和``document.getElementsByTagName()``分别可以按ID获得一个DOM结点和按Tag获得一组DOM结点

```javascript
    var menu = document.getElementById('drink-menu');
    var drinks = document.getElementsByTagName('dt');
    var i, s;

    s = '提供的饮料有:';
    for (i=0; i<drinks.length; i++) {
        s = s + drinks[i].innerHTML + ',';
    }
    console.log(s);
```

得到的结果为``提供的饮料有:摩卡，酸奶，果汁，``

#### DOM

👉 由于HTML文档被浏览器解析后就是一棵DOM树，操作一个DOM节点实际上就是对于树的操作：**更新，遍历，添加，删除**

👉 ID在HTML中是唯一的，``document.getElementById()``可以直接定位唯一的一个DOM结点。还有常用的方法是``document.getElementByTagName()``和CSS选择器``document.getElementByClassName()``,后面两种方法会返回一组DOM结点

```javascript
    // 返回ID为'test'的节点：
    var test = document.getElementById('test');

    // 先定位ID为'test-table'的节点，再返回其内部所有tr节点：
    var trs = document.getElementById('test-table').getElementsByTagName('tr');

    // 先定位ID为'test-div'的节点，再返回其内部所有class包含red的节点：
    var reds = document.getElementById('test-div').getElementsByClassName('red');

    // 获取节点test下的所有直属子节点:
    var cs = test.children;

    // 获取节点test下第一个、最后一个子节点：
    var first = test.firstElementChild;
    var last = test.lastElementChild;
```

👉 获取DOM结点还可以通过``querySelector()``和``querySelectorAll()``

```javascript
// 通过querySelector获取ID为q1的节点：
var q1 = document.querySelector('#q1');

// 通过querySelectorAll获取q1节点内的符合条件的所有节点：
var ps = q1.querySelectorAll('div.highlighted > p');
```

👉 修改DOM结点

第一种是修改``innerHTML``属性，可以设置HTML标签

```javascript
  // 获取<p id="p-id">...</p>
  var p = document.getElementById('p-id');
  // 设置文本为abc:
  p.innerHTML = 'ABC'; // <p id="p-id">ABC</p>
  // 设置HTML:
  p.innerHTML = 'ABC <span style="color:red">RED</span> XYZ';
  // <p>...</p>的内部结构已修改
```

第二种是修改``innerText``或``textContent``属性，但无法设置HTML标签

对于修改CSS，DOM结点的``style``属性对应所有的CSS，可以直接获取和设置

```javascript
// 获取<p id="p-id">...</p>
var p = document.getElementById('p-id');
// 设置CSS:
p.style.color = '#ff0000';
p.style.fontSize = '20px';
p.style.paddingTop = '2em';
```

👉 插入DOM结点

如果DOM结点是空的，如``<div></div>``，则直接使用``innerHTML = '<span>child</span>'``就可以修改DOM内容

如果DOM结点不为空，有两种方法插入新的结点

👉一个是``appenChild``，但这种方法把一个结点添加到父结点的**最后一个子结点**

```html
<!-- HTML结构 -->
<p id="js">JavaScript</p>
<div id="list">
    <p id="java">Java</p>
    <p id="python">Python</p>
    <p id="scheme">Scheme</p>
</div>
```

要把``<p id="js">JavaScript</p>``添加到``<div id="list">``的最后一个子结点

```javascript
var
    js = document.getElementById('js'),
    list = document.getElementById('list');
list.appendChild(js);
```

但更多的时候会从零创建一个结点，然后插入指定位置

```javascript
var
    list = document.getElementById('list'),
    haskell = document.createElement('p');
haskell.id = 'haskell';
haskell.innerText = 'Haskell';
list.appendChild(haskell);
```

操作之后的HTML结构为

```html
<!-- HTML结构 -->
<div id="list">
    <p id="java">Java</p>
    <p id="python">Python</p>
    <p id="scheme">Scheme</p>
    <p id="haskell">Haskell</p>
</div>
```

👉另一种插入结点的方法——插入指定的位置 使用``parentElement.insertBefore(newElement,referenceElement)``

对于上面的HTML结构，若要把``Haskell``插入到``Python``之前

```javascript
var
    list = document.getElementById('list'),
    ref = document.getElementById('python'),
    haskell = document.createElement('p');
haskell.id = 'haskell';
haskell.innerText = 'Haskell';
list.insertBefore(haskell, ref);
```

👉 删除DOM结点

要删除一个DOM结点，既要获得该结点又要获得其父结点，然后调用父结点``removeChild``

```javascript
// 拿到待删除节点:
var self = document.getElementById('to-be-removed');
// 拿到父节点:
var parent = self.parentElement;
// 删除:
var removed = parent.removeChild(self);
```

注意：删除后的结点虽然不在HTML的DOM树中，但是它还在内存中

#### Form(表单)

表单也是DOM树，表单的输入框、下拉框可以接收用户输入，HTML表单的输入控件主要有以下几种

👉 文本框 ``<input type="text">`` 用于输入文本

👉 口令框 ``<input type="password">`` 用于输入口令

👉 单选框 ``<input type="radio">`` 用于选择一项

👉 复选框 ``<input type="checkbox">`` 用于选择多项

👉 下拉框 ``<select>`` 用于选择一项

👉 隐藏文本 ``<input type="hidden">`` 用户不可见，但表单提交时会把隐藏文本发送到服务器

👉获取``<input>``结点的值，用``input.value``,这种方式可以用于``text password hidden select``,但是对于单选框和复选框，``input.value``返回的是HTML的预设值，我们要做的只是**确定用户是否“勾选”**，要用``input.checked``判断

```javascript
// <label><input type="radio" name="weekday" id="monday" value="1"> Monday</label>
// <label><input type="radio" name="weekday" id="tuesday" value="2"> Tuesday</label>
var mon = document.getElementById('monday');
var tue = document.getElementById('tuesday');
mon.value; // '1'
tue.value; // '2'
mon.checked; // true或者false
tue.checked; // true或者false
```

👉 设置值，对于``text password hidden select``，直接设置``value``即可，对于单选框和复选框，设置``checked``为``true``或``false``即可

👉 提交表单有两种方式

一是通过``<form>``元素的``submit()``方法提交一个表单

```html
<!-- HTML -->
<form id="test-form">
    <input type="text" name="test">
    <button type="button" onclick="doSubmitForm()">Submit</button>
</form>

<script>
function doSubmitForm() {
    var form = document.getElementById('test-form');
    // 可以在此修改form的input...
    // 提交form:
    form.submit();
}
</script>
```

这种方法的缺点是**扰乱了浏览器对``form``的正常提交**，浏览器默认点击``button``时提交表单

第二种方法是响应``<form>``本身的``onsubmit``事件，(没太看懂),``return true``来告诉浏览器继续提交，``return false``则浏览器不会提交``<form>``,这种情况对应用户输入有误

```html
<!-- HTML -->
<form id="test-form" onsubmit="return checkForm()">
    <input type="text" name="test">
    <button type="submit">Submit</button>
</form>

<script>
function checkForm() {
    var form = document.getElementById('test-form');
    // 可以在此修改form的input...
    // 继续下一步:
    return true;
}
</script>
```

👉 保障安全性，要充分利用``<input type="hidden">``来传递数据。例如，在提交表单时不传输明文口令，而是口令的MD5

```html
<!-- HTML -->
<form id="login-form" method="post" onsubmit="return checkForm()">
    <input type="text" id="username" name="username">
    <input type="password" id="input-password">
    <input type="hidden" id="md5-password" name="password">
    <button type="submit">Submit</button>
</form>

<script>
function checkForm() {
    var input_pwd = document.getElementById('input-password');
    var md5_pwd = document.getElementById('md5-password');
    // 把用户输入的明文变为MD5:
    md5_pwd.value = toMD5(input_pwd.value);
    // 继续下一步:
    return true;
}
</script>
```

上面的代码中``id``为``md5-password``的``<input>``标记了``<name>``属性，而``id``为``input-password``的``<input>``没有``<name>``属性，没有``<name>``属性的数据不会被提交

#### File

👉 在``<form>``中，可以上传文件的唯一控件是``<input type="file">``

👉 当表单包含``file``控件时，表单的``enctype``必须指定为``multipart/form-data``,``method``必须指定为``post``

👉 注意执行JavaScript总是单线程执行，执行多任务实际上都是**异步调用**。因为是异步操作，在JavaScript中不知道操作什么时候结束，因此要**设置一个回调函数**，当异步操作完成后，JavaScript引擎自动调用回调函数。[关于JS异步看此B乎](https://zhuanlan.zhihu.com/p/30630902) [也可看这个BLOG](https://www.cnblogs.com/Yellow-ice/p/10433423.html)

#### AJAX(Asynchronous JavaScript and XML)

👉 上文的链接。

👉 写AJAX主要依靠``XMLHttpRequest``对象

```javascript
function success(text) {
    var textarea = document.getElementById('test-response-text');
    textarea.value = text;
}

function fail(code) {
    var textarea = document.getElementById('test-response-text');
    textarea.value = 'Error code: ' + code;
}

var request = new XMLHttpRequest(); // 新建XMLHttpRequest对象

request.onreadystatechange = function () { // 状态发生变化时，函数被回调
    if (request.readyState === 4) { // 成功完成
        // 判断响应结果:
        if (request.status === 200) {
            // 成功，通过responseText拿到响应的文本:
            return success(request.responseText);
        } else {
            // 失败，根据响应码判断失败原因:
            return fail(request.status);
        }
    } else {
        // HTTP请求还在继续...
    }
}

// 发送请求:
request.open('GET', '/api/categories');
request.send();

alert('请求已发送，请等待响应...');
```

👉 ``XMLHttpRequest``对象的``open()``方法有三个参数，第一个参数指定``GET``还是``POST``；第二个参数指定URL地址；第三个参数指定是否使用异步，默认是``true``

👉 最后调用``send()``方法才**真正发送请求**，``GET``请求不需要参数，``POST``请求需要把body部分以字符串或``FormData``对象传进去

👉 ``send()``方法是AJAX向服务器发送数据，**它是一个异步任务**，将请求交给浏览器的HTTP请求线程发起对服务器的请求，JS的主线程继续向下执行代码(如果执行栈中还有代码)

👉 ``request.onreadystatechange``属于事件回调，在请求抢得到响应之后出发请求完成事件，将该事件添加到任务队列，当JS主线程空闲之后，会执行该事件的回调函数

👉 当创建``XMLHttpRequest``对象后，要先设置``onreadystatechange``的回调函数。在回调函数中通过``readyState === 4``判断请求是否完成，如果已完成，再根据``status === 200``判断是否是一个成功的响应

👉 上述代码中URL使用的是相对路径，如果改为``http://www.sina.com.cn/``,会报错，这是浏览器的**同源策略**导致的。默认情况下，JS在发送AJAX请求时，URL的域名必须和当前页面完全一致(域名相同(``www.example.com``和``example.com``不同)，协议相同(``http``和``https``不同)，端口相同(默认是``:80``端口)) 若想通过JS访问外域的URL，方法如下

- **JSONP** 但是它只能用``GET``请求，并且要求返回JS。这种方法实际是利用了浏览器允许跨域引用JS资源。先准备好JSONP要调用的函数，然后给页面动态加一个``<script>``结点，相当于动态读取外域的JS资源，最后等着接收回调

```javascript
function refreshPrice(data) {
    var p = document.getElementById('test-jsonp');
    p.innerHTML = '当前价格：' +
        data['0000001'].name +': ' +
        data['0000001'].price + '；' +
        data['1399001'].name + ': ' +
        data['1399001'].price;
}
function getPrice() {
    var
        js = document.createElement('script'),
        head = document.getElementsByTagName('head')[0];
    js.src = 'http://api.money.126.net/data/feed/0000001,1399001?callback=refreshPrice';
    head.appendChild(js);
}
```

👉 但如果浏览器支持H5(现在没有浏览器不支持H5吧)，可以使用**CORS(Cross-Origin Resource Sharing)**,这是H5定义的如何跨域访问资源

Origin表示浏览器当前页面的域。当JS向外域发起请求后，浏览器收到响应后，**首先检查``Access-Control-Allow-Origin``是否包含Origin。如果是，跨域请求成功；如果不是，请求失败

所以，跨域能否成功，取决于**对方服务器是否给当前域一个``Access-Control-Allow-Origin``

## jQuery

👉 使用jQuery只需要在页面的``<head>``引入jQuery文件

```html
<html>
<head>
    <script src="//code.jquery.com/jquery-1.11.3.min.js"></script>
</head>
<body>
    ...
</body>
</html>
```

👉 **\$符号**：jQuery把所有功能全部封装在一个**全局变量jQuery**中 ``$``是``jQuery``的别名

### Selector(选择器)

👉 jQuery的核心，类型``getElementById()``之类的，为了帮助我们快速定位到一个或多个DOM结点

👉 按ID查找

```javascript
// 查找<div id="abc">:
var div = $('#abc');
```

返回的对象是**jQuery对象**。以👆为例，如果``id``为``abc``的``<div>``存在，返回的jQuery对象如👇,如果不存在，返回``[]``

```javascript
[<div id="abc">...</div>]
```

jQuery对象和DOM对象之间可以相互转化，通常情况下使用jQuery对象更方便

```javascript
var div = $('#abc'); // jQuery对象
var divDom = div.get(0); // 假设存在div，获取第1个DOM元素
var another = $(divDom); // 重新把DOM包装为jQuery对象
```

👉 按tag查找 如查找所有``<p>``结点 ``var ps = $('p');``

👉 按class查找 要在class名称前加一个``.`` 若同时查找包含``red``和``green``的结点  ``var a = $('.red.green')``

👉 也可以按照其他属性查找

#### Descendant Selector(层级选择器)

👉 如果两个DOM元素由层级关系，可以用``$('ancestor descendant')来选择

```html
<!-- HTML结构 -->
<div class="testing">
    <ul class="lang">
        <li class="lang-javascript">JavaScript</li>
        <li class="lang-python">Python</li>
        <li class="lang-lua">Lua</li>
    </ul>
</div>
```

若要选出``JavaScript``,``<div>``和``<ul>``都是``<li>``的祖先结点

```javascript
$('ul.lang li.lang-javascript'); // [<li class="lang-javascript">JavaScript</li>]
$('div.testing li.lang-javascript'); // [<li class="lang-javascript">JavaScript</li>]
```

#### Find and Filt(查找和过滤)

👉 查找

```html
<!-- HTML结构 -->
<ul class="lang">
    <li class="js dy">JavaScript</li>
    <li class="dy">Python</li>
    <li id="swift">Swift</li>
    <li class="dy">Scheme</li>
    <li name="haskell">Haskell</li>
</ul>
<script>
var ul = $('ul.lang'); // 获得<ul>
var dy = ul.find('.dy'); // 获得JavaScript, Python, Scheme
var swf = ul.find('#swift'); // 获得Swift
var hsk = ul.find('[name=haskell]'); // 获得Haskell
</script>
```

### jQuery_DOM

👉 修改Text和HTML

```html
<!-- HTML结构 -->
<ul id="test-ul">
    <li class="js">JavaScript</li>
    <li name="book">Java &amp; JavaScript</li>
</ul>
<script>
//get text and html
var j1 = $('#test-ul li.js');
var j2 = $('#test-ul li[name=book]');
//set text and html
j1.html('<span style="color: red">JavaScript</span>');
j2.text('JavaScript & ECMAScript');
</script>
```

👉 添加DOM

用``append()`` ``prepend()``方法，先得到父结点，然后调用``append()``传入HTML片段

```html
<div id="test-div">
    <ul>
        <li><span>JavaScript</span></li>
        <li><span>Python</span></li>
        <li><span>Swift</span></li>
    </ul>
</div>
<script>
var ul = $('#test-div>ul');
ul.append('<li><span>Haskell</span></li>');
</script>
```

👉 删除DOM

调用``remove()``方法

### Event

👉 在异步机制说过，一旦页面上的所有JavaScript代码被执行完后，就只能依赖**触发事件来执行JS代码**

👉 浏览器在接收到用户的鼠标或键盘输入后，**会自动在对应的DOM结点上触发相应的事件**，如果该结点已经**绑定**了对应的**JS处理函数**，该函数就会自动调用,如👇绑定一个``click``
事件

```html
<a id = "test-link" href="#0">嘤嘤嘤</a>

<script>
var a = $('test-link');
a.click(function () {
    alert('hello!');
})
</script>
```

👉 鼠标事件

- ``click``：鼠标单击时触发
- ``dblclick``: 鼠标双击时触发
- ``mouseenter``: 鼠标进入时触发
- ``mouseleave``：鼠标移出时触发
- ``mousemove``：鼠标在DOM内部移动时触发
- ``hover``: 鼠标进入和退出时触发两个函数

👉 键盘事件——仅作用在当前焦点的DOM上 通常是``<input>``和``<textarea>``

- ``keydown``: 键盘按下时触发
- ``keyup``: 键盘松开时触发
- ``keypress``: 按一次键后触发

👉 其他事件

- ``focus``: 当DOM获取焦点时触发
- ``blur``: 当DOM失去焦点时触发
- ``change``: 当``<input> <select>或<textarea>``的内容发生改变时触发
- ``submit``: 当``<form>``提交时触发
- ``ready``: 当页面被载入且DOM树完成初始化后触发

``ready``仅作用于``document``对象，由于``ready``事件在DOM完成初始化后触发，且只触发一次，**所以非常适合写其他初始化代码**，如👇

```html
<html>
<head>
    <script>
        $(document).ready(function () {
            $('#testForm').submit(function() {
                alert('submit!');
            });
        });
    </script>
</head>
<body>
    <form id = "testform"></form>
</body>
```

上的JS代码甚至可以再简化为👇，这种写法最常见

```javascript
$(function () {
    //init ....
})
```

👉 取消绑定 ``off('event',function)``

```javascript
function hello() {
    alert('hello!');
}

a.click(hello); // 绑定事件

// 10秒钟后解除绑定:
setTimeout(function () {
    a.off('click', hello);
}, 10000);
```

👉 事件触发条件

事件的触发总是由用户操作引发，如监控文本框的内容改动👇

```javascript
var input = $('#test-input');
input.change(function () {
    console.log('changed...');
});
```

当用户在文本框中输入，会触发``change``事件。但是！！！，如果用JS代码去改动文本框的值，不会触发``change``事件，如👇

```javascript
var input = $('#test-input');
input.val('change it!'); // 无法触发change事件
```

可以这样改动，👇``input.change()``相当于``input.trigger('change')``

```javascript
var input = $('#test-input');
input.val('change it!');
input.change(); // 触发change事件
```

### AJAX

👉 jQuery在全局对象``jQuery``中绑定了``ajax()``函数，可以处理AJAX请求。``ajax(url,settings)``函数需要接收一个URL和一个可选的对象。对象中选项如👇

- ``async``: 是否异步执行AJAX请求，默认``true``
- ``method``：缺省为``'GET'``,可指定为``'POST','PUT'``
- ``contentType``：发送``POST``请求的格式
- ``data``: 发送到数据
- ``headers``:发送额外的HTTP头
- ``dataType``: 接收数据的格式

👉 jQuery的jqXHR对象类似一个Promise对象，如👇

```javascript
function ajaxLog(s) {
    var txt = $('#test-response-text');
    txt.val(txt.val() + '\n' + s);
}

$('#test-response-text').val('');
var jqxhr = $.ajax('/api/categories', {
    dataType: 'json'
}).done(function (data) {
    ajaxLog('成功, 收到的数据: ' + JSON.stringify(data));
}).fail(function (xhr, status) {
    ajaxLog('失败: ' + xhr.status + ', 原因: ' + status);
}).always(function () {
    ajaxLog('请求完成: 无论成功或失败都会调用');
});
```

👉 ``get()``方法，👇

```javascript
var jqxhr = $.get('/path/to/resource', {
    name: 'Bob Lee',
    check: 1
});
```

👉 ``post()``方法 👇

```javascript
var jqxhr = $.post('/path/to/resource', {
    name: 'Bob Lee',
    check: 1
});
```

👉 ``getJSON()``方法来快速通过GET获取一个JSON对象

```javascript
var jqxhr = $.getJSON('/path/to/resource', {
    name: 'Bob Lee',
    check: 1
}).done(function (data) {
    // data已经被解析为JSON对象了
});
```

## Error Handling

👉 ``try...catch..finally`` 被``try {...}``包裹的代码块表示这部分代码执行中可能会发生错误，**一旦发生错误，就不执行后面的代码，转而跳到``catch``块``,``catch (e) {...}``包裹的代码就是错误处理代码，变量``e``表示捕获到的错误。``finally {...}``一定会被执行

```javascript
var r1, r2, s = null;
try {
    r1 = s.length; // 此处应产生错误
    r2 = 100; // 该语句不会执行
} catch (e) {
    console.log('出错了：' + e);
} finally {
    console.log('finally');
}
console.log('r1 = ' + r1); // r1应为undefined
console.log('r2 = ' + r2); // r2应为undefined
```

👉 程序可以主动抛出一个错误，用``throw``语句，让执行流程直接跳转到``catch``块

```javascript
var r, n, s;
try {
    s = prompt('请输入一个数字');
    n = parseInt(s);
    if (isNaN(n)) {
        throw new Error('输入错误');
    }
    // 计算平方:
    r = n * n;
    console.log(n + ' * ' + n + ' = ' + r);
} catch (e) {
    console.log('出错了：' + e);
}
```

👉 异步错误处理

如👇，不会捕捉到错误

```javascript
function printTime() {
    throw new Error();
}

try {
    setTimeout(printTime, 1000);
    console.log('done');
} catch (e) {
    console.log('error');
}

```

## underscore

👉 underscore提供一套完善的函数式编程接口

👉 把自身绑定到唯一的全局变量``_``

### Collections(集合类)

👉 underscore为集合类(Array和Object)对象提供一致的接口

👉 ``map() filter()``

```javascript
var obj = {
    name: 'bob',
    school: 'No.1 middle school',
    address: 'xueyuan road'
};

var test = _.map(obj, function (key, value){
    //..do something
})
```

👉 ``some() every()`` 当集合中所有元素都满足条件``every()``返回``true``.当集合中至少一个元素满足条件``some()``返回``true``

👉 ``max() min()`` 若作用于Object，则只对value有效

👉 ``groupBy()`` 把集合的元素按照key归类

```javascript
var scores = [20, 81, 75, 40, 91, 59, 77, 66, 72, 88, 99];
var groups = _.groupBy(scores, function (x) {
    if (x < 60) {
        return 'C';
    } else if (x < 80) {
        return 'B';
    } else {
        return 'A';
    }
});
// 结果:
// {
//   A: [81, 91, 88, 99],
//   B: [75, 77, 66, 72],
//   C: [20, 40, 59]
// }
```

### underscore_array

👉 ``first() last()`` 分别取第一个和最后一个元素

👉 ``flatten()`` 接收一个Array，将其变为一个一维数组

👉 ``range()`` 快速生成一个序列

## Node.js

👉 在执行JS代码的时候，要以严格模式运行,可以在第一行写上``'use strict'``,也可直接在终端输入``node --use_strict file_name.js``

👉 在Node环境中，一个js文件就称为一个模块(module)。模块名就是去掉``.js`` 👇是如何在一个模块中调用另一个模块的函数

```javascript
// hello.js
'use strict';

var s = 'Hello';

function greet(name) {
    console.log(s + ', ' + name + '!');
}

module.exports = greet;
```

注意，最后一行语句，要将函数``greet()``作为模块的输出暴露出去，这样别的模块就可以使用``greet()``函数

```javascript
'use strict';

// 引入hello模块:
var greet = require('./hello');

var s = 'Michael';

greet(s); // Hello, Michael!
```

引入模块用Node提供的``require``函数，👆 ``greet``就是hello.js文件中的``module.exports``

这个模块加载机制称为**CommonJS规范**

### Basic Module

👉 Nodejs环境有一个唯一的全局对象``global``

👉 ``process``对象代表当前Nodejs的进程

#### fs

👉 ``fs``模块是文件系统模块，负责读写文件

👉 异步读取时，传入的回调函数接收两个参数 正常读取时 ``err===null``,``data``读取到的为String

```javascript
'use strict';

var fs = require('fs');
//sample.txt文件必须在工作目录下，且文件编码是utf-8
fs.readFile('sample.txt', 'utf-8', function (err, data) {
    if (err) {
        console.log(err);
    } else {
        console.log(data);
    }
});
```

👉 当读取的文件不是文本文件，而是二进制文件，回调函数的``data``将返回一个``Buffer``对象。在Nodejs中，``Buffer``对象就是一个包含任意个子节的数组

```javascript
'use strict';

var fs = require('fs');

fs.readFile('sample.png', function (err, data) {
    if (err) {
        console.log(err);
    } else {
        console.log(data);
        console.log(data.length + ' bytes');
    }
});
```

``Buffer``对象可以和String转换，如👇

```javascript
// Buffer -> String
var text = data.toString('utf-8');
console.log(text);

// String -> Buffer
var buf = Buffer.from(text, 'utf-8');
console.log(buf);
```

👉 写文件 ``fs.writeFile()``实现，参数依次是文件名，数据和回调函数。如果传入的数据是String，默认按uft-8编码，如果传入参数是``Buffer``，写入的是二进制的文件

```javascript
'use strict';

var fs = require('fs');

var data = 'Hello, Node.js';
fs.writeFile('output.txt', data, function (err) {
    if (err) {
        console.log(err);
    } else {
        console.log('ok.');
    }
});
```

👉 获取文件大小，创建事件等信息 ``fs.stat()``

```javascript
'use strict';

var fs = require('fs');

fs.stat('sample.txt', function (err, stat) {
    if (err) {
        console.log(err);
    } else {
        // 是否是文件:
        console.log('isFile: ' + stat.isFile());
        // 是否是目录:
        console.log('isDirectory: ' + stat.isDirectory());
        if (stat.isFile()) {
            // 文件大小:
            console.log('size: ' + stat.size);
            // 创建时间, Date对象:
            console.log('birth time: ' + stat.birthtime);
            // 修改时间, Date对象:
            console.log('modified time: ' + stat.mtime);
        }
    }
});
```

#### stream

👉 ``stream``是nodejs提供的仅在服务端可用的模块，是为了支持"流"这种数据结构

👉 ``data``事件表示流的数据可以读取，``end``事件表示流已经到了末尾，没有数据可读，``error``事件表示出错。初始化一个读取流``fs.createReadStream('file','coding')``

```javascript
'use strict';

var fs = require('fs');

// 打开一个流:
var rs = fs.createReadStream('sample.txt', 'utf-8');

rs.on('data', function (chunk) {
    console.log('DATA:')
    console.log(chunk);
});

rs.on('end', function () {
    console.log('END');
});

rs.on('error', function (err) {
    console.log('ERROR: ' + err);
});
```

``data``事件可能会有很多次，每次传递的``chunk``是流的一部分数据

👉 以流的形式写入文件，不断调用``write()``方法，最后以``end()``结束

```javascript
'use strict';

var fs = require('fs');

var ws1 = fs.createWriteStream('output1.txt', 'utf-8');
ws1.write('使用Stream写入文本数据...\n');
ws1.write('END.');
ws1.end();

var ws2 = fs.createWriteStream('output2.txt');
ws2.write(new Buffer('使用Stream写入二进制数据...\n', 'utf-8'));
ws2.write(new Buffer('END.', 'utf-8'));
ws2.end();
```

👉 ``pipe()``类似于linux中的管道，将数据从一个流输入到另一个流

```javascript
'use strict';

var fs = require('fs');

var rs = fs.createReadStream('sample.txt');
var ws = fs.createWriteStream('copied.txt');

rs.pipe(ws);
```

#### http

👉 ``request``对象封装了HTTP请求，调用``request``对象的属性和方法就可以拿到所有**HTTP请求的信息**

👉 ``response``对象封装了HTTP响应，操作``response``对象的方法，就可以把HTTP响应返回给浏览器 👇是一个HTTP服务器的程序,它对于所有请求，都返回``Hello World!``

```javascript
'use strict';

// 导入http模块:
var http = require('http');

// 创建http server，并传入回调函数:
var server = http.createServer(function (request, response) {
    // 回调函数接收request和response对象,
    // 获得HTTP请求的method和url:
    console.log(request.method + ': ' + request.url);
    // 将HTTP响应200写入response, 同时设置Content-Type: text/html:
    response.writeHead(200, {'Content-Type': 'text/html'});
    // 将HTTP响应的HTML内容写入response:
    response.end('<h1>Hello world!</h1>');
});

// 让服务器监听8080端口:
server.listen(8080);

console.log('Server is running at http://127.0.0.1:8080/');
```

之后在终端node环境下运行该js文件，之后打开浏览器输入``http://127.0.0.1:8080``即可看到``Hello World``

👉 若要将上面的程序变为一个**文件服务器**，只需要解析``request.url``中的路径，然后再本地找到对应的文件，把文件内容发送即可

解析URL要用到``url``模块，通过``parse()``将一个字符串解析为一个``url``对象

```javascript
'use strict';

var url = require('url');

console.log(url.parse('http://user:pass@host.com:8080/path/to/file?query=string#hash'));

//解析结果如下
Url {
  protocol: 'http:',
  slashes: true,
  auth: 'user:pass',
  host: 'host.com:8080',
  port: '8080',
  hostname: 'host.com',
  hash: '#hash',
  search: '?query=string',
  query: 'query=string',
  pathname: '/path/to/file',
  path: '/path/to/file?query=string',
  href: 'http://user:pass@host.com:8080/path/to/file?query=string#hash' }
```

处理本地文件目录要使用``path``模块,可以处理服务器端文件的路径

```javascript
'use strict';

var path = require('path');

// 解析当前目录:
var workDir = path.resolve('.'); // '/Users/michael'

// 组合完整的文件路径:当前目录+'pub'+'index.html':
var filePath = path.join(workDir, 'pub', 'index.html');
// '/Users/michael/pub/index.html'
```

完整的代码如👇，其中没必要手动读取文件内容，因为``response``对象是一个``Writable Stream``,直接用``pipe()``方法就实现了自动读取文件内容并输出到HTTP响应

```javascript
//file_server.js
'use strict';

var path = require('path');

// 解析当前目录:
var workDir = path.resolve('.'); // '/Users/michael'

// 组合完整的文件路径:当前目录+'pub'+'index.html':
var filePath = path.join(workDir, 'pub', 'index.html');
// '/Users/michael/pub/index.html'
```

```javascript
'use strict';

var
    fs = require('fs'),
    url = require('url'),
    path = require('path'),
    http =  require('http');

var root = path.resolve(process.argv[2] || '.'); //获取root目录(从命令行获取) 默认是当前目录 ||是比较运算符

console.log('Static root dir: ' + root);

var server = http.createServer(function (request , response) {
    //获取URL的path
    var path_name = url.parse(request.url).pathname;
    //获取对应的本地文件路径
    var filepath = path.join(root, pathname);
    //获取文件状态
    fs.stat(filepath, function (err, stats) {
        if (!err && stats.isFile()) {
            //没有报错且文件存在
            console.log('200 '+ request.url);
            //发送200响应
            response.writeHead(200);
            //将文件流导向response
            fs.createReadStream(filepath).pipe(response);
        } else{
            //报错或文件不存在
            console.log('404 ' + request.url);
            //发送404响应
            response.writeHead(404);
            response.end('404 Not Found');
        }
    });
});

server.listen(8080);

console.log('Server is running at http://127.0.0.1:8080');
```

👆要从命令行获取文件的目录，在终端node环境下输入``node file_server.js /path/to/dir``，其中``/path/to/dir``是存放文件的目录，只要在当前目录下存在文件``index.html``,在浏览器中输入``http://localhost:8080/index.html``,服务器就可以把文件内容发送给浏览器，控制台输出如👇

```javascript
200 /index.html
200 /css/uikit.min.css
200 /js/jquery.min.js
200 /fonts/fontawesome-webfont.woff2
```

#### crypto

👉 ``crypto``模块是提供通用的加密和哈希算法

👉 MD5 SHA... 👇``'md5'``可以改成``'sha1' 'sha256'``等

```javascript
const crypto = require('crypto');

const hash = crypto.createHash('md5');

// 可任意多次调用update():
hash.update('Hello, world!');
hash.update('Hello, nodejs!');

console.log(hash.digest('hex')); // 7e1977739c748beac0c0fd14fd26a544
```

### Web开发

#### koa

👉 koa是Express的下一代基于nodejs的web框架

##### Express

👉 对nodejs的http进行了封装，但是问题在于实现异步代码只有一个方法——回调。会出现回调地狱

##### koa 1.0

👉 使用generator实现异步

##### koa2

👉 koa2完全使用Promise且配合``async``和``await``实现异步

👉 关于安装koa 在工作目录下 在终端执行``npm install koa@2.0.0``

完整的用koa写的小程序👇

```javascript
// 导入koa，和koa 1.x不同，在koa2中，我们导入的是一个class，因此用大写的Koa表示:
const Koa = require('koa');

// 创建一个Koa对象表示web app本身:
const app = new Koa();

// 对于任何请求，app将调用该异步函数处理请求：
app.use(async (ctx, next) => {
    await next();
    ctx.response.type = 'text/html';
    ctx.response.body = '<h1>Hello, koa2!</h1>';
});

// 在端口3000监听:
app.listen(3000);
console.log('app started at port 3000...');
```

```javascript
app.use(async (ctx, next) => {
    await next();
    var data = await doReadFile();
    ctx.response.type = 'text/plain';
    ctx.response.body = data;
});
```

👉 由``async``标记的函数称为异步函数，在异步函数中，可以用``await``调用另一个异步函数

👉 参数``ctx``是koa传入的封装了``request``和``response``的变量，``next``是koa传入的将要处理的下一个异步函数

👉 每收到一个http请求，koa就会调用通过``app.use()``注册的``async``函数，并传入``ctx``和``next``参数

👉 为什么在``async``函数中还要调用另一个异步函数``await next()`` 👇

koa把很多``async``函数组成一个**处理链**，每个``async``函数都可以做自己要做的事情，然后用``await next()``来调用下一个``async``函数，把每个``async``函数称为**middleware**，这些middleware可以组合起来，如👇

```javascript
app.use(async (ctx, next) => {
    console.log(`${ctx.request.method} ${ctx.request.url}`); // 打印URL
    await next(); // 调用下一个middleware
});

app.use(async (ctx, next) => {
    const start = new Date().getTime(); // 当前时间
    await next(); // 调用下一个middleware
    const ms = new Date().getTime() - start; // 耗费时间
    console.log(`Time: ${ms}ms`); // 打印耗费时间
});

app.use(async (ctx, next) => {
    await next();
    ctx.response.type = 'text/html';
    ctx.response.body = '<h1>Hello, koa2!</h1>';
});
```

###### Handling URL

👉 👆👆的koa2小程序，输入任何的URL，都会返回相同的网页，其实应该对不同的URL调用不同的处理函数

👉 引入了``koa-router``这个middleware，负责URL的映射 用``npm install koa-router``

```javascript
const Koa  =require('koa');

// 若只是require('koa-router') 返回的是函数
const router = require('koa-router')();

const app = new Koa();

// log request URL:
app.use(async (ctx, next) => {
    console.log(`Process ${ctx.request.method} ${ctx.request.url}...`);
    await next();
});

// add url-route
router.get('/hello/:name', async (ctx, next) => {
    var name = ctx.params.name;
    ctx.response.body = `<h1>Hello, ${name}!</h1>`;
});

router.get('/', async (ctx, next) => {
    ctx.response.body = `<h1>Index</h1>`;
});

// add router middleware:
app.use(router.routes());

app.listen(3000);
console.log('app started at port 3000...');
```

👉 使用``router.get('/path', async fn)``来注册一个GET请求。可以在请求路径中使用带变量的``/hello/:name``，变量可以通过``ctx.params.name``访问

👉 处理post请求

👆 ``router.get('/path',async fn)``处理的是get请求，若要处理post请求，用``router.post('/path', async fn)``

post请求通常会发送一个表单，或者JSON，它作为request的body发送，但是nodejs提供的原始request对象，还是koa提供的request对象，都不提供解析request的body的功能，👇

引入另一个middleware来解析原始request请求，然后把解析后的参数，绑定到``ctx.request.body``上，👉``koa-bodyparser`` 安装——``npm install koa-bodyparser``

middleware的顺序很重要，``koa-bodyparser``必须在``router``之前被注册到``app``对象上

下面是一段处理post请求的代码

```javascript
router.get('/', async (ctx, next) => {
    ctx.response.body = `<h1>Index</h1>
        <form action="/signin" method="post">
            <p>Name: <input name="name" value="koa"></p>
            <p>Password: <input name="password" type="password"></p>
            <p><input type="submit" value="Submit"></p>
        </form>`;
});

router.post('/signin', async (ctx, next) => {
    var
        name = ctx.request.body.name || '',
        password = ctx.request.body.password || '';
    console.log(`signin with name: ${name}, password: ${password}`);
    if (name === 'koa' && password === '12345') {
        ctx.response.body = `<h1>Welcome, ${name}!</h1>`;
    } else {
        ctx.response.body = `<h1>Login failed!</h1>
        <p><a href="/">Try again</a></p>`;
    }
});
```

类似的，put,delete,head请求也可以由``router``处理

👉 但如上的方式，太乱了。对代码进行重构。添加一个Controller Middleware 要看代码！！

###### Nunjucks

👉 模板引擎——基于模板配合数据构造出字符串输出的一个组件

如👇就是一个模板引擎

```javascript
function examResult (data) {
    return `${data.name}同学一年级期末考试语文${data.chinese}分，数学${data.math}分，位于年级第${data.ranking}名。`
}
```

模板引擎最常见的输出就是输出网页

###### MVC(Modek-View-Controller)

[多看几遍](https://www.liaoxuefeng.com/wiki/1022910821149312/1023026038570336)

👉 当用户通过浏览器请求一个URL时，koa将调用某个异步函数处理URL，在这个异步函数内部，用``ctx.render('home.html', { name: 'Michael' });``,通过Nunjucks把数据用指定模板渲染成HTML，然后输出给浏览器，如👇图所示![3](Captures\3.PNG "3")

👉 MVC中异步函数是C，负责业务逻辑，如见擦汗用户名是否存在，取出用户信息

👉 包含变量``{{ name }}``的模板就是V，负责显示逻辑，通过简单地替换一些变量，View最终输出的就是用户看到的HTML

👉 Model是用来传给View，View在替换变量时，从Model中取出相应的数据，👆中Model就是JS对象``{name :'Michael'}``

👉 处理首页GET / 在``./controller/index.js``中

```javascript
async (ctx, next) => {
    ctx.render('index.html', {
        title: 'Welcome'
    });
}
```

👉 处理登录请求 POST/signin

```javascript
async (ctx, next) => {
    var
        email = ctx.request.body.email || '',
        password = ctx.request.body.password || '';
    if (email === 'admin@example.com' && password === '123456') {
        // 登录成功:
        ctx.render('signin-ok.html', {
            title: 'Sign In OK',
            name: 'Mr Node'
        });
    } else {
        // 登录失败:
        ctx.render('signin-failed.html', {
            title: 'Sign In Failed'
        });
    }
}
```

登录成功时用``signin_ok.html``渲染，登录失败用``signin_failed.html``渲染。所以在``./view``中需要三个View：``index.html signin_ok.html signin_failed.html``

👉 编写View实际上就是写HTML，直接使用一个现成的框架——Bootstrap，将所有静态资源文件放到``./static``目录下。

所以需要一个middleware来处理以``/static/``开头的URL

``./static_file.js``中的``staticFiles``函数接收两个参数:URL前缀和一个目录，然后返回一个``async``函数，该函数会判断当前URL是否以指定前缀开头，如果是就发送文件内容。如果不是，这个函数不做事情，只是调用``await next()``——让下一个middleware去处理请求

使用处理静态文件的middleware只需在``app.js``中加上

```javascript
let staticFiles = require('./static-files');
app.use(staticFiles('/static/', __dirname + '/static'));
```

👉 集成Nunjucks也是编写一个middleware，这个middleware的作用是给``ctx``对象绑定一个``render(view, model)``的方法，之后Controller就可以调用这个方法来渲染模板。``./templating.js``实现这个middleware

在``app.js``中添加如下代码

```javascript
const isProduction = process.env.NODE_ENV === 'production';

app.use(templating('views', {
    noCache: !isProduction,
    watch: !isProduction
}));
```

定义了一个常量``isProduction``,判断当前环境是否是production环境。如果是，就使用缓存；如果不是，就关闭缓存。**在开发环境下，关闭缓存后，若修改View，可以直接刷新浏览器看到效果。否则，每次修改都要重启Node，会降低开发效率**

在全局变量``process``中定义了一个环境变量``NODE_ENV``。使用此变量是因为在开发环境下，该值应设置为``development``,部署到服务器，环境变量应设置为``'production'``。注意，**生产环境必须配置此变量，而开发环境不需要**

来编写处理静态文件的middleware时，可以如下编写

```javascript
if (! isProduction) {
    let staticFiles = require('./static-files');
    app.use(staticFiles('/static/', __dirname + '/static'));
}
```

这是因为在生产环境下，静态文件是由反向代理服务器(如Nginx)处理的，Node不需要处理。但是在**开发环境，我们希望koa能顺带处理静态文件，否则就要手动配置一个反向代理服务器**

👉 上面说过需要3个Views，可以编写一个``base.html``作为骨架，其他模板都继承``base.html``

👉 编写Middleware的时候要注意middleware的顺序。在示例工程``view_koa``中

- 第一个middleware是记录URL以及页面的执行时间

```javascript
app.use(async (ctx, next) => {
    console.log(`Process ${ctx.request.method} ${ctx.request.url}...`);
    var
        start = new Date().getTime(),
        execTime;
    await next();
    execTime = new Date().getTime() - start;
    ctx.response.set('X-Response-Time', `${execTime}ms`);
});
```

- 第二个处理静态文件

```javascript
if (! isProduction) {
    let staticFiles = require('./static-files');
    app.use(staticFiles('/static/', __dirname + '/static'));
}
```

- 第三个解析post请求

```javascript
app.use(bodyParser());
```

- 第四个为``ctx``绑定``render()``方法，以使用Nunjucks

```javascript
app.use(templating('view', {
    noCache: !isProduction,
    watch: !isProduction
}));
```

- 最后一个middleware处理URL路由

```javascript
app.use(controller());
```

#### mysql

👉 对于nodejs程序，访问mysql是通过网络发送SQL命令给mysql服务器，**访问mysql服务器的软件包称为mysql的驱动程序**，可以直接用``npm install mysql``安装

#### Use ORM Sequelize

👉 数据库是一个二维表，**每一行可以用一个JS对象表示**。这就是**ORM(Object-Relational Mapping)技术**——把关系数据库的表结构映射到对象上。ORM框架用来做这种转换

👉 选择Node的ORM框架**Sequelize**，可以将JS对象变换为数据库中的行

👉 若要查询某一个表，如``pets``表

```javascript
(async ()=> {
    var pets = await Pet.findAll();
})
```

👉 由于mysql各版本语法的不同，创建用户用``create user 'stephlee'@'localhost' identified by 'password';``,然后将``test``数据库授权给用户(若无``test``数据库 执行``create database test``)，执行``grant all privileges on test.* to 'stephlee'@'localhost';``

👉 先将工作目录下的``init,txt``复制到mysql命令行执行，然后执行``app.js``,工作目录下的``config.js``是一个配置文件

👉 实现

- 在``app.js``中先创建一个``sequelize``对象实例

```javascript
const Sequelize = require('sequelize');
const config = require('./config');

var sequelize = new Sequelize(config.database, config.username, config.password, {
    host: config.host,
    dialect: 'mysql',
    pool: {
        max: 5,
        min: 0,
        idle: 30000
    }
});
```

- 然后定义模型``Pet``，告诉``Sequelize``如何映射数据库表.用``sequelize.define()``定义Model

```javascript
var Pet = sequelize.define('pet', {
    id: {
        type: Sequelize.STRING(50),
        primaryKey: true
    },
    name: Sequelize.STRING(100),
    gender: Sequelize.BOOLEAN,
    birth: Sequelize.STRING(10),
    createdAt: Sequelize.BIGINT,
    updatedAt: Sequelize.BIGINT,
    version: Sequelize.BIGINT
}, {
        timestamps: false
    });
```

- 向数据库中添加数据

```javascript
(async () => {
    var dog = await Pet.create({
        id: 'd-' + now,
        name: 'Odie',
        gender: false,
        birth: '2008-08-08',
        createdAt: now,
        updatedAt: now,
        version: 0
    });
    console.log('created: ' + JSON.stringify(dog));
})();
```

- 查询数据

```javascript
(async () => {
    var pets = await Pet.findAll({
        where: {
            name: 'Gaffey'
        }
    });
    console.log(`find ${pets.length} pets:`);
    for (let p of pets) {
        console.log(JSON.stringify(p));
    }
})();
```

- 更新数据和删除数据分别调用``save()``和``destroy()``方法，详见代码

#### Build Model

👉 一个统一的模型，强迫所有Model都遵守同一个风格

👉 Rules

- Models存放的文件夹必须在``models``内，并且以Model名字命名
- 统一主键，名称必须是``id``,类型必须是``STRING(50)``
- 所有字段默认为``NOT NULL``
- 统一timestamp机制，每个Model必须有``createdAt updatedAt version``，分别记录创建时间，修改时间和版本号。前两个以``BIGINT``存储时间戳，``version``每次修改时自增

👉 About mysql

- 查看所有数据库``show databases``
- 查看用户``select host,user from mysql.user``
- 查看数据库中的表——``show tables``
- 查看表中的所有内容——``select * from table_name``

### WebSocket

👉 无限制的全双工通信

- WebSocket是利用HTTP协议来建立连接，连接必须**由浏览器发起**，格式如下

```txt
GET ws://localhost:3000/ws/chat HTTP/1.1
Host: localhost
Upgrade: websocket
Connection: Upgrade
Origin: http://localhost:3000
Sec-WebSocket-Key: client-random-string
Sec-WebSocket-Version: 13
```

GET请求的地址是以``ws://``开头的地址，请求头``Upgrade:websocket Connection:Upgrade``表示这个连接要被转换为WebSocket连接

- 如果服务器接收该请求，返回如下相应

```txt
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: server-random-string
```

响应代码``101``表示本次连接的HTTP协议即将被更改，更改后的协议就是``Upgrade``指定的WebSocket协议

### REST(Representational State Transfer)

👉 Web API的标准

👉 什么是Web API?

如果我们想要获取某个电商网站的某个商品，输入``http://localhost:3000/products/123``，就可以看到id为123的商品页面，但这个结果是HTML页面，它**同时混合包含了Product的数据和Product的展示两个部分**。对于用户来说，阅读起来没有问题，但是，如果机器读取，就**很难从HTML中解析出Product的数据**。

如果一个URL返回的不是HTML，而是**机器能直接解析的数据**，这个URL就可以看成一个Web API

所以REST就是一种设计API的模式，最常用的数据格式是JSON

#### Write REST API

👉 编写REST API，实际上就是编写处理HTTP请求的``async``函数，但是REST请求与普通的HTTP请求不同的是：

- 除GET请求外，其他请求``body``的格式是JSON格式，因此请求的``Content-Type``为``application/json``
- REST响应返回的结果是JSON格式，因此响应的``Content-Type``也是``application/json``

![4](Captures\4.PNG "4")

👉 用koa处理REST

在koa中处理REST请求是非常简单的。``bodyParser()``这个middleware可以解析请求的JSON数据并绑定到``ctx.request.body``上，输出JSON时我们先指定``ctx.response.type = 'application/json'``，然后把JavaScript对象赋值给``ctx.response.body``就完成了REST请求的处理。

👉 如何组织URL

以固定的前缀区分，``/static/``开头的URL是静态资源文件，``/api/``开头的URL是REST API，其他的URL是普通的MVC请求

👉 统一输出REST

参考集成Nunjucks，通过一个middleware给``ctx``添加一个方法，这里同样这样做——添加一个``rest()``方法