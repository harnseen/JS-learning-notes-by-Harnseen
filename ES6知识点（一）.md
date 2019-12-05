## let 和 const
>不存在变量提升，声明之前使用会报错 <br>
都不能重复声明 <br>
let 可以重复赋值，const 不行 <br>
对于 let 有“临时性死区” <br>
只在块级作用域内有效

## Symbol
1. 创建 Symbol 类型数据时不能用 new 命令，因为 Symbol 是原始数据类型，不是对象
2. Symbol 作为对象属性名时不能用.运算符，要用方括号
3. Symbol 值作为属性名时，该属性是公有属性不是私有属性，可以在类的外部访问。但是不会出现在 for...in 、 for...of 的循环中，也不会被 Object.keys() 、 Object.getOwnPropertyNames() 返回。如果要读取到一个对象的 Symbol 属性，可以通过 Object.getOwnPropertySymbols() 和 Reflect.ownKeys() 取到
4. Symbol.for( )，Symbol.keyFor( )

## 结构赋值
### [对象解构赋值](https://segmentfault.com/a/1190000013817091)

### [数组解构赋值](https://segmentfault.com/a/1190000019928303)

### [函数参数解构](https://segmentfault.com/a/1190000007768428)

## Promise
[Promise 用法](https://blog.csdn.net/qq_34645412/article/details/81170576) <br>
[Promise 详细视频教程（尚硅谷）](https://www.bilibili.com/video/av77292118) <br>
[十道练习题](https://blog.csdn.net/weixin_37719279/article/details/80950713) <br>
[Promise 面试题](https://blog.csdn.net/FE_dev/article/details/83278508) <br>
[Promise 源码实现](https://segmentfault.com/a/1190000018428848) <br>

Promise 练习:
```javascript
setTimeout(()=>{
    console.log('setTimeout1')
    })

let p1=new Promise((resolve)=>{
    console.log('Promise1')
    resolve('Promise2')
})

p1.then((res)=>{
    console.log(res)
})

console.log(1)

setTimeout(()=>{
console.log('setTimeout2')
})
```
<details><summary>答案</summary>

Promise1 <br>
1 <br>
Promise2 <br>
setTimeout1 <br>
setTimeout2

**解析**：<br>
本题的难点在于then和setTimeout的执行顺序。setTimeOut追加在次轮循环，而then 或 catch 中的代码将在本轮循环的末尾执行，先于次轮循环。<br>
**文章**：<br>
[*定时器与代码执行次序*](https://blog.csdn.net/tang_yi_/article/details/80067696) <br>
[*setTimeout与 console.log、promise.then之间执行先后顺序*](https://blog.csdn.net/judy_qiudie/article/details/82768243)
</details>