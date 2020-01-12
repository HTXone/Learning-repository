# Socket

socket为 应用层与TCP/IP协议族通信的中间软件抽象层

网络中进程标识通过三元组（IP地址，协议，端口）进行

由Unix的一切皆文件理念 socket为一种特殊的Unix下的文件 而socket函数就是对此文件的读写开关操作

### Socket() 函数

```cpp
int socket(int domain,int type,int protocol);
```

socket函数用于创建一个socket描述符 其唯一标识一个socket 

domain: 协议域/协议族 决定了socket的地址类型 在通信中必须采用对应的地址

type： 指定socket类型 

protocol： 指定协议(为0时 自动选择type类型对应的默认协议)

### bind() 函数

```cpp
int bind(int sockfd,const struct*addr,socklen_t addrlen)
```

bind()函数将一个地址族中的特定地址赋给socket 

sockfd: 通过socket()函数创建的socket描述字

addr: 一个const struct sockaddr* 指针 指向要绑定给sockfd的协议地址 此地址根据地址创建socket时的地址协议族不同而不同

addrlen:地址的长度 

主机字节序： 大端小端模式 不同CPU有不同的字节序类型 字节序为整数在内存中的保存顺序

网络字节序： 4字节的32bit值以0\~7bit，8\~15bit, 16\~23bit,24\~32bit 的顺序进行传输（大端字节序） 

将一个地址绑定到socket的时候应先将主机字节序转换为网络字节序

### listen(),connect()函数

服务器调用socket() bind()之后将调用listen()来监听socket 客户端此时将调用 connect()来发送连接请求

```cpp
int listen(int sockfd,int backlog);

int connect(int sockfd, const struct sockaddr* addr,socklen_t addrlen);
```

listen中 

sockfd:要进行监听的socket描述字

backlog:相应socket可以排队的最大连接个数

connect中

sockfd:客户端socket描述字 

addr: 服务器socket地址

addrlen: socket地址的长度

### accept()函数

当监听到客户端的connect请求后 使用accept函数进行请求处理 处理之后将开始网络I/O操作 

```cpp
int accept(int sockfd,struct sockaddr *addr,sokclen_t *addrlen);
```

sockfd: 服务器socket描述字（服务器开始调用socket()函数生成(监听socket描述字)） 

addr: 指向地址的指针 用于返回客户端的协议地址

addrlen 协议地址的长度 

如何请求接收成功则将返回一个由内核自动生成的新socket描述字 代表返回客户端的TCP连接（服务器的socket描述字在服务器开始调用socket()函数时将随着服务器生命周期一直存在 而accept返回的socket描述字再服务器完成对客户的服务后就关闭）

### read()\write()函数

当服务器和客户端之间一经建立连接后就可以调用网络I/O进行读写操作 （即实现了网络中不同进程间的通信）

read()/write(), recv()/send(), readv()\writev(), recvmsg()\sendmsg(), recvfrom()/sendto()

 

# JAVA下的socket类

基于TCP实现的客户端socket类和服务端ServerSocket类

基于UDP协议的DatagramSocket类

1. java.net.InetAddress类 ： 是对IP地址的封装 其表示的地址包含有主机名和IP地址两部分

2. Socket类： 4种构造函数

   ```java
   Socket (String address,int point) throws UnknownHostException,IOException
   ```

   ```java
   Socket(InetAddress address,int port) throws IOException
   ```

   ....

   

   获取信息：

   ​	获取地址

   ```java
   getInetAddress() //返回一个InetAddress对象
   ```

   ​	获取远程端口

   ```java
   getPort() 		//返回一个Int型的端口名
   ```

   ​	获取本地端口

   ```java
   getLocationPort()	//返回Int本地端口名
   ```

   ​	获取本地地址

   ```java
   getLocationAddress()	//返回一个InetAddress对象
   ```

   从嵌套字中读取数据

   ```java
   getInputStream() throws IOException	//返回一个InputStream对象
   ```

   将信息写入到远程对象上

   ```java
   getOutputStream() throws IOException	//返回一个OutputStream对象
   ```

   关闭网络嵌套字

   ```java
   close() throws IOException
   ```

3. ServerSocket类：
   构造函数：

   ```java
   public ServerSocket(int port,int backlog,InetAddress bindingAddress) throws IOException	//需要使用已有的InetAddress对象进行构建
   ```

   accept()方法：

   ```java
   accept() throws IOException  //返回一个Socket对象 此对象用于和客户端传输数据
   ```

   

