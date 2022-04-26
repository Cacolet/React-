**一 .**

**(1)** Number 、String 、Boolean 、Null 、Undefined

**(2)** 因为 JS 里面采用的是 IEEE 754双精度标准，计算机内部存储数据的编码的时候，0.1在计算机内部根本不是精

​      确的0.1 ，而是一个有舍入误差的 0.1 。当代码被编译或解释后，0.1已经被四舍五入成一个与之很接近的计算

​      机内部数字，以至于计算还没开始，一个很小的舍入错误就产生了 。所以 0.1 + 0.2 ！= = 0.3

**(3)** null 不是对象 ，这是 JS 存在的一个悠久 Bug。在 JS 的最初版本中使用的是 32 位系统，为了性能考虑使用低    位存储变量的类型信息，000开头代表是对象，然而null表示为全零，所以将它错误的判断为object。虽然现在的内部类型判断代码已经改变了，但是对于这个 Bug 却是一直流传下来

**(4)**   

​          1> typeof  ： 用来判断基本数据类型 ，返回对应数据类型的字符串 ，

​                                   注 ： 不能判断 Array 和 null ，返回值都是 object 

 

​          2> instanceof :  判断参照对象（大写字母A）的prototype属性所指向的对象是否在被行测对象a的原型链

​                                       上，instanceof 只能用来判断两个对象是否属于实例关系，而不能判断一个对象实例具体 

​                                       属于哪种类型

​         

​          3> constructor ： 这种方式解决了instanceof的弊端，可以检测出除了undefined和null的9种类型（因为它

​                                          两没有原生构造函数）

​                                          console.log(udf.constructor); //Cannot read property "constructor" of undefined

​                                          console.log(nul.constructor);//Cannot read property "constructor" of null



​          4> === :                    可以判断undefined （a===undefined）                                           

​                                            可以判断null 



  **(5)**    == 代表相等， ===代表严格相等

​        这么理解： 当进行双等号比较时候： 先检查两个操作数数据类型，如果相同， 则进行===比较， 如果不同， 

​        则愿意为你进行一次类型转换， 转换成相同类型后再进行比较， 而===比较时， 如果类型不同，直接就是

​         false.

​        **比较过程 ：** <1> ==      ：

​                                                     （1）如果两个值类型相同，再进行三个等号(===)的比较

　　                                           （2）如果两个值类型不同，也有可能相等，需根据以下规则进行类型转换在比较：

　　　　                                                   1）如果一个是null，一个是undefined，那么相等

　　　                                                   　2）如果一个是字符串，一个是数值，把字符串转换成数值之后再进行比较

​                              <2> ===       ： 

​                                               （1）如果类型不同，就一定不相等

　　                                      （2）如果两个都是数值，并且是同一个值，那么相等；如果其中至少一个是NaN，那

​                                                 么不相等。（判断一个值是否是NaN，只能使用isNaN( ) 来判断）

　　                                      （3）如果两个都是字符串，每个位置的字符都一样，那么相等，否则不相等。

　　                                      （4）如果两个值都是true，或是false，那么相等

　　                                      （5）如果两个值都引用同一个对象或是函数，那么相等，否则不相等

　                                      　（6）如果两个值都是null，或是undefined，那么相等

**（6）**  

​               **1》：**遍历类数组，依次将元素放入一个空数组。类数组本身虽然不是数组，但是有interator接口，所以

​                         可以遍历

​               **2》:**   扩展运算符 或者 Array . from ( ) 

![img](https://img-blog.csdn.net/20180719002007510?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjczMzE1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



​            **3》：** 用apply展开

​                      ![img](https://img-blog.csdn.net/20180719003043306?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjczMzE1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)