###                                              数组API ：

**1》增加删添数组与元素方法**
       (1) push()   ----------  在数组的末尾 添加一个或者多个数组元素
           例： var arr=【1,2,3】；
                   arr.push(4,'严浩翔') ；
                   console.log(arr) ;   输出为 【1，2，3，4，‘ 严浩翔 ’】
            push()完毕后返回的是新数组的长度，即      console.log(arr.push(4,'严浩翔'))     输出是5
        

​      (2) unshift（）---------  在数组的开头 添加一个或多个数组元素 
​                                             也是返回新数组的长度
​        
​      (3) pop（）---------  删除数组的最后一个元素
​                                         返回值是最后一个要删除的元素本身

​      (4) shift () --------  删除数组中的第一个元素
​                                    返回值也是数组的第一个元素

**2》数组排序方法 ：**
         (1)翻转数组  reverse（）；
            var arr=['严浩翔','刘耀文','马嘉祺'];
            arr.reverse();
            console.log(arr);
            

​        (2)数组排序 sort();  
​               var arr2=[3,7,4,1];
​               arr1.sort();         【如果这样写，只能实现一位数的排序】
​               console.log(arr2);
​        

        完美写法： arr1.sort(function(a,b){
                return a-b;      升序    b-a是降序
        }); 

**3》数组内元素查找【去重】**
          (1)indexOf(数组元素)  返回数组中该元素的第一个索引号
                               找不到就返回-1

​          (2)lastindexOf(数组元素)
​                               返回数组中该元素的最后一个索引号
​     案例：数组中的去重【核心算法：遍历旧数组，在新数组中查找旧数组的元素，如果新数组中有就不存了，如果没有就存】
​     
**4》数组转化为字符串**
​           (1) toString()
​             例： var arr=[1,2,3];
​                 console.log(arr.toString());   输出为1,2,3

​           (2) join(可以随意设置分隔符，即默认的逗号，)
​             例： console.log(arr.join('-'));  输出为1-2-3
​             
​             
**5》多个数组的合并  concat（）**
​           原数组.concat(要合并的数组)；
​           例： ['hellow'].concat(['world']);
​               即为['hellow','world'];

​           不只是数组，concat里面也可以放对象，数等等
​           例： [1,2,3].concat(4,5,6);
​                [].concat({a:1},{b:2});
​             
**6》提取数组的一部分 slice()**
​           var a=['a','b','c'];
​           a.slice(0)  //即输出为['a','b','c']
​           a.slice(1,2)  //即输出为['b']  包括起始位置，不包括末尾位置
​           a.slice(-2)  //输出为['b','c'] 若为负数，则表示倒数的位置
​           a.slice(-2,-1) // 输出为['b']
​       注意：
​           若arr.slice(a,b)   若a>数组长度，则返回空数组
​                              若a>b  也返回空数组
​                              
​                              
**7》splice()  用于删除原数组中的一部分元素，并加上新元素,返回删除了的值**
​     var a=[1,1,1];
​     a.splice(1,0,2) 即在1号位置删除0个元素，再添上一个2【2加在1号位置】
​                     即[1,2,1,1]   
​                     

     如果只提供一个参数，即把数组分为两部分
                   var a=[1,2,3,4];
                   a.splice(2);  //[3,4]
                   a  //[1,2]

**8》map()   将一个数组中的所有元素传入参数函数(即下列function中的n），然后把每一次的执行结果组成一个新数组返回。**
         【函数里面接收三个值，当前值，当前位置，整个数组】
       例1：var numbers = [1,2,3];
          numbers.map(function(n){
                return n+1;
          });
                  [2,3,4];
       例2：       
**9》forEach（）和 map（）用法很相似，但不返回值**



**10》filter（） 用于过滤数组成员，满足一定条件的数组成员组成一个新数组返回**
      里面可以放函数

​    [1,2,3,4,5].filter(function(elem){
​         return (elem>3);
​    })

    里面也可以跟Boolean 即filter(Boolean) 返回数组元素中布尔值为true的
    例：  var arr=[0,1,'a',false];
         arr.filter(Boolean)  即返回[1,'a']

**11》every()  some()**

​      （1）Array.every（）：全部满足条件

​                     // 是否全部大于0
​                       let a = [1,2,3,4].every(item => {
​                            return item > 0;
​                       });
​                 console.log(a) ;  **// true** 返回是一个布尔值

​      （2）Array.some（）：部分满足条件

​              **判断数组中有没有符合条件的元素，只要遇到符合条件的就退出循环。**

​                            // 是否有部分大于3
​                          let a = [1,2,3,4].some(item => {
​                                      return item > 3;
​                          });
​                          console.log(a); // true

**12》数组内部元素求和  reduce（    ，  ）**

1. 内部可以接受两个参数，一个是一个函数（一个求和的函数），另一个可以不写

   2. 求和函数内部可以接受两个参数，一个是初始值或者前面元素的求和的值，另一个是当前元素的值

      ![0139](C:\Users\lenovo\Desktop\哈哈\0139.png)

**13》Array.find（）找出第一个符合条件的数组成员，没找到返回 undefined。**

const persons = [
    {id: 1, name: 'Jim', age: 22},
    {id: 2, name: 'Alen', age: 17},
    {id: 3, name: 'Lily', age: 20}
]

let a = persons.find(person => {
    return person.id === 2;
});

console.log(a)  // **{id: 2, name: 'Alen', age: 17}**

**14》Array.findIndex（）找出第一个符合条件的数组成员的位置，没找到返回 -1。**

const persons = [
    {id: 1, name: 'Jim', age: 22},
    {id: 2, name: 'Alen', age: 17},
    {id: 3, name: 'Lily', age: 20}
]

let a = persons.findIndex(person => {
    return person.id === 2;
});

console.log(a) **// 1**

**15》Array.includes表示某个值是否在数组里，includes() 不接受函数参数。**

let a = [1,2,3].includes(3);

console.log(a) // true

