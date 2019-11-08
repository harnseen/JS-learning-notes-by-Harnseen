## 变量提升
> JavaScript 引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行地运行<br>
这造成的结果，就是所有的变量的声明语句，都会被提升到代码的头部，这就叫做变量提升
---

## 数据类型
有 Number、String、Boolean、Undefined、Null 和 Object 六个<br>
以及 ES6 新增的 Symbol，Symbol 值是原始类型，Symbol() 构造函数是对象（暂不讨论）
>### 原始类型（3个）:
>* number
>* string
>* boolean
>### 对象类型 :
>* object
>### object 又可以分为3个子类型 ：
>* 狭义的 object
>* array
>* function
---
## typeof 运算符
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
| :----: | :----: |
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

typeof null === 'object'; // 这算是一个历史遗留问题。因为在 JavaScript 最初的实现中，JavaScript 中的值是由一个表示类型的标签和实际数据值表示的。对象的类型标签是 0。由于 null 代表的是空指针（大多数平台下值为 0x00），因此，null 的类型标签是 0，typeof null 也因此返回 "object"。
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
---

## 类型转换

### 显示类型转换
### 隐示类型转换
> 字符串与其他类型数据相加，其他类型数据会自动变为字符串<br>

---

## 逻辑运算符：与或非
> &&&ensp; 若找到了第一个假，则后面的不会执行，若没找到，则取最后一个的值<br>
>&ensp;| |&ensp;&ensp;若找到了第一个真，则后面的不会执行，若没找到，则取最后一个的值<br>
---

