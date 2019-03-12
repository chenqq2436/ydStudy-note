### 面向对象
1. 面向对象的特点
    * 封装,继承,多态
2. 面向对象的三个目标
    * 重用性,灵活性，扩展性
3. 面向对象的三个主要特性
    * 对象的行为
    * 对象的状态
    * 对象的标识
4. 定义类的简单格式
    [修饰符] class 类名{
        [成员属性] //也叫成员变量
        [成员方法] //也叫成员函数
    }
5. 完整格式
    [修饰符] class 类名 [extends 父类] implements [接口1,[接口2,...]]{
    [成员属性] //也叫成员变量
    [成员方法] //也叫成员函数
    }
6. 定义类的成员属性
    * 语法：修饰符 $变量名[=默认值] 如public $name = "张三";
    * 注意: 成员属性不可以是带运算符的表达式、变量、方法或函数调用
7. 成员方法定义
    * 语法: [修饰符] function 方法名(参数列表){
        [方法体]
        [return 返回值]
    }
8. 使用new关键字来对类进行实例化
$对象名 = new 类名([实参列表]);
9. 通过类实例化对象-对象中成员的访问
    * 语法: $引用名 = new 类名(构造函数);
    $ 引用名->成员属性 = 赋值; // 给对象的属性赋值
10. 构造方法 和 析构方法
 * 在php中两个__代表私有的
 * 构造方法 [修饰符] function ___construct(形参列表){
     //用于对类初始化的对象进行初始化操作
     [方法体]
 }
 * 析构方法 [修饰符] __destruct(形参列表){
     //用途 可以进行资源的释放 如数据库的关闭
    //当对象被销毁的时候执行 即没有代码再运行了
     [方法体]
 }
11. public private protected
    * public 公共的 构造函数内外都可以进行访问
    * private 和 protected 只能在内部进行访问
12. 访问类型控制权限
    |           |  public   |  private  |  protected  |
    |:---------:|:---------:|:---------:|:-----------:|
    | 在同一类中 |   可以    |    可以    |    可以     |
    | 在类的外部 |   可以    |    不可以  |    不可以    |
    | 父子类中实现继承时 |   可以    |    不可以    |     可以    |
13. 魔术方法
    * 所有魔术方法都需要使用 __ 前缀
    * __set、__get只对private和protected有效 对public无效
    * isset判断某个属性或方法是否存在 unset卸载某个属性或方法
    * __set、__get 配合外部的 -> 使用
    * __isset、__unset 配合外部的isset(对象->属性)、unset(对象->属性)使用
14. 当子类继承父类 并且要重写父类的方法时 使用 parent::方法名 来进行调用父类中的方法（php中没有类似java中的重载 即函数名相同参数列表不同不会被覆盖）
15. 父类中的使用private修饰符修饰的属性或者方法不可以被继承
16. 抽象类
    * 抽象类和抽象方法都是用abstract修饰
    * 含有抽象方法的类必须是抽象类
    * 抽象类不一定非要包含抽象方法，也可以有普通方法
    * 抽象类不能被实例化，必须由子类去继承，并且要实现该抽象类中的所有抽象方法
17. 接口
    * 接口使用interface关键字定义
    * 接口中可以声明常量也可以声明抽象方法（声明常量使用const 关键字 常量名全部大写）
    * 接口中的方法都是抽象方法，不需要使用abstract进行修饰
    * 一个类不能继承多个类 但是可以实现多个接口
18. 静态属性或方法或常量都可以使用类名直接调用 调用方式采用person::name这种形式调用(常量名不需要$)
19. 在类的内部访问常量时需要使用self::常量名
20. php中的关键字
    > final
    + final 关键字可以修饰类和成员方法 不可以修饰成员属性
    + 使用final关键字标识的类不能被继承
    + 使用final关键字标识的方法不能被子类重写
    > static
    + 类中的静态属性和方法可以直接使用类名访问(类名::$静态属性  类名::静态方法)
    + 在类的方法中不能使用$this来引用静态变量和静态方法 需要使用self::静态属性||静态方法
    + 静态方法中不可以使用非静态内容 也就是不能使用$this
    + 静态属性是共享的 也就是new很多对象也是共用一个属性
21. const 是一个在类中定义常量的关键字
    + const 常量名 = 值;
    + 在类的内部使用self::常量名进行访问
    + 外部可以使用类名或对象名::常量名进行访问


----------
#### 代码操作
1. 定义一个类并进行实例化等
```
class Person{
        public function __construct($name,$age){
            $this -> name = $name;
            $this -> age = $age;
            echo "你好.{$this->name}";
            echo "<hr>";
        }
        public function say(){
            echo "name:".$this-> name."age:". $this->age;
        }
        public function __destruct(){
            //用途 可以进行资源的释放 如数据库的关闭
            //当对象被销毁的时候执行 即没有代码再运行了
            echo 'byebye';
        }
    }
    $xiaoming = new Person("xiaoming",22);
    $xiaoming -> say();
```
2. private、protected、魔术方法
```
 class Person{
      public $name = "陈强";
      private $age = 18;
      protected $sex = "男";

      private function say(){
          echo $this -> name."  ".$this -> age."  ".$this -> sex;
      }
      public function __set($key,$val){
        $this -> $key = $val;
      }
      public function __get($key){
        return $this -> $key;
      }
      public function __isset($key){
        return $this -> $key != "" ? true : false;
      }
      public function __unset($key){

      }
  }
  $p = new Person();
  echo $p -> sex;
  echo isset($p -> sex);
  unset($p -> name);
  echo $p -> name;
```