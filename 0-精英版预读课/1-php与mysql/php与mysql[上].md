### PHP与MYSQL

##### PHP
> PHP是一门后端语言
* 开源的脚本语言不需要编译（类c语言）
* 主要用于web开发领域
* xamppd的文件编写路径在htdocs下
* PHP可以嵌入到HTML中运行
> PHP基本语法
1. PHP基本语法
    * 使用<?php?>进行包裹
    * echo类似js中的console.log用于输出
    * 语句结束符使用;
    * PHP连接字符串使用.
    * 单行注释使用 // 或者# 多行注释使用 /* */
    * PHP中数据类型有 String，Integer，Boolean，null，Object，Array，Recourse，Float
    * PHP 中定义常量使用define(常量名，常量值，true|false) //第三个参数不加默认为false 此时常量名必须大写 定义和访问常量时也不需要加$
    * PHP中异或只有一个为真时才为真 （XOR）
        
2. PHP变量
    * 使用$进行命名
    * 判断变量是否被定义使用isset方法
    * PHP变量仅在块级作用域内有效
    * 将变量提升至全局变量使用 global关键字进行提升
    * 使用$GLOBALS[变量名] 来进行定义超全局变量
3. 引入外部文件
    * 引入外部文件使用 include_once(文件名称)
    require_once(文件名称)
    > 两种方式引入文件的区别
        * require引入文件错误的话会阻断后续正常代码的执行，include引入文件错误则不会阻断后续代码的执行。
4. PHP数组
    * 数组定义的语法为 array(0=>'值0',1=>'值1',...)
    * 数组使用的方法和js基本类似
    * 使用json_encode方法可以用于打印整个数组
5. PHP session（会话机制）
    * session_start(); 用于启动session服务 一般在配置文件中启动一次即可
    * $_SESSION[变量名] 一般用于存储和获取值
6. PHP中接收form表单提交的参数
    `$_GET`[参数名]用于接收get请求的参数
    `$_POST`[参数名]用于接收post请求的参数
    `$_REQUEST`[参数名]用于接收GET/post请求的参数
7. GET/POST请求的参数信息
    * get请求的参数信息在url中可见
    * post请求的参数信息可以在请求头Header中的Form Data中查看
8. 防止中文乱码可在PHP中使用header方法进行设置  
    * `header('Content-type:application/json;charset=utf-8');`
9. js阻止事件的默认行为 `e.preventDefault();`

> PHPMYAdmin
1. Mysql是一个关系型数据库
2. PHPMYAdmin是一个用于操作mysql的图形化界面的工具

> PHP与mysql
1. php连接mysql
    ```
    // 创建一个mysql的连接池 PHP7以上使用mysqli_connect方法进行连接
    //参数依次为 数据库地址，用户名，密码，数据库名
    $con = mysqli_connect("localhost","root",'');
    if(!$con){
        die('Cloud not connect:'.mysqli_error($con));
    }else{
        echo '连接成功'.json_encode($con);
    }
    mysqli_close($con);
    ```
    `mysqli_set_charset('utf8') 或者 mysqli_query("连接池","set names utf8")` 用于解决乱码问题
2. 增删改操作
    ```
    //自定义新增sql语句，以新增为例
    $sql = "insert into 表名 ("键名",...)" values ("键对应的值"...)
    mysqli_query(连接池对象,sql语句);
    if($res){
        echo "操作成功";
    }else{
        mysqli_error($con);
    }
    ```
3. 查询操作
    ``` 
    $sql = "select * from students"
    $res = mysqli_query($con,$sql);
    while($item = mysql_fetch_array($res)){
        echo $item["属性名"]
    }
    mysql_fetch_array方法用于遍历sql查询到的结果
    ```
4. array_push方法 用于向数组中添加新元素

> PHP PDO
1. 如何使用PDO
    ```
        $dbms = "mysql"; //定义当前数据库的类型
        $host = "localhost";
        $dbname = "admin";
        $username = "root";
        $psd = "";
        $dsn = "$dbms:host=$host;dbname=$dbname";
        try{
            //创建PDO对象
            $dbh = new PDO($dsn,$username,$psd);
            //as 就相当于定义了一个变量 并将查询到的值赋给该变量
            foreach($dbh->query("select * from students") as $item){
                print_r($item);
            }
        }catch(DBOException $err){
            echo "error".$err.getMessage();
        }
        
    ``` 
2. echo/print/print_r的区别
   * echo 可以输出一个或者多个字符串
   * print 只能输出简单类型 如int，string等
   * print 可以输出复杂类型的变量 如数组对象等
3. -> 和 => 的区别
    * -> 是对象成员访问符号
    * => 是数组成员访问符号
4. 双引号和单引号的区别
    * 双引号会自动解析变量 而 单引号则会当成字符串进行输出
5. .连接时注意 非空非数字字符串会转化成0
6. $dbh.exec(sql语句); 也可以用于sql操作