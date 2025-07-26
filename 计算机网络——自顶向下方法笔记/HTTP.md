# 1 请求

HTTP请求报文的第一行叫做请求行(request line)，其后继的行叫做首部行(headerline )。请求行有3个字段:方法字段URL字段和HTTP版本字段。方法字段可以取几种不同的值，包括GET、POST、HEADPUT和DELETE。绝大部分的HTTP请求报文使用GET方法。当浏览器请求一个对象时使用GET方法，在URL字段带有请求对象的标识