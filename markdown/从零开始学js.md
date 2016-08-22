# 快速入门
## Introduction
### What is javascript?
JavaScript 是一门跨平台、面向对象的轻量级脚本语言。 在主机环境中， JavaScript能够通过连接环境对象而实现可控制编译。  
JavaScript内置了一个包含一系列对象的标准库，比如数组，日期，数学和一个语言元素核心集合包括操作符，流程控制符以及语句等。JavaScript的核心部分可以通过组合已有语言核心对象来扩展语言以适应不同用途；例如：

- 客户端的JavaScript通过提供控制浏览器及其文档对象模型（DOM）的对象来扩展语言核心。例如：客户端版本直接支持应用将元素放在在HTML表单中并且支持响应用户事件比如鼠标点击、表单提交和页面导航。
- 服务端的JavaScript则通过提供有关在服务器上运行JavaScript的对象来可扩展语言核心。例如：服务端版本直接支持应用和数据库通信，提供应用不同调用间的信息连续性，或者在服务器上执行文件操作。
### javascript 和 java
JavaScript和Java有一些共性但是在另一些方面有着根本性区别。JavaScript酷似Java但是并没有Java的静态类型和强类型检查特性。JavaScript遵循了Java的表达式语法，命名规范以及基础流程控制，这也是JavaScript从LiveScript更名的原因。

与Java通过声明式构建类的编译时系统不同，JavaScript采用基于少量的数据类型如数字、布尔、字符串值的运行时系统。JavaScript拥有基于原型的对象模型提供的动态继承；也就是说，独立对象的继承是可以改变的。 JavaScript 支持匿名函数。 函数也可以作为对象的属性执行。

与Java相比，Javascript是一门形式自由的语言。你不必声明所有的变量，类和方法。你不必关心方法是否是 共有、私有或者受保护的，也不需要实现接口。无需显式指定变量、参数、方法返回值的数据类型。

Java是基于类的编程语言，设计的初衷就是为了快速执行和类型安全的。类型安全，举例来说，你不能将一个Java 整数变量 转化为一个对象引用，或者由Java字节码访问专有存储器。Java基于类的模型，意味着程序包含专有的类及其方法。Java的类继承和强类型要求紧耦合的对象层级结构。这些要求使得Java编程比JavaScript要复杂的多。

相比之下，JavaScript传承了HyperTalk和dBASE语句精简、动态类型等精髓，为更多开发者提供了一种语法简单、内置功能强大以及用最小需求创建对象的编程工具。
#### JavaScript 和 Java 的对比
JavaScript | java  
---|---  
面向对象。不区分对象类型。通过原型机制继承，任何对象的属性和方法均可以被动态添加。 | 基于类系统。分为类和实例，通过类层级的定义实现继承。不能动态增加对象或类的属性或方法。  
变量类型不需要提前声明(动态类型)。 | 变量类型必须提前声明(静态类型)。  
不能直接自动写入硬盘。 | 可以直接自动写入硬盘。  

## 语法和数据类型
### 基础知识(Basics)
avaScript 是大小写敏感的，使用 Unicode 字符集。

在JavaScript中，语句被称为 statements，并用分号分隔（;）。空格、制表符和换行符被称为空白。 
JavaScript的脚本的源文本从左到右扫描，并转换成由令牌，控制字符，行结束符，注释或空白组成的输入元素序列。  
ECMAScript中还定义了某些关键字和字面值，并具有分号自动插入功能（ASI）来结束语句。但是，建议随时添加分号结束你的语句以避免副作用。
### 注释(Comments)
注释语法与和许多其他语言相同：  
```  
// 单行注释
 
/* 这是一个多行注释 
   多行注释
 */
 
/* 但是, 你不能, /* 嵌套注释 */ 语法错误 */  
```  
### 声明(Declarations)
JavaScript有三种声明。

**var**
声明变量，可选择将其初始化为一个值。
**let**
声明块范围局部变量(block scope local variable)，可选择将其初始化为一个值。
**const**
声明一个只读(read-only)的有名字的常量。
#### 变量(Variables)
在应用程序中，使用变量来为值命名。变量的名称称为 identifiers，需要遵守一定的规则。

