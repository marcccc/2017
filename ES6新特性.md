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
