### 一 . 算法(大数相加)

> 给定两个字符串形式的非负整数 num1 和 num2 计算他们的和

````js
var addStrings = function(num1,num2){
    let sum;
    sum = parseInt(num1) + parseInt(num2);
    return sum.toString();
}
````

### 二 . JS

1. 更改 this 指向有哪些方案

   * `call()`方法

     ````js
     class Person{
         constructor(name,age,gender){
             this.name = name;
             this.age = age;
             this.gender = gender;
         }
         findThis(){
             console.log(this);
         }
     }
     const p1 = new Person('Tom',18,'男');
     p1.findThis();//Person {name: 'Tom', age: 18, gender: '男'}
     
     class Student{
         constructor(name,school){
             this.name = name;
             this.school = school;
         }
     }
     const s1 = new Student('Jack','西南石油大学');//Student {name: 'Jack', school: '西南石油大学'}
     p1.findThis.call(s1);
     ````

   * `apply()`方法

     > apply() 与call（） 非常相似， 不同之处在于提供参数的方式， apply（） 使用参数数组， 而不是参数列表

     ````js
     function add(a,b){
         console.log(this);// Window
         return a+b;
     }
     add(3,6);
     var Person = {
         name:"Jerry",
         age:15
     }
     add.apply(Person,[1,6]);//{name: 'Jerry', age: 15}
     ````

   * `bind()`方法

     > bind() 创建的是一个新的函数（ 称为绑定函数）， 与被调用函数有相同的函数体， 当目标函数被调用时this的值绑定到 bind() 的第一个参数上

     ````js
     function add(a,b){
         console.log(this);// Window
         console.log(a+b);
     }
     var Person = {
         name:"Jerry",
         age:15
     }
     add.bind(Person,3,4);// 只改变了this的指向.没有输出
     add.bind(Person,3,4)();// 改变了this的指向并输出
     // {name: 'Jerry', age: 15}   7
     ````

   * 将`this`存储为变量 , 也可以改变 `this` 的指向

     ````js
     let divItem = document.getElementsByTagName('div')[0];
     divItem.onclick = function(){
         var _this = this;// 将this存储在变量中,而不改变定时器的指向
         setTimeout(function(){
             console.log(_this);// <div></div>
             console.log(this);// 定时器this的指向没有被改变,仍然为window
         },1000);
     }
     ````

2. `bind` , `call` , `apply` 区别是什么 ?

   * 三者都可以传参 , 但参数不同
   * `apply` 传的参数是数组 , 而 `call` 传的是参数列表 
   * `apply` 和 `call` 是一次性传入参数 ,`bind` 可以分多次传入 
   * `bind` 是返回绑定 `this` 之后的函数 , `apply` 和 `call` 则是立即执行

3. 什么是原型

   函数有原型 , 函数有一个属性叫 `prototype` , 函数的这个原型指向一个对象 , 这个对象叫原型对象 , 这个原型对象有一个 	`constructor` , 指向这个函数本身

   在每一个实例对象中 `__proto__` 中同时有一个 `constructor` 属性 , 该属性指向创建该实例的构造函数

   在每一个实例对象中的 `__proto__` 指向构造函数中的 `prototype` 两个是相等的

