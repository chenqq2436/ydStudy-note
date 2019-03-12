#### 你不知道的HTML
1. 前端实现跨域的几种方式
    * jsonp
2. 同源策略
    * 所谓同源是指：域名、端口、协议都相同
    * 提交表单不受同源策略控制
    * 浏览器不同的域名不能访问对应的coolie，但是内部的表单没有限制
    * 非同源，以下三种行为受到限制
        +  Cookie、localStorage、indexDB
        + Dom无法获得
        + ajax请求不能发送
3. cookie
    * 如下: test1和test2就属于二级域名 baidu.com属于一级域名
        http://test1.baidu.com/a.html

        document.domain = "baidu.com";
        document.cookie = "abc";

        http://test2.baidu.com/a.html;

        var allCookie = document.cookie;
4. 如何突破同源策略
    * HTML标签
        img、iframe、script(jsonp)、link(background)
5. jsonp跨域只支持get请求