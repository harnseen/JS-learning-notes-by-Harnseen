# 目录
[变量提升](#变量提升) <br>
[数据类型](#数据类型) <br>
[typeof 运算符](#typeof运算符) <br>
[类型转换](#类型转换) <br>
[逻辑运算符：与或非](#逻辑运算符：与或非) <br>

## <a name="">变量提升</a>
> JavaScript 引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行地运行<br>
这造成的结果，就是所有的变量的声明语句，都会被提升到代码的头部，这就叫做变量提升
---

## <a name="数据类型">数据类型</a>
有 Number、String、Boolean、Undefined、Null 和 Object 六个<br>
以及 ES6 新增的 Symbol，Symbol 值是原始类型，Symbol() 构造函数是对象（暂不讨论）
>### 原始类型/基本类型（Undefined 和 Null 比较特殊）:
>* number
>* string
>* boolean
>### 对象类型/引用类型 :
>* object
>### object 又可以分为3个子类型 ：
>* 狭义的 object
>* array
>* function
---
## <a name="typeof运算符">typeof 运算符</a>
### 语法：
```javascript
/*
 * 下面是使用 typeof 的两种方法
 * operand 为参数
 */
typeof operand    
typeof(operand)   
```
### typeof 可能的返回值:
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
### 一些比较特殊的情况：
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
### 原始类型的值不可变，对象的值可变
> 这个涉及到数据结构的知识<br>
> 任何方法都改变不了原始值，而对象类型是可以修改的<br>
> 参考《JavaScript权威指南(第六版)》第三章的第七节：“不可变的原始值和可变的引用对象”
---

## <a name="类型转换">类型转换</a>
### 为什么 JavaScript 中会经常发生类型转换？
> 因为 JavaScript 是弱类型语言，变量没有类型限制，可以随时赋予任意值。
### 显示类型转换/强制转换
#### Number( )
> 可能会有以下四种结果：<br>
> ***纯数字***：当参数为字符串，且字符串里的内容为纯数字，或当参数为只包含单个纯数字的数组，则返回这个纯数字 <br>
> ***0***：false，null，''(空字符串)<br>
> ***1***: true<br>
> ***NaN***: undefined,对象或字符串中含有非数字的字符。
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
### 隐示类型转换
> 字符串与其他类型数据相加，其他类型数据会自动变为字符串<br>

### 小练习：
var a="123abc"; 
1. typeof(+a) 
7. typeof(!!a) 
8. typeof(a+"")
9. alert(1=="1");
10. alert(NaN==NaN); 
11. alert(NaN==undefined); 
12. alert("11"+11); 
13. alert(1==="1"); 
14. alert(parseInt("123abc"));
15. var num=123123.345789; <br>alert(num.toFixed(3)); 
16. typeof(typeof(a));
<details><summary><b>答案</b></summary>
<p>


</p>
</details>

---

## <a name="逻辑运算符：与或非">逻辑运算符：与或非</a>
> &&&ensp; 若找到了第一个假，**则后面的不会执行**，若没找到，则取最后一个的值<br>
>&ensp;| |&ensp;&ensp;若找到了第一个真，**则后面的不会执行**，若没找到，则取最后一个的值<br>
---