在 JavaScript 语言中，一个标识符(identifier)必须以字母、下划线（_）或者美元（$）符号开头；后续的字符可以包含数字（0-9）。因为 JavaScript 语言是区分大小写的，这里所指的字母可以是（大写的）“A”到“Z”和（小写的）“a”到“z”。

#### 声明变量(Declaring variables)

你可以用以下三种方式声明变量：

使用关键词 var。例如，var x = 42。这个语法可以同时用来声明局部和全局变量。
直接赋值。例如，x = 42。这样就声明了一个全局变量并会导致JavaScript编译时产生一个严格警告。因而你应避免使用这种非常规格式。
使用关键词let。例如，let y = 13。这个语法可以用来声明语句块代码段的局部变量(block scope local variable)。參考下方Variable scope 。
#### 对变量求值(Evaluating variables)

用 var 或 let 声明的未赋初值的变量，值会被设定为undefined（译注：即未定义值，本身也是一个值）。

试图访问一个未初始化的变量会导致一个 ReferenceError 异常被抛出：
```
var a;  
console.log("The value of a is " + a); // logs "的值未定义"  
console.log("The value of b is " + b); // 抛出ReferenceError异常  
```  
你可以使用undefined来确定变量是否已赋值。以下的代码中，变量input未被赋值，因而if条件语句的求值结果是true。

```
var input;
if(input === undefined){
  doThis();
} else {
  doThat();
}
```
undefined值在布尔类型环境中会被当作false。例如，下面的代码将运行函数myFunction，因为数组myArray中的元素未被赋值：

```
var myArray = new Array();
if (!myArray[0]) myFunction();
```
数值类型环境中undefined值会被转换为NaN（译注：NaN为“Not a Number”，不是一个数字 的缩写）。

```
var a;
a + 2; // Evaluates to NaN
```
当你对一个空变量求值时，空值 null 在数值类型环境中会被当作0来对待，而布尔类型环境中会被当作false。例如：

```
var n = null;
console.log(n * 32); // logs 0
```
#### 变量的域(Variable scope)

在所有函数之外声明的变量，叫做全局变量，因为它可被当前文档中的其他代码所访问。在函数内部声明的变量，叫做局部变量，因为它只能在该函数内部访问。

ECMAScript 6 之前的JavaScript没有 语句块 作用域；相反，语句块中声明的变量将成为语句块所在代码段的局部变量。例如，如下的代码将在控制台输出 5，因为 x 的作用域是声明了 x 的那个函数（或全局范围），而不是 if 语句块。

```
if (true) {
  var x = 5;
}
console.log(x); // 5
```
如果使用 ECMAScript 6 中的 let 声明，上述行为将发生变化。

```
if (true) {
  let y = 5;
}
console.log(y); // ReferenceError: y is not defined
```
#### 变量声明提升(Variable hoisting)

JavaScript 变量的另一特别之处是，你可以引用稍后声明的变量，而不会引发异常。这一概念称为变量声明提升(hoisting)；JavaScript 变量感觉上是被“提升”或移到了所有函数和语句之前。然而提升后的变量将返回 undefined 值，所以即使在使用或引用某个变量之后存在声明和初始化操作，这个被提升的引用仍将得到 undefined 值。

```
/**
 * Example 1
 */
console.log(x === undefined); // logs "true"
var x = 3;

/**
 * Example 2
 */
// will return a value of undefined
var myvar = "my value";

(function() {
  console.log(myvar); // undefined
  var myvar = "local value";
})();
```
上面的例子，也可写作：

```
/**
 * Example 1
 */
var x;
console.log(x === undefined); // logs "true"
x = 3;
 
/**
 * Example 2
 */
var myvar = "my value";
 
(function() {
  var myvar;
  console.log(myvar); // undefined
  myvar = "local value";
})();
```
由于存在变量声明提升，一个函数中所有的var语句应尽可能地放在接近函数顶部的地方。这大大地提升了程序代码的清晰度。
#### 全局变量(Global variables)

全局变量实际上是全局对象的属性。在网页中，（译注：缺省的）全局对象是 window，所以你可以用形如 window.variable的语法来设置和访问全局变量。

