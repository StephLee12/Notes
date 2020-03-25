- [Javascript Rookie Learning](#javascript-rookie-learning)
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
    - [Object](#object)
      - [Standard Object](#standard-object)
      - [Date](#date)
      - [JSON](#json)
    - [OOP](#oop)
    - [Explorer Object](#explorer-object)
      - [DOM](#dom)
      - [Form(表单)](#form%e8%a1%a8%e5%8d%95)
      - [File](#file)

# Javascript Rookie Learning

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

👉 注意执行JavaScript总是单线程执行，执行多任务实际上都是**异步调用**