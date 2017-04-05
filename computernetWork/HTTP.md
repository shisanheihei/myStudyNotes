##超文本传输协议  
 > HTTP协议定义了浏览器怎么想万维网服务器请求万维网文档，以及服务器怎么把文档传送给浏览器的
 #### 万维网的工作流程  
 每个万维网网点有一个服务器进程，不断的监听这TCP的端口80，以便发现是否有浏览器向它发送连接建立的请求，一旦监听到连接建立请求并建立TCP连接之后，浏览器就想万维网发送浏览某个页面的请求，服务器就返回所请求的
 页面，最后释放TCP连接。浏览器的请求和响应交互都必须按照规定的格式和遵循一定的规则，这些规则和格式就是HTTP协议。
 #### 长连接和短链接
 1. 长连接：建立一次TCP协议可以一段时间内保持这个连接，可以持续的发送HTTP的请求报文和响应报文。  
 * 非涟水室连接：一次发送等到响应后继续发送。
 * 流水式连接：直接发送不需要等待响应。
 2. 短链接： 建立TCP连接后发送一次HTTP的请求和响应报文后就直接关闭TCP连接。
 #### HTTP的报文
 1. 请求报文
 * HTTP请求报文的方法：get （请求读取URL的标识信息） POST（给服务器添加信息） option、put、head、delete、trace、connect。
 * POST方法将请求参数封装在HTTP请求数据中，以名称/值的形式出现，可以传输大量数据，这样POST方式对传送的数据大小没有限制，而且也不会显示在URL中。
 * 以get的报文为例：
 ```
 GET /search?hl=zh-CN&source=hp&q=domety&aq=f&oq= HTTP/1.1  
Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-excel, application/vnd.ms-powerpoint, 
application/msword, application/x-silverlight, application/x-shockwave-flash, */*  
Referer: <a href="http://www.google.cn/">http://www.google.cn/</a>  
Accept-Language: zh-cn  
Accept-Encoding: gzip, deflate  
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; TheWorld)  
Host: <a href="http://www.google.cn">www.google.cn</a>  
Connection: Keep-Alive  
Cookie: PREF=ID=80a06da87be9ae3c:U=f7167333e2c3b714:NW=1:TM=1261551909:LM=1261551917:S=ybYcq2wpfefs4V9g; 
NID=31=ojj8d-IygaEtSxLgaJmqSjVhCspkviJrB6omjamNrSm8lZhKy_yMfO2M4QMRKcH1g0iQv9u-2hfBW7bUFwVh7pGaRUb0RnHcJU37y-
FxlRugatx63JLv7CWMD6UB_O_r  
 ```
 * 第一行：是请求报文的方法和URL及HTTP的协议。第二行**accepte**是列出了浏览器可以接收的媒体数据类型。第三**referer**指向的地址。第四行**accept-Language**告知服务器浏览器能够处理的自然语言集（中文、英文等）。zh-CN中文简体。
 第五行**Accept-Encoding**是浏览器用来告知服务器它能够支持的内容编码及内容编码的优先级顺序，可一次性指定多种内容编码。gzip：有文件压缩程序gzip生成的编码格式。deflate：组合使用zlib格式和deflate压缩算法生成的编码格式。sdch： Shared Dictionary Compression over HTTP字典压缩算法。
 第六行**User-Agent**代表浏览器信息。第七行**host**代表服务器域名。第八行**connection**代表是长连接还是短链接。第八行：**cookies**代表用户信息。
 2. 响应报文
 ```
 HTTP/1.1 200 OK
Date: Sat, 31 Dec 2005 23:59:59 GMT
Content-Type: text/html;charset=ISO-8859-1
Content-Length: 122
```
 * 状态码：
    * 1xx：指示信息--表示请求已接收，继续处理。
    * 2xx：成功--表示请求已被成功接收、理解、接受。
    * 3xx：重定向--要完成请求必须进行更进一步的操作。
    * 4xx：客户端错误--请求有语法错误或请求无法实现。
    * 5xx：服务器端错误--服务器未能实现合法的请求。
 * 常见状态吗
     * 200 OK：客户端请求成功。
     * 400 Bad Request：客户端请求有语法错误，不能被服务器所理解。
     * 401 Unauthorized：请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用。
     * 403 Forbidden：服务器收到请求，但是拒绝提供服务。
     * 404 Not Found：请求资源不存在，举个例子：输入了错误的URL。
     * 500 Internal Server Error：服务器发生不可预期的错误。
     * 503 Server Unavailable：服务器当前不能处理客户端的请求，一段时间后可能恢复正常，举个例子：HTTP/1.1 200 OK（CRLF）。
#### Cookie的工作原理
 * 当用户浏览某个使用cookie的网站时，该网站的服务器就为用户产生一个唯一的识别码，并以此在服务器端产生一个项目，并在给用户的响应报文中添加一个叫Set——cookie的首部行
 * 当用户收到这个响应时，浏览器就在它管理的cookie文件中添加一行，其中包括这个服务器的主机名和set-cookie的识别码，以后此用户在此浏览这个网站时，每发送一个http的请求报文时，浏览器就回从其cookie文件中取出这个识别码，并放在http的请求报文中。如get的cookie的请求。
 
 