因此，你可以通过指定 window 或 frame 的名字，从一个 window 或 frame 访问另一个 window 或 frame 中声明的变量。例如，设想一个叫 phoneNumber 的变量在文档里被声明，你可以在子框架里用 parent.phoneNumber 来引用它。

#### 常量(Constants)
你可以用关键字 const 创建一个只读(read-only)的常量。常量标识符的命名规则和变量的相同：必须以字母、下划线或美元符号开头并可以包含有字母、数字或下划线。

const prefix = '212';
常量不可以通过赋值改变其值，也不可以在脚本运行时重新声明。它必须被初始化为某个值。

常量的作用域规则与 let 块级作用域变量相同。若const关键字被省略了，该标识符将被视为变量。

在同一作用域中，不能用与变量或函数同样的名字来命名常量。例如：

```
// THIS WILL CAUSE AN ERROR
function f() {};
const f = 5;

// THIS WILL CAUSE AN ERROR ALSO
function f() {
  const g = 5;
  var g;

  //statements
}
```
### 数据结构和类型
JavaScript语言可以识别下面 7 种不同类型的值：

- 六种是 原型 的数据类型:
  - Boolean.  布尔值，true 和 false.
  - null. 一个表明 null 值的特殊关键字。 JavaScript 是大小写敏感的，因此 null 与 Null、NULL或其他变量完全不同。
  - undefined.  变量未定义时的属性。
  - Number.  表示数字，例如： 42 或者 3.14159。
  - String.  表示字符串，例如："Howdy"
  - Symbol ( 在 ECMAScript 6 中新添加的类型).。一种数据类型，它的实例是唯一且不可改变的。
- 以及 Object 对象

仅凭这些为数不多的数据类型，在你的应用程序中它們就能够执行有用的功能。
Objects 和 functions 是本语言的其他两个基本要素。你可以将对象视为存放值的命名容器，而将函数视为你的应用程序能够执行的过程(procedures)。

#### 数据类型的转换(Data type conversion)

JavaScript是一种动态类型语言(dynamically typed language)。这意味着你声明变量时可以不必指定数据类型，而数据类型会在脚本执行需要时自动转换。那么，你可以这样来定义变量：

```
var answer = 42;
```
然后，你还可以给同一个变量分配一个字符串值，例如：

```
answer = "Thanks for all the fish...";
```
因为 JavaScript 是动态类型的，这样的指定并不会提示出错。

在涉及加法运算符(+)的数字和字符串表达式中，JavaScript 会把数字值转换为字符串。例如，假设有如下的语句：

```
x = "The answer is " + 42 // "The answer is 42"
y = 42 + " is the answer" // "42 is the answer"
```
在涉及其它运算符（译注：如下面的减号'-'）时，JavaScript语言不会把数字变为字符。例如（译注：第一例是数学运算，第二例是字符串运算）：

```
"37" - 7 // 30
"37" + 7 // "377"
```
##### 字符串转换为数字(converting strings to numbers)

有一些方法可以将内存中表示一个数字的字符串转换为对应的数字

parseInt()和parseFloat()

参见：parseInt()和parseFloat()的相关页面。

parseInt 仅能够返回整数，所以使用它会丢失小数部分。另外，调用 parseInt 时最好总是带上进制(radix) 参数，这个参数用于指定使用哪一种数制。

单目加法运算符

将字符串转换为数字的另一种方法是使用单目加法运算符。

```
"1.1" + "1.1" = "1.11.1"
(+"1.1") + (+"1.1") = 2.2   // 注：加入括号为清楚起见，不是必需的。
```
#### 字面值(Literals)EDIT
（译注：字面值是由语法表达式定义的常量；或，通过由一定字辞组成的语词表达式定义的常量）

在JavaScript中，你可以使用各种字面值。这些字面值是脚本中按字面意思给出的固定的值，而不是变量。（译注：字面值是常量，其值是固定的，而且在程序脚本运行中不可更改，比如false，3.1415，thisIsStringOfHelloworld ，invokedFunction: myFunction("myArgument")。本节将介绍以下类型的字面值：

