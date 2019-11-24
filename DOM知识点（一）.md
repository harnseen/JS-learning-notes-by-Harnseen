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

### 事件流
#### 事件流的三个阶段
1. 事件流的三个阶段
事件捕捉阶段：由外部动作触发到传递到目标元素最近的父节点的过程，途中不会接受事件。
2. 处于目标元素阶段：从事件传入到目标元素之初，到未接收事件之末的过程。
3. 冒泡阶段：从事件接受处理触发之初，到事件递交document节点之末的过程，途中接受事件。
#### 事件的冒泡与捕获
>addEventListener( )方法，可以传入三个参数，前两个是必须的，第三个是一个可选的布尔类型的数 <br>
默认是 false，指定事件发生在冒泡阶段 <br> true 指定事件发生在捕获阶段

![事件的捕获和冒泡](./static/img/事件的捕获和冒泡.png)

#### 事件代理 / 事件委托
例子：
```html
	<ul id="ul" onclick="show(event)">
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
	</ul>
```
```javascript
	function show (e) {
		//事件target属性:返回事件的目标节点(简称触发节点)
		var tagname = e.target;
		if (tagname.nodeName = "li")
		alert(tagname.innerHTML);
	}
```
>在上面这个例子中，虽然没有为每个 li 标签绑定函数，但利用事件代理，可以完成点击每个 li 标签就弹出对应数字的功能

事件代理的优点：
1. **提高性能**: 每一个函数都会占用内存空间，只需添加一个事件处理程序代理所有事件,所占用的内存空间更少。
2. **动态监听**: 使用事件委托可以自动绑定动态添加的元素,即新增的节点不需要主动添加也可以一样具有和其他元素一样的事件。