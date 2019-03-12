#### ES6在企业中的运用
1. 新特性-模块-现有模块
    + AMD
    + CMD
    + commonjs
    + UMD
2. 模块语法
    + es6
        `import {$} from 'jquery.js';`
        `export {$};`
    + AMD
    `var $ = require('jquery.js')['$'];`
    `export.$ = $;`
3. 期刊 为何ES Module如此姗姗来迟 https://segmentfault.com/a/1190000004940294
4. 数组
    `var arr1 = [1,2,3];`
    `var arr2 = [...arr1]; //其实是对arr1的浅拷贝`
    + 浅拷贝的意思是： 也就相当于把原对象赋值给了一个新对象。 影响：操作任何一边另一边都会受到影响
5. 函数
    + rest参数(剩余参数)
        + 如下args就等于[3,4]
    ```
    function aaa(a,b...args){
        console.log(args);
    }
    aaa(1,2,3,4);
    ```
6. ES6 promise
    ```
        function async(){
            return new Promise((resolve,reject)=>{

                window.setTimeout(()=>{resolve(123)},1000)
            })
        }
        async().then(function(res){
            console.log(res);
        });
    ```
    ES5 写法
    ```
    function async(callback){
        window.setTimeout(()=>{
            callback();
        },1000)
    }
    async(function(){
        xxx
    });
    ```
7. es5-shim
8. babel 编译器
9. 构建工具 gulp webpack grunt
