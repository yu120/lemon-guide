<div style="color:#16b0ff;font-size:50px;font-weight: 900;text-shadow: 5px 5px 10px var(--theme-color);font-family: 'Comic Sans MS';">Subject</div>

<span style="color:#16b0ff;font-size:20px;font-weight: 900;font-family: 'Comic Sans MS';">Introduction</span>：收纳专题相关的知识总结！

[TOC]

# Redis

## 线程模型

Redis内部使用文件事件处理器File Event Handler，这个文件事件处理器是单线程的所以Redis才叫做单线程的模型。它采用I/O多路复用机制同时监听多个Socket，将产生事件的Socket压入到内存队列中，事件分派器根据Socket上的事件类型来选择对应的事件处理器来进行处理。文件事件处理器包含5个部分：

- 多个Socket
- I/O多路复用程序
- Scocket队列
- 文件事件分派器
- 事件处理器(连接应答处理器、命令请求处理器、命令回复处理器)

客户端与redis的一次通信过程：

![Redis请求过程](images/Subject/Redis请求过程.png)

- **请求类型1**：`客户端发起建立连接的请求`
  - 服务端会产生一个AE_READABLE事件，IO多路复用程序接收到server socket事件后，将该socket压入队列中
  - 文件事件分派器从队列中获取socket，交给连接应答处理器，创建一个可以和客户端交流的socket01
  - 将socket01的AE_READABLE事件与命令请求处理器关联

- **请求类型2**：`客户端发起set key value请求`
  - socket01产生AE_READABLE事件，socket01压入队列
  - 将获取到的socket01与命令请求处理器关联
  - 命令请求处理器读取socket01中的key value，并在内存中完成对应的设置
  - 将socket01的AE_WRITABLE事件与命令回复处理器关联

- **请求类型3**：`服务端返回结果`
  - Redis中的socket01会产生一个AE_WRITABLE事件，压入到队列中
  - 将获取到的socket01与命令回复处理器关联
  - 回复处理器对socket01输入操作结果，如ok。之后解除socket01的AE_WRITABLE事件与命令回复处理器的关联



### 效率高

- `纯内存操作`：数据存放在内存中，内存的响应时间大约是100纳秒，这是Redis每秒万亿级别访问的重要基础
- `非阻塞的I/O多路复用机制`：Redis采用epoll做为I/O多路复用技术的实现，再加上Redis自身的事件处理模型将epoll中的连接，读写，关闭都转换为了时间，不在I/O上浪费过多的时间
- `C语言实现`：距离操作系统更近，执行速度会更快
- `单线程避免切换开销`：单线程避免了多线程上下文切换的时间开销，预防了多线程可能产生的竞争问题



## 数据结构



## 热点数据



## 双写一致性

如何保证缓存和数据库的双写一致性？



## 缓存问题

### 缓存雪崩

### 缓存击穿

### 缓存穿透



# Netty

## 线程模型

## 单机支持百万连接

## 长连接心跳保活机制

## 时间轮



# MySQL

## 数据结构

## 内存设计

## 索引设计



# RocketMQ



# Thread Pool



# Register

## 多数据中心方案

## 百万服务访问



# 问题定位

## CPU飙高

## 内存飙高

## 频繁GC

## 死锁



# 服务治理

## 限流

### 固定时间窗口

### 滑动时间窗口

### 漏桶算法

### 令牌桶算法

### 分布式限流

## 熔断

## 降级

