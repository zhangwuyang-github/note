# 前端压缩图片

上传 file 文件，使用 canvas 的api进行压缩，压缩后再转化为 file 文件上传到云服务器。

# 深拷贝浅拷贝

## 实现深拷贝

1. JSON.stringify() 缺点：无法处理函数
2. 循环遍历: a(index) = b(index) 

## 实现浅拷贝

1. =
2. Object.assign()

# 判断数据类型

1. typeof
2. instanceOf
3. .constructor
4. Object.prototype.toString.call()

# 闭包

```javascript
const a = () => {
	const val = 'hello'
	const b = () => {
		console.log(val)
	}
}
```

闭包是作用域链的特殊应用。闭包函数中声明的变量是存放于堆区中的。

# 严格模式

- 变量必须声明后才能使用

- 禁止使用with语句，因为with无法确定属性归属于哪个对象

- 禁止this指向全局作用域

- 禁止函数内部遍历调用栈

- 无法删除变量

  ```javascript
  'use strict'
  var x;
  delete x; // ERROR
  
  var o = Object.create(null, {'x': {
    value: 1,
    configurable: true
  }})
  delete o.x // 成功
  ```

- 禁止拥有同名属性
- 禁止拥有同名参数

# 虚拟节点

dom的作用是将网页转化为一个JS对象，从而可以使用脚本来进行各种操作。而dom本身是很庞大的，当我们直接操作dom去进行dom更新时，容易发生页面重排重绘，从而导致一定的性能问题。而虚拟dom在patch过程中尽可能地一次性将差异更新到DOM中；符合函数式编程思想；跨平台开发。

# diff算法

通过比较虚拟dom之间有没有改变，从而节约性能。

# 继承

- ## 原型链继承

  ```javascript
  function Parent () {
    this.name = 'kevin'
  }
  Parent.prototype.getName = function () {
    console.log(this.name)
  }
  function Child() {}
  Child.prototype = new Parent()
  const child1 = new Child()
  console.log(child1.getName()) // kevin
  ```

- ## 借用构造函数继承

  ```javascript
  /*
  * 优点：不会被所有的子类共享；可以传参
  * 缺点：每次创建实例都会创建一遍方法
  */
  function Parent () {
    this.names = ['Jack', 'Rose']
  }
  function Child (name) {
    Parent.call(this, name)
  }
  
  const child1 = new Child()
  child1.name.push('yayu')
  console.log(child1.names) // ['Jack', 'Rose', 'yayu']
  
  const child2 = new Child()
  console.log(child2.names) // ['Jack', 'Rose']
  ```

- ## 组合继承

- ## 原型式继承

  ```javascript
  function createObj (o) {
    function F() {}
    F.prototype = o
    return new F()
  }
  ```

- ## 寄生式继承

  ```javascript
  function createObj (o) {
    var clone = object.create(o)
    clone.sayName = function () {
      console.log('hi')
    }
    return clone
  }
  ```

- ## 寄生组合式继承

# EventLoop

是一种在JS引擎中等待任务，执行任务，休眠状态的无限循环。有任务时执行任务，无任务时休眠等待出现任务。

设置任务 => 引擎处理任务 => 休眠等待更多任务

当一个任务到来时，引擎可能正好在处理其他任务，那么这个任务就会被排入队列，即‘"宏任务队列"。

# async await

async是一个基于Promise的一个语法糖，他返回一个promise对象。而await关键字只能用于异步中，他表示暂时阻塞代码的运行，直到promise函数得到返回结果，并将结果返回。可以优化promise函数，使得代码逻辑清晰。缺点是他会阻塞后面代码的运行，使得如果有大量await的promise时会使得代码变慢。

# 原型

```javascript
function Person (name, age) {
  this.name = name
  this.age = age
}

const person01 = new Person('K', 21)

Person.prototype.constructor === Person
person01.__proto__ === Person.prototype
```

# 垃圾回收机制

将内存分为新生代和老生代；新生代为存活时间较短的对象，老生代为存活时间较长或常驻内存的对象。

新生代使用scavenge算法，将区域分为使用空间from、闲置空间to两个空间。
