#### ES6
1. polyfill
2. const、let
    * const声明常量 一旦创建就不可以修改
    * const比较符合函数式编程
    * 本质的区别 编译器内部对处理机制
3. 对象的解构
4. 模板字符串
    * 判断字符串中是否 包含某个字符 String.prototype.includes
5. Object.setPrototypeOf、Object.getPrototypeOf 设置和获取对象的原型对象
    Object.setPrototypeOf(对象,目标原型对象)
    Object.getPrototypeOf(对象)
6. 可以手动指定__proto__来设置对象的原型对象
7. super关键字
    * 当子类继承父类时，重写父类方法时，可以使用super来调用父类的方法，例如: 
    ```
    var eat = {
        getEat(){
            return "鸡腿";
        }
    }
    var drink = {
        getDrink(){
            return "啤酒";
        }
    }
    var Sunday = {
        __proto__: eat,
        getEat(){
            return super.getEat() + "可口可乐";
        }
    }
    Sunday.getEat();
    ```
8. 函数名.name可以访问到函数的函数名(function 后面的函数名 比 var函数名 权限高)
9. 使用箭头函数 this会绑定到当前对象所属的顶级作用域上 并且一成不变
10. 使用for...of遍历数组
```
    for(var v of arr){  
        console.log(v);
    }
```
11. ES6中的类
    * `class`关键字用于声明一个类  
    * `constructor`是一个类的构造函数 在这个函数里进行对象new时的初化操作
    * 定义方法时采用 `方法名(形参列表){方法体}`  的形式
    * 使用`extends` 实现类和类之间的继承
    * 当一个类继承了某个父类并要重写父类方法时 可以使用`super`关键字访问到父类(注意：构造函数中使用 ```super(参数列表)``` 的形式，一般方法采用  ```super.函数名```  的形式进行使用)
    * 可以使用`set`和`get`关键字进行实现属性的设置和获取
    * 使用`static`定义的属性或方法为静态属性或方法 可以直接使用类名访问 是所有该类实例化出来的对象共享的
    * 使用`#`来定义私有属性或方法 ，私有属性或方法只能在类的内部调用 不可在外部使用
``` 
class Person{
	constructor(name){
		this.name = name;
	}
	tell(){
		console.log(`我的名字叫${this.name}`);
	}
}
<!-- extends 关键字用于继承某个类 -->
class Chinese extends Person{
	constructor(name){
		super(name);
        this.hobbies = [];
	}
    set hobby(hob){
        this.hobbies.push(hob);
    }
    get hobby(){
        return this.hobbies;
    }
	tell(){
		super.tell();
		console.log("我是一名伟大的中国人");
	}
    static country = "chinese";
    static init(){
        console.log("我是static方法init");
    }
}

var china = new Chinese('张三');
china.tell();
china.hobby = "唱歌";
console.log(china.hobby);
```
12. Set、Map
    * 类似于数组 其中的数据不会重复 
    * Map中的键可以是复杂数据类型
13. 使用export {a,b} 可以采用import {a,b} from xxx来进行导入
    使用export default {a,b} 采用 import data from xxxx  data.a data.b来进行使用
