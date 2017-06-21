# redis-cli详解

* -r（repeat）代表将命令执行多次。

* -i（interval）代表每隔几秒执行一次命令，但是-i选项必须和-r选项一起使用。**-i的单位是秒，如果每10毫秒执行一次，可以使用-i 0.01**

* -x选项代表从标准输入读取数据作为redis-cli的最后一个参数，例如：
```
echo "world" | redis-cli -x set hello
```

* -a选项输入密码。

* --scan和--patern用于扫描制定模式的键，相当于scan命令。

* **--bigkeys选项使用scan命令对Redis的键进行采样，找到内存占用比较大的键值。**

* --latency选项可以测试客户端到目标Redis的网络延迟。

* --stat选项可以实时获取Redis的重要统计信息。
