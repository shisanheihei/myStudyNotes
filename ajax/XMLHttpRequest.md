### XMLHttpRequest  
> XMLHttpRequest 是一个 JavaScript 对象,它为客户端提供了在客户端和服务器之间传输数据的功能。这个类的**每个实例都表示一个独立的请求/响应对**。
 ##### 1.构造函数
 ```js
 var request =new XMLHttpRequest();
 ```
 ##### 2.发起一个HTTP的请求  
 * XMLHttpRequest的open方法
 > open 主要是用来初始化HTTP请求的。
 ```js
  request.open(metod,url,async,user,password)
  ```
 1. method是指HTTP的方法（详见HTTP.md）,一般大写。
 2. url是指响应地址，一般使用的是相对文档的内容，跨域请求通常会报错。  
 3. async如果是ture的话为异步，flase为同步。  
 4. user和passowrd的授权的用户的名和密码。  
* setRequestHeader()的方法  
 > 设置请求的主题
 ```js
 request.setRequestHeader("Content-type","text/plain")
 ```
 1. 类型为MIME的类型
 * send方法
 > 发送HTTP的请求
 ```js
 request.send(null);
 ```
 1. send的参数是发送的body，get没有body，所以可以写出null或者是省略。post一般和setrequestHeader一起使用。    
 #### 3. HTTP的响应
 >HTTP的响应主要包括状态码、响应头集合、响应主体
 * 状态码
 status是以数字的形式显示HTTP的状态码、statusText是以文本的形式展示。（详见HTTP.md）
 * 响应头
 getResponseHeader（）和getALLResponseHeader()来查询响应头（响应头的具体内容详见HTTP.md）  
 注意：响应头中会自动忽略cookie  
 * 响应主体
 responseText展示的是文本的形式，responseXML展示的是DOM的形式  
 * readystatechange事件
 我们在响应准备就绪时得到通知，则需要监听readystatechange的事件。
 1. readystate指定了HTTP的请求状态
 UNSENT                      0       open()尚未调用  
 OPENED                      1       open()已经调用  
 HEADERS_RECEIVED            2       接收到头消息  
 LOADING                     3       接收到响应头消息  
 DONE                        4       响应完成  
 ```js
 request.readystate==4&&status==2
 ```
 