![img](https://img2018.cnblogs.com/blog/1695219/201910/1695219-20191029155031828-2055436792.png)

JS 就是一门基于原型的语言 , 在软件设计模式中 , 有一种模式叫原型模式 , JS 正式利用这种模式被创建出来的

> 原型模式是用于创建重复的对象，同时又能保证性能，这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。这种模式是实现了一个原型接口，该接口用于创建当前对象的克隆。原型模式的目的是用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象，也就是说利用已有的一个原型对象，可以快速地生成和原型对象一样的新对象实例
>
> 原型：一个可以被复制（或者叫克隆）的一个类，通过复制原型可以创建一个一模一样的新对象，也可以说原型就是一个模板，在设计语言中更准确的说是一个对象模板

原型是**定义了一些公用的属性和方法**，利用原型创建出来的新对象实例会共享原型的所有属性和方法

即使在严格模式下，原型的属性和方法还是会被原型实例所共享的

![898d6eb6bb2f6f47987d99d9babf013.png](https://img.php.cn/upload/image/297/713/174/1604384080667263.png)

4. 什么是原型链

   JS 的原型链就是该编程语言为了实现面向对象编程的一种设计 , 基于原型链 , 可以让 JS 对象拥有封装 , 继承和多态等面向对象特性

5. `instanceof` 判断变量类型的原理是什么

   > `instanceof` 运算符用于测试构造函数的 `prototype` 属性是否出现在对象原型链中的任何位置 (MDN)

   如果 `A instanceof B` , 那么 A 必须是一个对象 , 而 B 必须是一个合法的 JS 函数 , 在马满足这两个条件的前提下

   判断 B 的 `prototype` 属性指向的原型对象 (`B.prototype`) 是否在对象 A 的原型链上

   如果在 , 则返回 `true` , 如果不在 , 则为 `false`

   例如 :

   ````js
   function Person(){}
   const p1 = new Person();
   console.log(p1 instanceof Person); // true
   ````

   * 所有 JavaScript 对象都有 `__proto__` 属性，只有 `Object.prototype.__proto__ === null`
   * 构造函数的 `prototype` 属性指向它的原型对象，而构造函数实例的 `__proto__` 属性也指向该原型对象

   > 每一个构造函数都有一个 `prototype` 属性
   >
   > 这个 `prototype` 属性指向这个构造函数的原型对象
   >
   > 通过 new 关键字 , 可以创建一个构造函数的实例 , 而实例上有一个 `__proto__ ` 属性
   >
   > 实例上 `__proto__` 属性也指向构造函数的原型对象 
   >
   > 通过 `A instanceof B` , 检查 B 的 `prototype` 属性指向的原型对象 , 是否在对象 A 的原型链上

6. 如何实现对象 (构造函数) 的继承

   ````js
   // 创建父类
   function Animal(name){
       // 属性
       this.name = name || 'Animal';
       // 实例方法
       this.sleep = function(){
           console.log(this.name + '正在睡觉');
       }
   }
   ````

   * 原型链继承

     > 核心 : 将父类的实例作为子类的原型

     ````js
     function Cat(){
     
     }
     Cat.prototype = new Animal();
     Cat.prototype.name = 'cat';
     var cat = new Cat();
     console.log(cat.name); // cat
     console.log(cat.eat('fish')); // cat正在吃fish
     console.log(cat.sleep()); // undefined
     console.log(cat instanceof Animal); // true
     console.log(cat instanceof Cat); // true
     ````

     > 特点：
     >
     > 1. 非常纯粹的继承关系，实例是子类的实例，也是父类的实例
     > 2. 父类新增原型方法/原型属性，子类都能访问到
     > 3. 简单，易于实现
     >
     > 缺点：
     >
     > 1. 要想为子类新增属性和方法，必须要在`new Animal()`这样的语句之后执行，**不能放到构造器中**
     > 2. 无法实现多继承
     > 3. 来自原型对象的所有属性被所有实例共享（来自原型对象的引用属性是所有实例共享的）
     > 4. 创建子类实例时，无法向父类构造函数传参

   * 构造继承

     > **核心：**使用父类的构造函数来增强子类实例，等于是复制父类的实例属性给子类（没用到原型）

     ````js
     function Cat(name){
         Animal.call(this);
         this.name = name || 'Tom';
     }
     var cat = new Cat;
     console.log(cat.name);// Tom
     console.log(cat.sleep());// Tom 正在睡觉
     console.log(cat instanceof Animal); // false
     console.log(cat instanceof Cat); // true
     ````

     > 特点：
     >
     > 1. 解决了原型链继承中，子类实例共享父类引用属性的问题
     > 2. 创建子类实例时，可以向父类传递参数
     > 3. 可以实现多继承（call多个父类对象）
     >
     > 缺点：
     >
     > 1. 实例并不是父类的实例，只是子类的实例
     > 2. 只能继承父类的实例属性和方法，不能继承原型属性/方法
     > 3. 无法实现函数复用，每个子类都有父类实例函数的副本，影响性能

   * 实例继承

     > **核心：**为父类实例添加新特性，作为子类实例返回

     ````js
     function Cat(name){
         var instance = new Animal();
         instance.name = name || 'Tom';
         return instance;
     }
     var cat = new Cat();
     // var cat = Cat();
     console.log(cat.name);
     console.log(cat.sleep());
     console.log(cat instanceof Animal);// true
     console.log(cat instanceof Cat);// true
     ````

     > 特点：
     >
     > 1. 不限制调用方式，不管是 `new 子类() `还是 `子类() `, 返回的对象具有相同的效果
     >
     > 缺点：
     >
     > 1. 实例是父类的实例，不是子类的实例
     > 2. 不支持多继承

   * 拷贝继承

     ````js
     function Cat(name){
         var animal = new Animal();
         for(var p in animal){
             Cat.prototype[p] = animal[p];
         }
         this.name = name || 'Tom';
     }
     var cat = new Cat();
     console.log(cat.name);
     console.log(cat.sleep());
     console.log(cat instanceof Animal);// false
     console.log(cat instanceof Cat); // true
     ````

     > 特点：
     >
     > 1. 支持多继承
     >
     > 缺点：
     >
     > 1. 效率较低，内存占用高（因为要拷贝父类的属性）
     > 2. 无法获取父类不可枚举的方法（不可枚举方法，不能使用for in 访问到）

   * 组合继承

     > **核心：**通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用

     ````js
     function Cat(name){
       Animal.call(this);
       this.name = name || 'Tom';
     }
     Cat.prototype = new Animal();
     // 组合继承也是需要修复构造函数指向的。
     Cat.prototype.constructor = Cat;
     var cat = new Cat();
     console.log(cat.name);
     console.log(cat.sleep());
     console.log(cat instanceof Animal); // true
     console.log(cat instanceof Cat); // true
     ````

     > 特点：
     >
     > 1. 弥补了方式2的缺陷，可以继承实例属性/方法，也可以继承原型属性/方法
     > 2. 既是子类的实例，也是父类的实例
     > 3. 不存在引用属性共享问题
     > 4. 可传参
     > 5. 函数可复用
     >
     > 缺点：
     >
     > 1. 调用了两次父类构造函数，生成了两份实例（子类实例将子类原型上的那份屏蔽了）

   * 寄生组合继承

     > **核心：**通过寄生方式，砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性，避免的组合继承的缺点

     ````js
     function Cat(name){
       Animal.call(this);
       this.name = name || 'Tom';
     }
     (function(){
       // 创建一个没有实例方法的类
       var Super = function(){};
       Super.prototype = Animal.prototype;
       //将实例作为子类的原型
       Cat.prototype = new Super();
     })();
     var cat = new Cat();
     console.log(cat.name);
     console.log(cat.sleep());
     console.log(cat instanceof Animal); // true
     console.log(cat instanceof Cat); //true
     Cat.prototype.constructor = Cat; // 需要修复下构造函数
     ````

     > 特点：
     >
     > 1. 堪称完美
     >
     > 缺点：
     >
     > 1. 实现较为复杂

