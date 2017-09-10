# ES6-notes
##### 1.let命令 
```
let适合for循环 
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6]();  //6    如果使用for则只能输出10

1 .  let不允许重复声明
2.  外层代码块不受内层代码块的影响
function f1() {
  let n = 5;
  if (true) {
    let n = 10;
  }
  console.log(n); // 5
}
```
#### 2.const命令 
```
1.const声明一个只读的常量。一旦声明，常量的值就不能改变。
2.const的作用域与let命令相同：只在声明所在的块级作用域内有效。
3.const声明的常量，也与let一样不可重复声明。
4.如果真的想将对象冻结，应该使用Object.freeze方法。

const foo = Object.freeze({});

// 常规模式时，下面一行不起作用；
// 严格模式时，该行会报错
foo.prop = 123;
```
#### 3. global
``
浏览器里面，顶层对象是window，但 Node 和 Web Worker 没有window。
浏览器和 Web Worker 里面，self也指向顶层对象，但是 Node 没有self。
Node 里面，顶层对象是global，但其他环境都不支持。
``

