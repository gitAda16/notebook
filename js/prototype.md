## prototype详解

### 概念

prototype属于函数的一个属性，是函数的原型对象，能够引用它的只有函数

为什么说prototype是函数的一个属性呢？因为，只有函数才能调用prototype，而且是以这样的方式func.prototype调用的,这样的方式调用东西是不是和对象调用属性一模一样呢？是的，就是因为函数调用prototype的时候是和对象调用属性的时候一样的，我们才把prototype说成是函数的一个属性为什么说prototype是函数的一个属性呢？因为，只有函数才能调用prototype，而且是以这样的方式func.prototype调用的

而函数的这个属性其实是一个对象，所以说，这个prototype就是函数的属性，本质是函数的原型对象

```javascript
function func(){}
console.log(func.prototype)
console.log(typeof(func.prototype))
console.log(JSON.stringify(func.prototype))
```

为什么强调说prototype的本质是函数的原型对象呢

因为函数的实例对象都可以拥有prototype中定义的属性

```javascript
//定义一个函数
function func(){

}
//给函数的属性prototype赋予一个方法get
func.prototype.get=function(value){
    return value;//很简单，你给我什么我就输出什么
}
var ob1 = new func();
//用func实例化出来的对象来调用get属性函数
console.log(ob1.get('hello,prototype原型对象'));
console.log(func.prototype.get('asdf'));
```

**特别指出**：

- Array.prototype是一个数组

- String.prototype是一个字符串

- Object.prototype是一个对象

前面说prototype只能是函数的属性，这里需要注意的是 Array String Object 他们都能使用new的方式创建对象，他们其实都是内置函数

### prototype应用

- 应用1：给原型对象增加函数，就是让对象拥有公用的函数。

```javascript
Array.prototype.shuffle = function() {
		var value = this.valueOf(), len = this.length, temp, key;
		while (len--) {
			//随机生成数组的下标
			key = Math.floor(Math.random() * len);
			//temp为中间交换变量
			temp = value[key];
			value[key] = value[len];
			value[len] = temp;
		}
		return value;
	}
	var arr1 = [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 ];
	var arr2 = [ 'a', 'b', 'c', 'd', 'e', 'f' ];
	alert(JSON.stringify(arr1.shuffle()));
	alert(JSON.stringify(arr2.shuffle()));
```

- 应用2：给原型对象增加属性，也就是给对象增加公用的属性

```javascript
function fun() {

	}
	fun.prototype.name = '小东';
	fun.prototype.arr = [ 1, 2, 3, 4 ];//这里的属性可以是数组，也可以是对象
	var ob1 = new fun();
	var ob2 = new fun();
	alert(JSON.stringify(ob1.name));
	alert(JSON.stringify(ob2.arr));
```

- 应用3：实现原型继承

```javascript
function P1() {

	}
	function P2() {

	}
	//原型对象增加属性和方法
	P2.prototype.name = 'P2"s name';
	P2.prototype.get = function(value) {
		return value;
	}
	//实例化P2构造函数的一个对象
	var obp2 = new P2();//这个对象应该包含所有原型对象的属性和方法
	//给P1的原型对象赋值一个对象，相当于P1继承了obp2的所有属性和方法
	P1.prototype = obp2;//这个式子，简单来讲就类似于a = b, b赋值给a这个总该明白吧？
	//调用P1从obp2继承过来的get函数
	console.log(P1.prototype.get('out"s name'));
	//展示P1从obp2继承过来的name属性
	console.log(P1.prototype.name);
	//用构造函数P1实例化一个obp1对象
	var obp1 = new P1();
	//P1的原型对象prototype既然已经继承了obp2的所有属性和函数，那么依据P1所实例化出来的对象也都有obp2的属性和函数了
	console.log(obp1.get('obp1"s name'));
```

以上内容来源于[深入理解prototype](https://www.cnblogs.com/loveyoume/p/6139681.html)

## \_\_proto\_\_

### 概念

\_\_proto\_\_为对象所有，prototype为函数所有，由于函数也是对象，所有函数也有_\_proto\_\_属性

它的作用就是当访问一个对象的属性时，如果该对象内部不存在这个属性，那么就会去它的\_\_proto\_\_属性所指向的那个对象（可以理解为父对象）里找，如果父对象也不存在这个属性，则继续往父对象的\__\_proto\_\_属性所指向的那个对象（可以理解为爷爷对象）里找，如果还没找到，则继续往上找….直到原型链顶端null（可以理解为原始人。。。），此时若还没找到，则返回undefined（可以理解为，再往上就已经不是“人”的范畴了，找不到了，到此为止）_

由以上这种通过\__\_proto\_\_属性来连接对象直到null的一条链即为我们所谓的**原型链**

\_\_proto\_\_指向函数的原型对象prototype,如下

```javascript
function Foo() {
	};
var	f1 = new Foo();
//f1.__proto__ == Foo.prototype
```

## constructor

constructor属性也是对象才拥有的，它是从一个对象指向一个函数，含义就是指向该对象的构造函数，每个对象都有构造函数，从图中可以看出Function这个对象比较特殊，它的构造函数就是它自己（因为Function可以看成是一个函数，也可以是一个对象），所有函数最终都是由Function()构造函数得来，所以constructor属性的终点就是Function()。

![1551347756078](D:\source\git\notebook\notebook\js\prototypeconstruct.png)

以上内容来自[prototype](https://blog.csdn.net/cc18868876837/article/details/81211729)

## 继承

待续

