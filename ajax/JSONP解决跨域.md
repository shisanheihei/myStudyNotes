### JSONP解决跨域 
> JSONP是JSON with Padding的略称。它是一个非官方的协议，它允许在服务器端集成Script tags返回至客户端，通过javascript callback的形式实现跨域访问（这仅仅是JSONP简单的实现形式）
#### 同源策略
> 档的来源的**协议**、**主机**、**端口**的任意一个不同就代表是文档的来源不同。js则不能操作不同来源的文档。
XMLHttpRequest是不能完成跨域操作，但是XMLHttpRequest2可以进行跨域操作的。
#### JSONP的实现模式--CallBack
创建一个回调函数，然后在远程服务上调用这个函数并且将JSON 数据形式作为参数传递，完成回调。
我的理解是 在客户端定义好了fucction，然后将fuction以回调的方式传给server，然后用server执行function这个函数
#### JSONP的一个简单例子
1. 前端的代码
```HTML
<script>
       function fuc(data){
         console.log(data.name);
        }
     </script>
     <script src="http://www.baidu.com/api.php?callback=fuc"></script>
 ```
 2.后台的代码
 ```php
 <?php
2     $cb = $_GET['callback'];
3     $data = array(
4                 'name'=> 'zs',
5                 'age'=>18,
6                 'gender'=>true
7             );
8     echo $cb.'('.json_encode($data).')';
9 ?>
```

