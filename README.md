# HttpServer
一个简单的HTTP服务器，预先创建线程，由主线程统一accept。暂时仅能解析GET方法

# 工作流程
1.服务器启动，创建指定数目的线程放进线程池中

2.服务器在指定端口绑定HTTP服务

3.收到一个HTTP请求时，通过条件变量唤醒一个线程，被唤醒线程调用web_server函数提供服务，主线程继续监听请求

4.取出 HTTP 请求头中的method和url。对GET方法，分离出文件路径和？后面的参数。

5.检查路径是否合法，如果以/结尾或url是目录就在路径最后加上index.html

6.如果文件存在，对无参数的请求，发送服务器文件；对有参数请求调用cgi函数执行（未完善）

7.关闭与客户端连接，完成一次请求与回应

# 测试页
http://106.13.221.214/

# 参考
1.UNIX网络编程

2.Tinyhttpd
