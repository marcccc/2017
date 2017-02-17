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

# Map
新数据结构，类似于对象，但键名不限于字符串
```javascript
let m1 = new Map([
  [true, 123],
  [{ a: 1 }, 456],
  [3, 789]
]);
console.log(m1); // Map { true => 123, { a: 1 } => 456, 3 => 789 }
// 获取 Map 实例的成员总数
console.log(m1.size); // 3
// 为 Map 实例添加键值对
console.log(m1.set(undefined, 666)); // Map { true => 123, { a: 1 } => 456, 3 => 789, undefined => 666 }
// 获取值
console.log(m1.get(undefined)); // 666
// 删除值，返回 true or false
console.log(m1.delete(3)); // true

console.log(m1); // Map { true => 123, { a: 1 } => 456, undefined => 666 }
// 返回是否在 Map 实例数据结构中
console.log(m1.has(undefined)); // true

// 遍历键名
for(let key of m1.keys()){
  console.log(key);
}
// 遍历值
for(let val of m1.values()){
  console.log(val);
}
// 遍历键值对
for(let [key,val] of m1.entries()){
  console.log(key,val);
}
// 遍历成员
m1.forEach(function(val,key){
  console.log(key,val);
});

// 清空所有成员，无返回
console.log(m1.clear()); // undefined
console.log(m1); // Map {}
```

# 解构赋值
```javascript
let [a, b, c] = [1, 2, 3];
console.log(a, b, c); // 1 2 3

let [x, y = 'b'] = ['a'];
console.log(x, y); // a b

let [m, n = 'b'] = ['a', undefined];
console.log(m, n); // a b
let { foo, bar } = { foo: 'aaa', bar: 'bbb' };
console.log(foo, bar); // aaa bbb
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

# Promise 对象
通过回调和事件实现的异步编程方案
```javascript
var promise = new Promise(function(resolve, reject) {

  setTimeout(function() {
    reject();
  }, 3000);
});

promise.then(function(value) {
    console.log('promise ok!');
  }, function(error) {
    console.log('promise error!');
  })
  .catch(function(error) {
    console.log('发生错误！', error);
  });
// 3 秒后输出 promise error!
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
类概念，通过**class**关键字，可以定义类。
* ES6 的 class 只是一个语法糖。
* **constructor** 方法是类的默认方法，通过 new 命令生成对象实例时，自动调用该方法。一个类必须有 **constructor** 方法，如果没有显式定义，一个空的 **construcotr** 方法会被默认添加。
```javascript
class Person {

  constructor(name,age){
    this.name = name;
    this.age = age;
  }

  toString() {
    return '姓名：' + this.name + '\t 年龄：' + this.age;
  }

  // 静态方法
  static duty(){
    console.log('人类应该爱护环境！');
  }
}

// 静态方法不需要实例便可调用
Person.duty(); // 人类应该爱护环境！

var zs = new Person('张三', 18);
console.log(zs); // Person { name: '张三', age: 18 }
console.log(zs.toString()); // 姓名：张三     年龄：18

// 类的继承，可以继承父类的属性和方法。还不支持多继承
class Student extends Person {
  constructor(name, age, major) {
    super(name, age);
    this.major = major; // 需要放在 super 后
  }

  toString() {
    return '姓名：' + this.name + '\t 年龄：' + this.age + '\t 专业：' + this.major;
  }

  // 静态方法只有类名可以调用，具体实例不可以
  static duty(){
    console.log('学生应该学习！')
  }
}

var lilei = new Student('李雷', 22, '计算机');
console.log(lilei); // Student { name: '李雷', age: 22, major: '计算机' }
console.log(lilei.toString()); // 姓名：李雷  年龄：22   专业：计算机
```

# 对象简洁表示法
```javascript
var foo = 'bar';
var baz = {foo};
// 等同于
var baz = {foo: foo};

var o = {
    method() {
        return 'hello!';
    }
};
// 等同于
var o = {
    method: function(){
        return 'hello!';
    }
};

// 多个
let o = {
  sayHello() {
    console.log('hello');
  },
  sayBye() {
    console.log('bye');
  }
};
o.sayHello();
o.sayBye();

let aaa = 'AAA';
let bbb = 'BBB';
let abo = { aaa, bbb };
console.log(abo);
```

# 对象合并
```javascript
var target = { a: 1, b: 2 };
var source1 = { a: -1 };
var source2 = { c: 3 };
Object.assign(target, source1, source2);
console.log(target); // { a: -1, b: 2, c: 3 }
```




