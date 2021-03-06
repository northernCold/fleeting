# TSL四次握手

#https #tsl

## TSL基本流程

1. 客户端向服务器端获取公钥
2. 服务器端根据随机数生成`会话密钥`
3. 双方使用`会话密钥`加密通信

第1、2点是TSL握手过程。

## TSL四次握手

1. 第一次握手: 客户端发送`Client Hello`消息，里面包含

   1. 客户端支持的tsl协议版本号
   2. 一个由客户端生成的随机数
   3. 客户端支持的加密方法

2. 第二次握手：服务器端收到消息后，做出回应（`Server Hello`）

   1. 确实使用的tsl协议的版本号
   2. 一个服务器端生成的随机数
   3. 确认使用的加密方法
   4. 服务器证书

3. 第三次握手：首先验证从服务器获取的证书算法有效，如果有效则从中获取到公钥。然后再向服务器发送消息：

   1. 一个使用公钥加密的随机数
   2. 随后使用加密通信通知
   3. 客户端握手结束通知

4. 第四次握手：服务端根据前后生成的3个随机数生成`会话密钥`。然后向客户端发送：

   1. 随后使用加密通信通知
   2. 服务器握手结束通知

## REFRENCE

1. [小林coding|几幅图，拿下 HTTPS](https://www.cnblogs.com/xiaolincoding/p/14274353.html)
2. [小林coding|硬核！30 张图解 HTTP 常见的面试题](https://mp.weixin.qq.com/s/bUy220-ect00N4gnO0697A)
3. [阮一峰|SSL/TLS协议运行机制的概述](http://www.ruanyifeng.com/blog/2014/02/ssl_tls.html)