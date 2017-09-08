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
```
