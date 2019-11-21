## 节点的属性
### **nodeName** : 
>只读 <br> 元素节点：大写的标签名 <br> 属性节点：属性名 <br> 文档：#document <br> 文本节点：#text
### **nodeValue** ：
>读写 <br> 元素节点：null <br> 文本节点：内容本身 <br> 属性节点：属性值
### **nodeType** (*重要* ) :
>只读 <br> 返回节点类型 <br> 

| 元素类型	| NodeType |
| -------  | :------: |
|   元素   |     1    |
|   属性   |     2    |
|   文本   |     3    |
|   注释   |     8    |
|   文档   |     9    |

---

## 事件
### 事件的绑定与移除
#### dom0事件：
绑定：
```javascript
// 举例:
div.onclick = function() {};

/* 优点：兼容性好
** 缺点：同一个元素的同一种事件只能绑定一个函数，
*       否则后面的函数会覆盖之前的函数
*/
```
移除：
```javascript
div.onclick = null;
```

#### dom2事件：
绑定：
```javascript
function handler(){
	alert(123);
}

// 用法1：
div.addEventListener('click', hardler, false);

// 用法2：
div.attachEvent('onclick', handler);

/* 用法2是低版本IE浏览器的绑定事件的方法
*  用法1是符合W3C标准的事件绑定方法
*  dom2事件中的两种绑定事件的方法，它们所传入的参数不同
*  与dom0级事件不同的是，它们都能为一个元素添加多个事件处理函数
*  dom0和dom2可以共存，不互相覆盖，但是dom0之间依然会覆盖
*  用法1是顺序执行
*  用法2是倒序执行
*/
```
移除：
```javascript
div.removeEventListener('click', handler, false);
// 注意：removeEventListener 无法移除匿名函数

div.detachEvent('onclick', handler);
```

#### 一个兼容性写法：
 e = e || window.event;

### 事件委托