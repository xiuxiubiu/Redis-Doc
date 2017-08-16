# Pipeline

**Pipeline是非原子的**

Redis客户端执行一条命令分为如下四个过程：

* 发送命令

* 命令排队

* 命令执行

* 返回结果

其中第一步和第四步称为往返时间（Round Trip Time 缩写：RTT），例如要执行n次hgetall命令，需要消耗n次RTT。而且Redis的客户端和服务端可能部署在不同的机器上，网络请求会大大地降低Redis的吞吐量。Pipeline机制能改善上面的问题，可以有效的节省RTT。它能将一组Redis命令封装，通过一次RTT传输给Redis，再将这组命令的执行结果按顺序返回给客户端。**注意：Pipeline是非原子的。**

redis-cli的--pipe选项就是使用Pipeline机制。但大部分开发人员更倾向于使用高级语言客户端中的Pipeline。
