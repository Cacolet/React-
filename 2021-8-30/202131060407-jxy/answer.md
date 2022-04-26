## ES5

1.JS原始值类型：String，Number，Boolean，Null，Undefined，Symbol

2.因为计算机所有数据都是以二进制的形式存储的，所以在浮点数计算中会出现精度丢失

3.typeof，Object.prototype.toString.call()，instanceof

4.不是，因为不同的对象在底层都表示为二进制，在js中二进制前三位都为0的话会被判断为object类型，null的二进制表示是全0，所以会判断为object

5.==会先转换为同一类型再看值是否相等，而===类型不同结果就是不相等

6.①.遍历类数组，依次将元素放入一个空数组②.用扩展运算符或者Array.from()方法转换③.利用apply展开



