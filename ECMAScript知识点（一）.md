# 目录
[**变量提升**](#变量提升) <br>
[**数据类型**](#数据类型) <br>
&ensp;&ensp;[string,number,boolean,null,undefined,object](#数据类型) <br>
[**常见操作符 / 运算符**](#运算符) <br>
&ensp;&ensp;[typeof 运算符](#typeof运算符) <br>
&ensp;&ensp;[逻辑运算符：与或非](#逻辑运算符：与或非) <br>
&ensp;&ensp;[逗号操作符](#逗号操作符) <br>
[**类型转换**](#类型转换) <br>
&ensp;&ensp;[显示类型转换](#显示类型转换) <br>
&ensp;&ensp;[隐示类型转换](#隐示类型转换) <br>
[**JS常见内置对象**](#JS常见内置对象)


## <a name="变量提升">变量提升</a>
> JavaScript 引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行地运行<br>
这造成的结果，就是所有的变量的声明语句，都会被提升到代码的头部，这就叫做变量提升
---

## <a name="数据类型">数据类型</a>
有 Number、String、Boolean、Undefined、Null 和 Object 六个<br>
以及 ES6 新增的 Symbol，Symbol 值是原始类型，Symbol() 构造函数是对象（暂不讨论）
>### 原始类型/基本类型（Undefined 和 Null 比较特殊）:
>* Number
>* String
>* Boolean
>### 对象类型/引用类型 :
>* Object
>### object 又可以分为3个子类型 ：
>* 狭义的 Object
>* Array
>* Function
---
## <a name="运算符">常见操作符 / 运算符</a>
### <a name="typeof运算符">typeof 运算符</a>
#### 语法：
```javascript
/*
 * 下面是使用 typeof 的两种方法
 * operand 为参数
 */
typeof operand;   
typeof(operand);   
```
#### typeof 可能的返回值:
| 类型 | 返回值 |
| ---  | ---- |
| Undefined | "underfined" |
| Null | "object" |
| Boolean |	"boolean" |
| Number	| "number" |
| Symbol | "symbol" |
| BigInt	| "bigint" |
| String	| "string" |
| Function | "function |
| 其它任何对象 | "object" |
> **注意：typeof 的返回值是一个字符串**<br>
>> 例如：typeof(123) 返回的是 "number"，typeof(true) 返回的是 "boolean",它们都是字符串
#### 一些比较特殊的情况：
```javascript
typeof Infinity === 'number'; // Infinity属性的值为Number类型

typeof NaN === 'number'; // 尽管它是 "Not-A-Number" (非数值) 的缩写

typeof (typeof 1) === 'string'; // 正如上文提到的，typeof 总是返回一个字符串

typeof null === 'object'; 
/* 这算是一个历史遗留问题。
 * 因为在 JavaScript 最初的实现中，
 * JavaScript 中的值是由一个表示类型的标签和实际数据值表示的。
 * 对象的类型标签是 0。由于 null 代表的是空指针（大多数平台下值为 0x00），
 * 因此，null 的类型标签是 0，typeof null 也因此返回 "object"。
 */
```
```javascript
// 除 Function 外的所有构造函数的类型都是 'object'
var str = new String('String');
var num = new Number(100);

typeof str; // 返回 'object'
typeof num; // 返回 'object'

var func = new Function();

typeof func; // 返回 'function'
```
```javascript
// 括号有无将决定表达式的类型。
var iData = 99;

typeof iData + ' Wisen'; // 'number Wisen'
typeof (iData + ' Wisen'); // 'string'
```
```javascript
//对正则表达式字面量的类型判断在某些浏览器中不符合标准：
typeof /s/ === 'function'; // Chrome 1-12 , 不符合 ECMAScript 5.1
typeof /s/ === 'object'; // Firefox 5+ , 符合 ECMAScript 5.1
```
#### 原始类型的值不可变，对象的值可变
> 这个涉及到数据结构的知识<br>
> 任何方法都改变不了原始值，而对象类型是可以修改的<br>
> 参考《JavaScript权威指南(第六版)》第三章的第七节：“不可变的原始值和可变的引用对象”

> **当两个引用值相比较，比较的是地址**
---
### <a name="逻辑运算符：与或非">逻辑运算符：与或非</a>
> &&&ensp; 若找到了第一个假，**则后面的不会执行**，若没找到，则取最后一个的值<br>
>&ensp;| |&ensp;&ensp;若找到了第一个真，**则后面的不会执行**，若没找到，则取最后一个的值<br>

>与( && )的优先级高于或( || )
---
### <a name = "逗号操作符">逗号操作符</a>
> 对它的每个操作数求值（从左到右），并返回最后一个操作数的值。

#### 练习
```javascript
var f = (
    function f() {
        return "1";
    },
    function g() {
        return 2;
    }
)();

typeof f;
```
<details><summary><b>答案</b></summary>

"number"

</details>

---

## <a name="类型转换">类型转换</a>
### 为什么 JavaScript 中会经常发生类型转换？
> 因为 JavaScript 是弱类型语言，变量没有类型限制，可以随时赋予任意值
### <a name="显示类型转换">显示类型转换/强制转换</a>
#### Number( )
> 可能会有以下四种结果：<br>
> ***能够转换数字*** ：当参数为字符串，且字符串里的内容为纯数字，或当参数为只包含单个纯数字的数组，则返回这个纯数字 <br>
> ***0*** ：false，null，"" ( 空字符串 )或空数组<br>
> ***1*** : true<br>
> ***NaN*** : undefined, 对象或含有非数字字符的字符串。
```javascript
// 例子
console.log(Number("1px"));     // NaN
console.log(Number("1"));       // 1
console.log(Number({}));        // NaN
console.log(Number(null));      // 0
console.log(Number(undefined)); // NaN
console.log(Number([]));        // 0
console.log(Number(""));        // 0
console.log(Number(true));      // 1
console.log(Number(false));     // 0
console.log(Number([5]))        // 5
```
#### parseInt( )
> 用法与 Number ( ) 有些类似 <br>
> 常用来提取字符串中的数字 <br>
> 返回值只有两种可能：一个整数或NaN
##### 语法 ：
```javascript
parseInt(string, radix);
// string 是要被解析的值
// radix 表示string的基数
// string 将以这个进制运算，它的取值为2-36，可以省略。
// 例如：radix参数为10 将会把第一个参数看作是一个数的十进制表示，8 对应八进制，16 对应十六进制，等等。基数大于 10 时，用字母表中的字母来表示大于 9 的数字。例如十六进制中，使用 A 到 F
```
#### parseFloat( )
> 用法与 parseInt 相似 <br>
> 不同的是，parseFloat 没有 radix 参数，除了可以返回整数，还能返回浮点数。
#### String( )
>***数值***：&ensp;&ensp;&ensp;&ensp;&ensp;转为相应的字符串。<br>
>***字符串***：&ensp;&ensp;&ensp;转换后还是原来的值。 <br>
>***布尔值***：&ensp;&ensp;&ensp;true转为字符串"true"，false转为字符串"false"。<br>
>***undefined***：转为字符串"undefined"。<br>
>***null***：&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;转为字符串"null"。
```javascript
// 例子
String(123)          // "123"
String('abc')       // "abc"
String(true)       // "true"
String(undefined) // "undefined"
String(null)     // "null"
```
>String方法的参数如果是对象，返回一个类型字符串；如果是数组，返回该数组的字符串形式
```javascript
// 例子
String({a: 1}) // "[object Object]"
String([1, 2, 3]) // "1,2,3"
```
> String( )、toString( ) 与 typeof 方法相同的地方在于，它们返回的都是一个字符串
#### toString( )
> toString( ) 的功能与 String( ) 很类似 <br>
> 但有两个不同点：
> * 语法不同 <br> 1. 一个是 thing.toString() ，另一个是 String(thing) <br> 2. toString( ) 可以传参 
> * 不能转换 Null 和 Undefined
##### 语法：
```javascript
thing.toString();

// 当 thing 为 Number 时, 可以带 radix 参数
thing.toString(radix);
// 表示将 thing 转换成 radix 进制的数
```

#### Boolean( )
只有以下五种情况会返回 false ：
> * undefined
> * null
> * 0(包含-0和+0)
> * NaN
> * ""（空字符串）

其他的返回 true
### <a name="隐示类型转换">隐示类型转换</a>
>1. 转换成string：字符串与其他类型数据相加( + )时，其他类型数据会自动变为字符串, 即连接，其他情况则会自动转换为 number 类型
>2. 转换成number：++/--(自增自减运算符) + - * / %(算术运算符) > < >= <= == != === !=== (关系运算符)
>3. 转成boolean类型：!（逻辑非运算符）
>4. 字符串比较大小，比较的是ASCII码，一个数一个数地比较，或一个字母一个字母地比较
>5. 对于对象和数组：<br>1.先使用valueOf()方法获取其原始值，如果原始值不是number类型，则使用 toString()方法转成string <br>2.再将string转成number运算
>6. 特殊情况：<br>1. null == undefined <br> null 不等于任何值除了 null 和 undefined <br>2. NaN != NaN <br> NaN 不等于任何值，包括 NaN 本身

### 小练习1：
var a="123abc"; 
1. typeof(+a) 
2. typeof(!!a) 
3. typeof(a+"")
4. alert(1=="1");
5. alert(NaN==NaN); 
6. alert(NaN==undefined); 
7. alert("11"+11); 
8. alert(1==="1"); 
9. alert(parseInt("123abc"));
10. var num=123123.345789; <br>alert(num.toFixed(3)); 
11. typeof(typeof(a));
<details><summary><b>答案</b></summary>

```javascript
1. "number" // +a ==> NaN ==> number
2. "boolean" // !! 相当于 Boolean()
3. "string" // 连接运算符
4. true  // "1" ==> 1
5. false  // 特殊情况 NaN 不与任何东西相等，包括自己
6. false
7. "1111" // 连接
8. false // 一致运算符不会进行类型转换，
         //仅当操作数严格相等时返回true
9. 123   // 提取字符串开头整形数字
10. 123123.346 // 四舍五入保留3位
11. "string"  // typeof 方法返回字符串
```

</details>

### 小练习2：
1. true + false
2. 12 / "6"
3. "number" + 15 + 3
4. 15 + 3 + "number"
5. [1] > null
6. "foo" + + "bar"
7. "true" == true
8. false == "false"
9. null == ""
10. !!"false" == !!"true"
11. ["x"] == "x"
12. [] + null + 1
13. [1,2,3] == [1,2,3]
14. {} + [] + {} + [1]
15. ! + [] + [] + ![]
16. new Date(0) - 0
17. new Date(0) + 0
<details><summary><b>答案解析</b></summary>

```javascript
1. 1
2. 2
3. "number153"
4. "18number"
5. true
6. "fooNaN"
7. false
8. false
9. false
10. true
11. true
12. "null1"
13. false
14. "0[object Object]1"
15. 'truefalse'
16. 0
17. Thu Jan 01 1970 08:00:00 GMT+0800 (中国标准时间)0"
```
答案详细解析：[17道题让你彻底理解JS中的类型转换](https://www.jb51.net/article/167231.htm)

</details>

---
## <a name="JS常见内置对象">JS常见内置对象</a>
### <a name="Array对象">Array对象 / 数组</a>
#### 属性：
>length：返回数组元素的个数（数组的长度）
```javascript
var arr = [1, 2, 3];
console.log(arr.length); // 3
```
#### 常用方法：
**push( ):**
>往数组结尾添加一个或多个数组元素，并返回新长度

**unshift( ):**
>往数组前面添加一个或多个数组元素，并返回新长度

**pop( ):**
>删除数组最后一个元素，并返回被删除的元素（相当于剪切）<br> 
如果数组为空则返回 undefined

**shift( ):** 
>删除数组第一个元素，并返回被删除的元素（相当于剪切）<br>
如果数组为空则返回 undefined

**slice( ):**
>从已有的数组中返回选定的元素，不会改变原数组 <br> 
语法：slice(start, end), start 是必须的，end 是可选的 <br> 
返回一个新的数组，包含从 start 到 end（不包括该元素）, 参数可为负数。

**splice( ):**
>添加/删除元素，会改变原数组 <br>
返回删除的元素，如果只是添加元素，则会返回空数组 <br>
语法：splice( index, howmany, item ) <br>
其中，index 和 howmany 是必须的，item 是可选的 <br>
howmany 表示删除元素的个数，0 则表示不删除 <br>
item 要增加的元素 <br>
splice 方法可以在删除元素的同时增加元素

**concat( ):**
>连接多个数组，不会改变原数组

**indexOf( ):**
>返回某个指定的字符串值在字符串中首次出现的位置 <br>
语法：indexOf ( searchvalue, fromindex) <br>
searchvalue 是必须的，表示需要检索的元素,若没有则返回-1
<br>

**join( ):**
>将数组转换成字符串 <br>
默认是 , (逗号)
也可以是其他的，如空字符串，-，·


[数组10个方法](https://blog.csdn.net/e7SFd9w7T0c1W/article/details/78863489)
