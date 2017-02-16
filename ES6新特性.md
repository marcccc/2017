# let

用来声明变量
* 只在其代码块内有效
* 不会变量提升
* 不允许在相同作用域内重复声明同一个变量

# const

声明一个只读常量
* 只在其代码块内有效
* 声明后，不能重新赋值
* 不允许在相同作用域内重复声明同一个变量

# Set
新的数据结构，与数组类似，区别是成员值唯一
```javascript
var set = new Set([1,2,3,4,4,3,2,1]); // Set { 1, 2, 3, 4 }
console.log(set.size); // 4
set.add(5); // Set { 1, 2, 3, 4, 5 }
set.add(3); // Set { 1, 2, 3, 4, 5 }
set.delete(6); // return false; Set { 1, 2, 3, 4, 5 }
set.delele(2); // return true; Set { 1, 3, 4, 5 }
set.has(2); // return false;
set.clear(); // Set {}
```
# 箭头函数
定义函数
```javascript
var f = v => v;
// 等价于
var f = function(v) {
  return v;
};
f(3); // 3

var f = () => 3; // 无参数
// 等价于
var f = function() {
  return 3;
};
f(); // 3

var sum = (a, b) => a + b;
// 等价于
var sum = function(a, b) {
  return a + b;
};
sum(1, 2); // 3
```

# 模板字符串
用反引号(**\`**)表示
```javascript
var param = {
  a: 'A',
  b: 'B'
};
var str = `i am ${param.a}, you are ${param.b}.`;
console.log(str); // 'i am A, you are B.'
```

# Generator 函数
异步编程解决方案
* **function** 关键字与函数之间有一个星号
* 函数体内部使用**yield**语句，定义不同的内部状态
```javascript
function* helloGen() {
  yield 'hello';
  yield 'generator';
  return 'end';
};
var gen = helloGen();
gen.next(); // { value: 'hello', done: false }
gen.next(); // { value: 'generator', done: false }
gen.next(); // { value: 'end', done: true }
gen.next(); // { value: undefined, done: true }
```

# Class
类概念，通过**class**关键字，可以定义类。基本上 ES6 的 class 可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到。
**constructor** 方法是类的默认方法，通过 new 命令生成对象实例时，自动调用该方法。一个类必须有 **constructor** 方法，如果没有显式定义，一个空的 **construcotr** 方法会被默认添加。
