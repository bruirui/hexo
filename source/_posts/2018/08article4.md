---
title: 闭包
urlname: article4
date: 2018-08-24 10:29:55
tags: JavaScript
---

>闭包：能够读取其他函数内部变量的函数  
 闭包应用：函数作为返回值、函数作为参数传递
 闭包会导致原始作用域链不释放，造成内存泄漏（占用）

### 闭包经典面试题
```
for (var i = 1; i <= 5; i++) {
  setTimeout( function timer() {
      console.log(i);
  }, 1000 );
}
```
执行结果: 
```
6
6
6
6
6
```
#### 为什么执行结果会是这样?
setTimeout()函数要等执行完函数调用栈中的代码，然后立即调用定时器。定时器会放在队列的数据结构中，等待上下文的可执行代码运行完毕后，才开始运行定时器。所以在定时器运行的时候，变量i已经为6，所以输出全部是6.

拓展：[深入浅出js事件循环机制（上）](https://zhuanlan.zhihu.com/p/26229293)[深入浅出js事件循环机制（下）](https://zhuanlan.zhihu.com/p/26238030)

#### 那么做怎样的修改输出1 2 3 4 5?
思路：定时器访问的变量i是独立的(使用js闭包)
	 使用ES6新增变量声明方式let,可创建独立的块级作用域,即声明一个仅对当前"{}"内部有作用的变量
```
for (var i = 1; i <= 5; i++) {
  (function(i){
  	setTimeout( function timer() {
       	  console.log(i);
	}, 1000 );
  })(i)
}
```

---
### 再来一道
参考: [经典JS闭包面试题](https://www.cnblogs.com/xxcanghai/p/4991870.html)
```
function fun(n,o) {
  console.log(o)
  return {
    fun:function(m){
      return fun(m,n);
    }
  };
}
var a = fun(0);  a.fun(1);  a.fun(2);  a.fun(3);
var b = fun(0).fun(1).fun(2).fun(3);
var c = fun(0).fun(1);  c.fun(2);  c.fun(3);
//问:三行a,b,c的输出分别是什么？
```
执行结果: 
```
undefined 0 0 0
undefined 0 1 2
undefined 0 1 1
```
#### 注解：
![函数分析.png](../../../../resource/bibao.png "函数分析")
1. 第一行
	```
	var a = fun(0);  a.fun(1);  a.fun(2);  a.fun(3);
	```
	a=fun(0); 调用第一层fun函数; o=undefined,n=0;
	a.fun(1); 是在调用前一个fun的返回值的fun函数(调用第二层fun函数); fun(m=1,n=0)
	a.fun(2); 同a.fun(1)
	a.fun(3); 同a.fun(1)
	即：最终结果为undefined,0,0,0
2. 第二行
	```
	var b = fun(0).fun(1).fun(2).fun(3);
	```
	fun(0); 调用第一次fun函数; o为undefined；
	fun(0).fun(1); m为1，此时fun闭包了外层函数的n，也就是第一次调用的n=0，即m=1，n=0，并在内部调用第一层fun函数fun(1,0);所以o为0；
	fun(0).fun(1).fun(2); m为2，此时当前的fun函数不是第一次执行的返回对象，而是第二次执行的返回对象。而在第二次执行第一层fun函数时时(1,0)所以n=1,o=0,返回时闭包了第二次的n，遂在第三次调用第三层fun函数时m=2,n=1，即调用第一层fun函数fun(2,1)，所以o为1；
	fun(0).fun(1).fun(2).fun(3); .fun(3)时m为3，闭包了第三次调用的n，同理，最终调用第一层fun函数为fun(3,2)；所以o为2；
	即：最终结果为undefined,0,1,2
3. 第三行
	```
	var c = fun(0).fun(1);  c.fun(2);  c.fun(3);
	```
	a=fun(0); 调用第一层fun函数; o=undefined,n=0;
	fun(0).fun(1); 执行的是fun(0)返回的第二层fun函数，此时fun闭包了外层函数n,也就是第一次调用的n=0,即m=1,n=0,并在内部调用第一层fun函数fun(1,0); o为0；
	c.fun(2); m=2,此时fun闭包的是第二次调用的n=1,即m=2，n=1，并在内部调用第一层fun函数fun(2,1)； o为1；
	c.fun(3); 同c.fun(2);
	即：最终结果为undefined,0,1,1
