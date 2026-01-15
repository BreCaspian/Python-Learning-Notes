# 套接字socket

套接字(Socket)：socket 的原意是“插座”，在计算机通信领域，socket 被翻译为“套接字”， 是实现网络编程进行数据传输的一种技术手段,网络上各种各样的网络服务大多都是基于 Socket 来完成通信的。

> Socket是应用层与TCP/IP协议族通信的中间软件抽象层，它是一组接口。它把复杂的TCP/IP协议族隐藏在Socket接口后面，我们无需深入理解tcp/udp协议，socket已经为我们封装好了，我们只需要遵循socket的规定去编程。



## Socket代码书写

**服务端代码**

- 导入Python套接字编程模块：import socket

- 创建套接字

  ```python
  """
  功能：创建套接字
  参数：socket_family  网络地址类型 AF_INET表示ipv4
  	 socket_type  套接字类型 SOCK_STREAM 表示tcp套接字 （也叫流式套接字）
  返回值： 套接字对象
  """
  sockfd = socket.socket(socket_family,socket_type)
  ```

- 绑定地址

  ```python
  """
  功能：绑定本机网络地址
  参数：元组 (ip,port)  ('127.0.0.1',8888)
  """
  sockfd.bind(addr)
  ```

- 设置监听

  ```python
  """
  功能：将套接字设置为监听套接字，确定监听队列大小
  参数：监听队列大小
  """
  sockfd.listen(n)
  ```

- 处理客户端连接请求

  ```python
  """
  功能：阻塞等待处理客户端请求
  返回值：connfd  客户端连接套接字  addr  连接的客户端地址
  """
  connfd,addr = sockfd.accept()
  ```

- 消息收发

  ```python
  """
  功能: 接受客户端消息
  参数：每次最多接收消息的大小
  返回值：接收到的内容
  """
  data = connfd.recv(size)
  
  """
  功能 : 发送消息
  参数 ：要发送的内容  bytes格式
  返回值： 发送的字节数
  """
  n = connfd.send(data)
  ```

- 关闭套接字

  ```python
  # 功能：关闭套接字
  sockfd.close()
  ```

**客户端代码**

- 导入Python套接字编程模块：import socket

- 创建套接字

  ```python
  """
  功能：创建套接字
  参数：socket_family  网络地址类型 AF_INET表示ipv4
  	 socket_type  套接字类型 SOCK_STREAM 表示tcp套接字 （也叫流式套接字）
  返回值： 套接字对象
  """
  sockfd = socket.socket(socket_family,socket_type)
  ```

- 请求连接

  ```python
  """
  功能：连接服务器
  参数：元组 服务器地址
  """
  sockfd.connect(server_addr)
  ```

- 收发消息

  ```python
  """
  功能: 接受客户端消息
  参数：每次最多接收消息的大小
  返回值：接收到的内容
  """
  data = connfd.recv(size)
  
  """
  功能 : 发送消息
  参数 ：要发送的内容  bytes格式
  返回值： 发送的字节数
  """
  n = connfd.send(data)
  ```

  > 注意： 防止两端都阻塞，recv send要配合

- 关闭套接字

