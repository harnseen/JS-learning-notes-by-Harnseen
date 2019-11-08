## 变量提升
> JavaScript 引擎的工作方式是，先解析代码，获取所有被声明的变量，然后再一行一行地运行<br>
这造成的结果，就是所有的变量的声明语句，都会被提升到代码的头部，这就叫做变量提升
---

## 数据类型
Number、String、Boolean、Undefined、Null 和 Object<br>
ES6新增了 Symbol，Symbol 值是原始类型，Symbol() 构造函数是对象（暂不讨论）
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
| ---- | ---- |
| Undefined | "underfined" |
| Null | "null" |
| Boolean |	"boolean" |
| Number	| "number" |
| Symbol | "symbol" |
| BigInt	| "bigint" |
| String	| "string" |
| Function | "function |
| 其它任何对象 | "object" |
> **注意：typeof 的返回值是一个字符串**<br>
> 例如：typeof(123) 返回的是 "number"，typeof(true) 返回的是 "boolean",它们都是字符串
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