- 数组字面值(Array literals)
- 布尔字面值(Boolean literals)
- 浮点数字面值(Floating-point literals)
- 整数(Intergers)
- 对象字面值(Object literals)
- RegExp literals
- 字符串字面值(String literals)
- 数组字面值(Array literals)

数组字面值是一个封闭在方括号对([])中的包含有零个或多个表达式的列表，其中每个表达式代表数组的一个元素。当你使用数组字面值创建一个数组时，该数组将会以指定的值作为它的元素进行初始化，而其长度被设定为元素的个数。

下面的示例用3个元素生成数组coffees，它的长度是3。

```
var coffees = ["French Roast", "Colombian", "Kona"];

var a=[3];

console.log(a.length); // 1

console.log(a[0]); // 3
```
注意 这里的数组字面值也是一种对象初始化器。参考对象初始化器的使用。
若在顶层（全局）脚本里用字面值创建数组，JavaScript语言会在每次对包含该数组字面值的表达式求值时解释该数组。另一方面，在函数中使用的数组，将在每次调用函数时被创建一次。

数组字面值同时也是数组对象。有关数组对象的详情请参见数组对象一文。

数组字面值中的多余逗号

（译注：声明时）你不必列举数组字面值中的所有元素。若你在同一行中连写两个逗号（,），数组中就会产生一个没被指定的元素，其初始值是undefined。以下示例创建了一个名为fish的数组：

```
var fish = ["Lion", , "Angel"];
```
这个数组中，有两个已被赋值的元素，和一个空元素（fish[0]是"Lion"，fish[1]是undefined，而fish[2]是"Angel"；译注：此时数组的长度属性fish.length是3)。

若你在元素列表的尾部添加了一个逗号，它会被忽略。在下面的例子中，该数组的长度是3。并不存在myList[3]这个元素（译注：这是指数组的第4个元素噢，作者是在帮大家复习数组元素的排序命名方法）。元素列表中所有其它的逗号都表示一个新元素（的开始）。

注意：尾部的逗号在早期版本的浏览器中会产生错误，因而编程时的最佳实践就是移除它们。
(译注：而“现代”的浏览器似乎鼓励这种方式，因为好多网页中都这么写？)

```
var myList = ['home', , 'school', ];
```
在下面的例子中，数组的长度是4，元素myList[0]和myList[2]缺失（译注：没被赋值，因而是undefined）。

```
var myList = [ , 'home', , 'school'];
```
又一个例子，在这里该数组的长度是4，元素myList[1]和myList[3]被漏掉了。（但是）只有最后的那个逗号被忽略。

```
var myList = ['home', , 'school', , ];
```
理解多余的逗号（在脚本运行时会被如何处理）的含义，对于从语言层面理解JavaScript是十分重要的。但是，你自己写代码时：显式地将缺失的元素声明为undefined，将大大增加你的代码的清晰度和可维护性。（译注：此段话的重要性甚至超过整篇文章。译者：还有为啥不举例说明呢？）

##### 布尔字面值(Boolean literals)

（译注：即逻辑字面值）

布尔类型有两种字面值：true和false。

不要混淆作为布尔对象的真和假与布尔类型的原始值true和false。布尔对象是原始布尔数据类型的一个包装器。参见 布尔对象。

##### 整数(Intergers)

（译注：原文如此，没写成“整数字面值”）

整数可以被表示成十进制（基数为10）、十六进制（基数为16）以及八进制（基数为8）。

十进制整数字组成的数字序列，不带前导0。
带前导0、0O、0o 的整数字面值表明它是八进制。八进制整数只能包括数字0-7。
前缀0x或0X表示十六进制。十六进制整数，可以包含数字（0-9）和字母a~f或A~F。
八进制整数字面值在ECMA-262，第3版标准（严格模式下） 中被弃用并移除。不过JavaScript 1.5为了后向兼容仍然保留了支持。

整数字面值例子如下：

0, 117 and -345 (decimal, base 10)
015, 0001 and -077 (octal, base 8) 
0x1123, 0x00111 and -0xF1A7 (hexadecimal, "hex" or base 16)
##### 浮点数字面值(Floating-point literals)

