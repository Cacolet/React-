# Answer

## 1

* 数值（number)
* 字符串（string）
* 布尔值（boolean）
* undefined
* null
* 对象（object)

## 2

计算机会将十进制转为二进制运算，运算小数过程会产生精度问题

## 3

* `instanceof`运算符
* `typeof`运算符
* `Object.prototype.toString`方法

## 4

* 这是由于历史原因造成的，最初只设计了五种数据类型（对象、整数、浮点数、字符串和布尔值），把null当作`object`的一种特殊值，后来`null`独立出来。

## 5

相等操作符（==）会做类型转换，再进行值的比较，全等运算符(===)不会做类型转换.

## 6

* 利用数组对象的`slice`方法,被处理的对象必须有`length`属性，以及相对应的数字键。

```
Array.prototype.slice.apply({0: 1, length: 1}) // [1]
```

* Array.from()方法

```
let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
};

// ES6 的写法
let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
```

