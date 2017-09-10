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

#### 4.数组的解构赋值 § ⇧  [数组]
``
1.  let a = 1;
    let b = 2;
    let c = 3;
    ES6 允许写成下面这样。

    let [a, b, c] = [1, 2, 3];
    
2.  let [foo, [[bar], baz]] = [1, [[2], 3]];
foo // 1
bar // 2
baz // 3

let [ , , third] = ["foo", "bar", "baz"];
third // "baz"

let [x, , y] = [1, 2, 3];
x // 1
y // 3

let [head, ...tail] = [1, 2, 3, 4];
head // 1
tail // [2, 3, 4]

let [x, y, ...z] = ['a'];
x // "a"
y // undefined
z // []
如果解构不成功，变量的值就等于undefined。  

3.默认值可以引用解构赋值的其他变量，但该变量必须已经声明。

let [x = 1, y = x] = [];     // x=1; y=1
let [x = 1, y = x] = [2];    // x=2; y=2
let [x = 1, y = x] = [1, 2]; // x=1; y=2
let [x = y, y = 1] = [];     // ReferenceError
上面最后一个表达式之所以会报错，是因为x用到默认值y时，y还没有声明。
    
``
#### 4.2 数组的解构赋值 § ⇧  [对象]
``
对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值。

let { bar, foo } = { foo: "aaa", bar: "bbb" };
foo // "aaa"
bar // "bbb"

let { baz } = { foo: "aaa", bar: "bbb" };
baz // undefined


如果变量名与属性名不一致，必须写成下面这样。

var { foo: baz } = { foo: 'aaa', bar: 'bbb' };
baz // "aaa"

let obj = { first: 'hello', last: 'world' };
let { first: f, last: l } = obj;
f // 'hello'
l // 'world'

这实际上说明，对象的解构赋值是下面形式的简写（参见《对象的扩展》一章）。

let { foo: foo, bar: bar } = { foo: "aaa", bar: "bbb" };

与数组一样，解构也可以用于嵌套结构的对象。

let obj = {
  p: [
    'Hello',
    { y: 'World' }
  ]
};

let { p: [x, { y }] } = obj;
x // "Hello"
y // "World"

默认值生效的条件是，对象的属性值严格等于undefined。

var {x = 3} = {x: undefined};
x // 3

var {x = 3} = {x: null};
x // null

如果要将一个已经声明的变量用于解构赋值，必须非常小心。
// 错误的写法
let x;
{x} = {x: 1};
// SyntaxError: syntax error
上面代码的写法会报错，因为 JavaScript 引擎会将{x}理解成一个代码块，从而发生语法错误。只有不将大括号写在行首，避免 JavaScript 将其解释为代码块，才能解决这个问题。

// 正确的写法
let x;
({x} = {x: 1});
``