浮点数字面值可以有以下的组成部分：

一个十进制整数，它可以带符号（即前面的“+”或“ - ”号），
一个小数点（“.”），
一个小数部分（由一串十进制数表示），
一个指数部分。
指数部分是以“e”或“E”开头后面跟着一个整数，可以有正负号（即前面写“+”或“-”）。一个浮点数字面值必须至少有一位数字，后接小数点或者“e”（大写“E”也可）组成。

一些浮点数字面值的例子，如3.1415，-3.1E13，.1e12以及2E-12。

简言之，其语法是：

[(+|-)][digits][.digits][(E|e)][(+|-)]digits]
例如：

```
3.14      
-.2345789 // -0.23456789
-3.12e+12  // -3.12*1012
.1e-23    // 0.1*10-23=10-24=1e-24
```
##### 对象字面值(Object literals)

对象字面值是封闭在花括号对({})中的一个对象的零个或多个"属性名-值"对的（元素）列表。你不能在一条语句的开头就使用对象字面值，这将导致错误或非你所预想的行为，因为此时左花括号（{）会被认为是一个语句块的起始符号。（译者：这 里需要对语句statement、块block等基本名词的解释）

以下是一个对象字面值的例子。对象car的第一个元素（译注：即一个属性双值对）定义了属性myCar；第二个元素，属性getCar，引用了一个函数（即CarTypes("Honda")）；第三个元素，属性special，使用了一个已有的变量（即Sales）。

```
var Sales = "Toyota";

function CarTypes(name) {
  return (name === "Honda") ?
    name :
    "Sorry, we don't sell " + name + "." ;
}

var car = { myCar: "Saturn", getCar: CarTypes("Honda"), special: Sales };

console.log(car.myCar);   // Saturn
console.log(car.getCar);  // Honda
console.log(car.special); // Toyota
```
更进一步的，你可以使用数字或字符串字面值作为属性的名字，或者在另一个字面值内嵌套上一个字面值。如下的示例中使用了这些可选项。

```
var car = { manyCars: {a: "Saab", "b": "Jeep"}, 7: "Mazda" };

console.log(car.manyCars.b); // Jeep
console.log(car[7]); // Mazda
```
对象属性名字可以是任意字符串，包括空串。如果对象属性名字不是合法的javascript标识符，它必须用""包裹。属性的名字不合法，那么便不能用.访问属性值，而是通过类数组标记("[]")访问和赋值。

```
var unusualPropertyNames = {
  "": "An empty string",
  "!": "Bang!"
}
console.log(unusualPropertyNames."");   // 语法错误: Unexpected string
console.log(unusualPropertyNames[""]);  // An empty string
console.log(unusualPropertyNames.!);    // 语法错误: Unexpected token !
console.log(unusualPropertyNames["!"]); // Bang!
```
请注意：

```
var foo = {a: "alpha", 2: "two"};
console.log(foo.a);    // alpha
console.log(foo[2]);   // two
//console.log(foo.2);  // Error: missing ) after argument list
//console.log(foo[a]); // Error: a is not defined
console.log(foo["a"]); // alpha
console.log(foo["2"]); // two
```
在ES2015，对象文本扩展到支持在原型设置建造，简写foo：foo分配，界定方法，得到很好的名称，并与表达式计算属性名。总之，这些也带来了对象文字和类声明紧密联系起来，让基于对象的设计得益于一些同样的便利。

```
var obj = {
    // __proto__
    __proto__: theProtoObj,
    // Shorthand for ‘handler: handler’
    handler,
    // Methods
    toString() {
     // Super calls
     return "d " + super.toString();
    },
    // Computed (dynamic) property names
    [ 'prop_' + (() => 42)() ]: 42
};
```
##### RegExp 字面值

一个正则表达式是字符被斜线围成的表达式。下面是一个正则表达式文字的一个例子。

```
var re = /ab+c/;
```
##### 字符串字面值(String literals)

字符串字面值可以包含有零个或多个字符，由双引号（"）对或单引号（‘）对包围。字符串被限定在同种引号之间；也即，必须是成对单引号或成对双引号。下面的例子都是字符串字面值：

```
"foo"
'bar'
"1234"
"one line \n another line"
"John's cat"
```
你可以在字符串字面值上使用字符串对象的所有方法——JavaScript会自动将字符串字面值转换为一个临时字符串对象，调用该方法，然后废弃掉那个临时的字符串变量。你也能用对字符串字面值使用类似String.length的属性：

```
"John's cat".length
```
除非有特别需要使用字符串对象，否则,你应当始终使用字符串字面值。要查看字符串对象的有关细节，请参见字符串对象。

在字符串中使用的特殊字符

作为一般字符的扩展，你可以在字符串中使用特殊字符，如下例所示。

```
"one line \n another line"
```
以下表格列举了你能在JavaScript的字符串中使用的特殊字符。

 

表 2.1 JavaScript 特殊字符

Character |	Meaning
---|---
      \0	| 空字节
      \b	| 退格
      \f	| 换页符
      \n	| 换行符
      \r	| 回车符
      \t	| Tab(制表符)
      \v	| 垂直制表符
      \'	| 单引号
      \"	| 双引号
      \\	| 反斜杠字符（\）。
    \XXX	| 通过最多三个八进制位数×377。例如在0和指定的Latin-1编码的字符，\251是版权符号八进制序列。
    \xXX	| 由00和FF之间的两个十六进制数字XX指定的Latin-1编码的字符。例如，版权所有\ xA9为版权符号十六进制序列。
  \uXXXX	| 由四个十六进制数字XXXX规定的Unicode字符。例如，\ u00A9为版权符号的Unicode序列。见Unicode转义序列。
\u{XXXXX}	| Unicode code point escapes. For example, \u{2F804} is the same as the simple Unicode escapes \uD87E\uDC04.  

###### 转义字符

对于那些未出现在表2.1中的字符，其所带的前导反斜线'\'将被忽略。但是，这一用法已被废弃，应当避免使用。

通过在引号前加上反斜线'\'，可以在字符串中插入引号，这就是引号转义。例如:

```
var quote = "He read \"The Cremation of Sam McGee\" by R.W. Service.";
console.log(quote);
```
代码的运行结果为:

```
He read "The Cremation of Sam McGee" by R.W. Service.
```
要在字符串中插入'\'字面值，必须转义反斜线。例如，要把文件路径 c:\temp 赋值给一个字符串，可以采用如下方式:

```
var home = "c:\\temp";
```
也可以在换行之前加上反斜线以转义换行（译注：实际上就是一条语句拆成多行书写），这样反斜线和换行都不会出现在字符串的值中。

```
var str = "this string \
is broken \
across multiple\
lines."
console.log(str);   // this string is broken across multiplelines.
```
Javascript没有“heredoc”语法，但可以用行末的换行符转义和转义的换行来近似实现 

```
var poem = 
"Roses are red,\n\
Violets are blue.\n\
I'm schizophrenic,\n\
And so am I."
```
### Unicode编码EDIT
Unicode是一种通用字符编码标准，用于世界上主要书面语言的交换和显示。它涵盖美洲，欧洲，中东，非洲，印度，亚洲和环太平洋地区的语言，还包括古文字和技术符号。 Unicode允许多语言文本的交换、处理和显示，以及通用的技术和数学符号的使用。它有望解决多语言计算的国际化问题，如不同国家的文字标准，以解决国际化问题。但目前，并非所有的现代或古老的文字都得到了支持。

Unicode字符集可用于所有已知的编码。 Unicode字符集是在ASCII（美国信息交换标准码）字符集后建立的，它为每个字符设定一个数值和名称。字符编码指定字符的本体(identity)和数值（编码位置），以及这个数值的位(bit)表示。 16位的数字值（编码值）定义为一个带前缀U的十六进制数，例如，U+0041代表A。这个值的唯一名称是大写的拉丁字母A。

注意：1.3 版本之前的JavaScript并不支持Unicode编码。

#### 兼容于ASCII和ISO标准的Unicode编码

Unicode编码完全兼容ISO 10646的子集ISO/IEC 10646-1; 1993。

若干编码标准（包括UTF-8，UTF-16和ISO UCS-2）用于将Unicode表示为实际的二进制位。

Unicode的UTF-8编码与ASCII字符是兼容，并且被许多程序所支持。前128个Unicode字符与ASCII字符一一对应，并具有相同的字节值。从U+0020至U+007E的Unicode字符等价于从0x20到0x7E的ASCII字符。ASCII支持拉丁字母并使用7位字符集，而UTF-8的每个字符占用一到四个8位组(8位组octet，即1个字节或8位)，这样可以表示数百万个字符。另一种编码标准，UTF-16，使用两个字节来表示Unicode字符。转义序列允许UTF-16用4个8位组表示Unicode字符， ISO UCS-2（通用字符集）则使用两个字节。

JavaScript和Navigator支持UTF-8/Unicode，这意味着你可以在Javascript程序中使用非拉丁、国际化或本地化的字符，以及特殊的技术符号。Unicode提供了一种标准的方式来编码多语言文本。由于UTF-8的Unicode编码与ASCII兼容，程序可以使用ASCII字符。您可以在Javascript的注释、字符串字面值、标识符和正则表达式中使用非ASCII的Unicode字符。

#### Unicode转义序列

你可以在字符串字面值、正则表达式和标识符中使用Unicode转义序列。转义序列由6个ASCII字符构成：\u和一个4位十六进制数字。例如，\u00A9表示版权符号。每一个Unicode转义序列在JavaScript中被解释为一个字符。

下面的代码返回一个版权符号和字符串“Netscape Communications”。

```
var x = "\u00A9 Netscape Communications";
```
下表列出了常用特殊字符的Unicode值。

表 2.2 特殊字符的Unicode值

类别	              | Unicode值 | 名称	           | 格式名称
--------------------|-----------|------------------|---------
空白字符	          | \u0009	  | Tab(制表符)	     | <TAB>
                    | \u000B	  | 垂直制表符	     | <VT>  
                    | \u000C	  | 换页符	         | <FF>  
                    | \u0020	  | 空格	           | <SP>
换行符	            | \u000A	  | 换行符	         | <LF>
                    | \u000D	  | 回车符	         | <CR>
其他Unicode转义序列 |	\u0008	  | Backspace	       | <BS>
                    | \u0009	  | Horizontal Tab	 | <HT>
                    | \u0022	  | Double Quote	   | "
                    | \u0027	  | Single Quote	   | '
                    | \u005C	  | Backslash	       | \

JavaScript中Unicode转义序列的用法和Java不同。在JavaScript中，转义序列绝不会首先被理解为一个特殊字符。例如，在一个字符串的换行符转义序列不终止字符串，它被解释的功能。Javascript忽略注释中的任何转义序列。在Java中，如果在单行注释中使用转义序列，则它被解释为一个Unicode字符。对于一个字符串字面量，Java编译器首先解释转义序列。例如，如果在JavaScript(译注：此处原文误作Java)中使用一个行结束符转义字符（例如，\u000A），它终止字符串文字。而在Java中这样做将导致一个错误，因为(Unicode)换行符不允许出现在字符串字面值中，必须使用\n换行。在JavaScript中，转义序列的效果和\n一样。

#### JavaScript文件中的Unicode字符

早期的Gecko默认使用Latin-1字符作为从XUL文件加载的JavaScript代码文件的编码。在Gecko 1.8之后，则根据XUL文件的编码来推断。请参考在XUL JavaScript中使用国际字符一文内的更多信息。

#### 用Unicode编码显示字符

你可以使用Unicode显示不同语言的字符或技术符号。为了正确显示字符，客户端，如Mozilla Firefox或Netscape，必须支持Unicode。此外，客户端必须有可用的合适的Unicode字体，而且客户端平台必须支持Unicode。通常情况下，Unicode字体无法显示所有的Unicode字符。一些平台，如Windows 95，提供了对Unicode的部分支持。

要接收非ASCII字符的输入，客户端需要将输入作为Unicode来发送。使用标准的增强型键盘，客户端无法轻易地输入Unicode支持的附加字符。有时，输入Unicode字符的唯一办法就是使用Unicode转义序列。
