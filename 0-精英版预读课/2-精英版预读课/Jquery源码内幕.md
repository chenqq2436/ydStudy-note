#### Jquery源码内幕
1. 一般new会执行两步
    * 构造函数
    * 寻找原型链(方法)
2. jQuery.fn.extend 和 jQuery.extend的区别
    * 接收参数 Object对象
    * jQuery.fn.extend是挂载到jQuery的原型链上的 (jquery对象才可以访问)
    * jQuery.extend是挂载到jQuery对象上的 ($可以直接访问，只可以使用类名访问($或jQuery 就好比 a.name的形式))
3. jQuery的链式调用采用返回this的形式来实现的
4.
    ```
    $("body").append("<div class="test"></div>");
    $(".test").click(function(){
        console.log(12333);
    });
    // 事件代理 (把事件绑到根元素或父元素，
    通过事件对象 e.target 往下根据条件寻找并进行对应的操作)
	$("body").on("click",".test",function(){
		alert(123);
	});
    ```
5. 自定义事件代理
    ```
    function live(target,type,fn){
        <!-- 将事件都绑定到document身上 -->
        document.addEventListener(type,function(e){
            var tarTemp = e.srcElement || e.target;
            <!-- 判断当元素和事件类型与传入的相同时 执行传入的函数 -->
            if(e.type == type && tarTemp.tagName.toLocalLowerCase == target){
                fn();
            }
        });
    }
    ```
6. 短路表达式
    * 短路表达式会从右往左执行
    * a && b a,b都成立返回b
    * a || b a,b都成立返回a a成立b不成立返回a a不成立b成立返回b
