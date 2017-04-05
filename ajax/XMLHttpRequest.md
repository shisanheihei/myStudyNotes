### XMLHttpRequest  
> XMLHttpRequest 是一个 JavaScript 对象,它为客户端提供了在客户端和服务器之间传输数据的功能。这个类的**每个实例都表示一个独立的请求/响应对**。
 ##### 1.构造函数
 ```
 var request =new XMLHttpRequest();
 ```
 #### 2.发起一个HTTP的请求  
 * XMLHttpRequest的open方法
 > open 主要是用来初始化HTTP请求的。
 ```
  request.open(metod,url,async,user,password)
  ```
 1. method是指HTTP的方法（详见HTTP.md）,一般大写。
 2. url是指响应地址，一般使用的是相对文档的内容，跨域请求通常会报错。  
 3. async如果是ture的话为异步，flase为同步。  
 4. user和passowrd的授权的用户的名和密码。  
  
 
