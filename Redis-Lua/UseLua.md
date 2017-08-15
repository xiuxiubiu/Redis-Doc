# Redis中使用Lua

** 因为Redis是单线程，所以在Redis中执行lua脚本时间过长或死循环，会导致后面的命令被阻塞。 **

#### Lua脚本为Redis开发和运维人员带来的好处：

* Lua脚本在Redis中是源自执行的，执行过程不会插入其它命令。

* 可以使用Lua脚本创造出自己定制的命令，并可以将命令常驻内存，实现复用。

* Lua脚本可以将多条命令一次性打包，减少网络开销。

#### 在Redis中执行Lua脚本有两种方法：

* eval 脚本内容 key个数 key列表 参数列表

    ```
eval 'return {KEYS[1],KEYS[2],ARGV[1],ARGV[2]}' 2 key1 key2 arg1 arg2
    ```
    eval的第一个参数是Lua脚本程序，这段脚本不需要也不应该定义函数。
    eval的第二个参数是参数个数。此参数后参数个数内的参数表示Redis中用到的键，可以通过全局变量KEYS数组访问。其余为附加参数，可以通过全局变量ARGV数组访问。

    如果脚本较长，可以使用redis-cli --eval执行文件。

* evalsha 脚本SHA1值 key个数 key列表 参数列表

    ```
evalsha a42059b356c875f0717db19a51f6aaca9ae659ea
    ```

#### script命令：

* script exists script [script ...]

    检查脚本是否存在脚本缓存里
    ```
scirpt exists a42059b356c875f0717db19a51f6aaca9ae659ea a42059b356c875f0717db19a51f6aaca9ae659e
    ```

* script flush

    清空Lua脚本缓存

* script kill

    杀死当前正在运行的Lua脚本，当且仅当这个脚本没有执行过任何写操作时，这个命令才生效。

* script load script

    加载脚本到脚本缓存中中
