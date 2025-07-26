# 1 请求

HTTP请求报文的第一行叫做请求行(request line)，其后继的行叫做首部行(headerline )。请求行有3个字段:方法字段URL字段和HTTP版本字段。方法字段可以取几种不同的值，包括GET、POST、HEADPUT和DELETE。绝大部分的HTTP请求报文使用GET方法。当浏览器请求一个对象时使用GET方法，在URL字段带有请求对象的标识

对于post方法，首部行后面还有实体体（entity body）。首部行后面需要跟一个空行然后就是实体题。首部行可以有多个。具体如下图
![[Pasted image 20250726153621.png]]
2、响应
响应报文它有三个部分:一个初始状态行(slatusline)，首部行(header line)，然后是实体体(enlity body)。实体体部分是报文的主要部分，即它包含了所请求的对象本身。

初始状态行一般包括响应码 200 或者404之类的以及http的版本


![[Pasted image 20250726154156.png]]

ps：常见状态码：
200  OK:请求成功，信息在返回的响应报文中，
301 Moved Permanently:请求的对象已经被永久转移了，新的URL定义在响应报301文的Location:首部行中。客户软件将自动获取新的 URL。
400 BadRequest:一个通用差错代码，指示该请求不能被服务器理解，
404  Not Found:被请求的文档不在服务器上。
505   HTTP Version Not Supported:服务器不支持请求报文使用的 HTTP 协议版本

