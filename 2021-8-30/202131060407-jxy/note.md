# 数组和字符串api的总结

## 一.数组

### 1.修改原数组的方法：

##### ①.添加和删除元素：

- arr.push()：向数组末尾添加元素，返回修改后的数组长度
- arr.unshift()：向数组开头添加元素，返回修改后的数组长度
- arr.pop()：删除末尾的元素，返回被删除的元素
- arr.shift()：删除开头的元素，返回被删除的元素
- arr.splice(index,howmany,item1,item2...)：删除添加或替换元素，返回所有被删除元素组成的子数组。(index：起始位置，howmany：删除的元素个数，item：要增加或替换成的元素）

##### ②.反转数组：

- arr.reverse()：将数组反转，返回反转后的数组

##### ③.排序数组：

- arr.sort()：按照规则排序数组，默认按照数组元素第一位的ASCII码从小到大排列，返回排序后的数组
  - 升序：arr.sort(function(a,b){return a-b;});
  - 降序：arr.sort(function(a,b){return b-a;});

### 2.原数组不被改变的方法：

##### ①.截取数组：

- arr.slice(start，end)：截取指定位置的数组，返回被截取出的子数组。（start：开始位置，end：结束位置。含头不含尾）

##### ②.合并数组：

- arr.concat(a,b,c...)：参数可以为数组也可以为数字，将原数组和参数进行合并，返回拼接后的新数组。

##### ③.数组的遍历、查找和过滤：

数组遍历

- arr.map()：参数为回调函数，遍历数组所有项，可以根据函数对数组每个元素进行操作，返回操作后的新数组
- arr.forEach()：参数为回调函数，回调函数有item（数组每一项元素），index（数组索引），self（数组本身）三个参数，遍历元素值或索引值，返回值为undefined
- for(let index in arr)：用索引值遍历数组
- for(let value in arr)：遍历迭代对象数值

数组查找

- arr.indexOf(val)：查询并返回val第一次出现的位置，没有该元素返回-1
- arr.lastIndexOf(val)：查询并返回val最后一次出现的位置，没有该元素返回-1
- arr.includes(val)：判断数组中是否有val元素，返回布尔值

数组过滤：

- arr.every()：参数为回调函数，判断数组元素是否全部符合条件，返回布尔值
- arr.some()：参数为回调函数，有一个元素符合条件则返回true
- arr.filter()：参数为回调函数，返回满足条件的元素组成的子数组。

### 3.数组转字符串：

- arr.join()：以某种连接符拼接数组元素为字符串，返回字符串
- arr.toString()：直接将数组转为字符串，并返回字符串

## 二.字符串

### 1.大小写转换

- str.toLowerCase()：转换为小写并返回
- str.toUpperCase()：转换为大写并返回

### 2.截取和分割：

- str.slice(start,end)：截取字符串，并返回新字符串

- str.split()：以指定字符或正则表达式分割字符串
- str.substr(start,length)：返回从指定位置开始的子字符串

### 3.字符串的过滤：

- str.match(reg)：使用正则表达式自西向东r

