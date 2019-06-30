# <center>express学习之路由</center>

## 路由
路由是一个选择路径的过程,它决定什么请求该被如何处理,而区别路径的方法便是使用URI区别,用不同的URI定位不同的请求.
### 基础路由
express的基本路由是这样使用的:
``` js
app.METHOD(PATH, HANDLER)
```
其中:
* app是express的实例;
* METHOD是HTTP请求的名称;
* PATH是服务端的路径;
* HANDLER是路由匹配之后执行的函数;

这样,我们便可以简单地写出一个路由,以get请求为例:

``` js
app.get('/', function (req, res) {
  res.send('Hello World!')
})
```
这样,在服务器路由匹配之后,服务器便会执行res.send('Hello World!'),向客户端发出响应了;


### 路由参数

如果需要获得URL传递的参数,可以这样使用路由:
``` js
app.get('/users/:userId/books/:bookId', function (req, res) {
  res.send(req.params)
})
```
这样,当服务端发来的请求路径带有参数时,例如:
```
http://localhost:3000/users/34/books/8989
```
路由就会匹配路径,并将参数放入req.param内:
```
req.params: { "userId": "34", "bookId": "8989" }
```
