#### javascript语言精髓
1. js中的7种数据类型
    * Number
    * Boolean
    * String
    * null
    * undefined
    * Symbol
    * Object
      + array
      + Date
      + Math
      + RegExp
      + ...
2. var、let、const
    + var 声明为函数级作用域 默认在函数内有效
    + let、const 为块级作用域 (一个花括号内有效)
3. prototype
  + 每个函数都有一个`prototype`的对象属性，对象内有一个`constructor`属性，默认指向函数本身
  + 每一个对象都有一个__proto__属性，该属性指向其父类型(构造函数)的`prototype`
4. this在普通函数中的指向
    * 严格模式下 --> undeefined
    * 非严格模式下
      + node --> global
      + 浏览器 --> window
5. label statement （自己去理解）
  * javascript 中语句优先
--------
#### 高阶函数
1. 惰性函数
  * 判断一次就知道你该用哪种，下次在使用就不需要重复判断了
  ```
  function bindEvent(){
    if(window.addEventListener){
      return function(element,type,handler){
        element.addEventListener(type,handler,false);
      } 
    }else{
      return function(element,type,handler){
         element.attachEvent("on"+typem,handler.bind(element,widow.event));
      }
    }
  }
  ```
2. 柯里化
  * 一种允许使用部分函数生成函数的方式
  ```
  function isType(type){
    return function(obj){
      return Object.prototype.toString.call(obj) == "[object " + type + "]";
    }
  }
  var isNumber = isType("Number");
  console.log(isNumber(1));
  console.log(isNumber("s"));

  // 第二种
  function f(n){
    return n * n;
  }
  function g(n){
    return n * 2;
  }

  console.log(f(g(5)));

  function pipe(f,g){
    return function(){
      return f.call(null,g.apply(null,arguments));
    }
  }
  var fn = pipe(f,g);
  console.log(fn(5));
  ```
3. 尾递归
  * 尾调用是指某个函数的最后一步是调用另一个函数
  * 函数调用自身称为递归
  * 如果尾调用自身，称为尾递归
  * 递归很容易栈溢出（stack overflow）
4. Rambda（自己看  有关函数式编程）
5. 反柯里化 (把this当成参数传递进去 不再使用this.)
  ```
    Function.prototype.uncurry = function(){
      return this.call.bind(this);
    }
    //实现push通用化
    var push = Array.prototype.push.uncurry();
    var arr = [];
    push(arr,1);
    push(arr,2);
    push(arr,3);
    console.log(arr);
  ```
  6. 原型和原型链
    在javascript中，每定义一个对象或者函数时，对象中都会包含一些预定义的属性。其中函数对象的一个属性就是原型对象的prototype，普通对象没有prototype属性，但有__proto__属性。并且该__proto__属性指向其父类的prototype属性
   * 每个原型对象prototype中都有一个constructor属性，默认指向函数本身
      + 特殊 Object.prototype 指向Function
   * Function的prototype比较特殊，还是Function
   * 构造函数
      + 使用new关键字调用的函数
      + 构造函数可以实例化出一个对象
      + 返回值 默认返回类的实例
      + 特殊情况
          + 没有返回值 --> 返回类的实例
          + 简单数据类型 --> 返回类的实例
          + 对象类型（复杂数据类型） --> 返回当前return的对象
  