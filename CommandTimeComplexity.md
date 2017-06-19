# 命令时间复杂度

<div id="string"></div>

###  字符串命令

| 命令 | 时间复杂度 |
| --- | --- |
| set key value | O(1) |
| get key | O(1) |
| del key [key ...] | O(k)，k是键的个数 |
| mset key value [key value ...] | O(k)，k是键的个数 |
| mget key [key ...] | O(k)，k是键的个数 |
| incr key | O(1) |
| decr key | O(1) |
| incrby key increment | O(1) |
| decrby key decrement | O(1) |
| incrbyfloat key increment | O(1) |
| append key value | O(1) |
| strlen key | O(1) |
| setrange key offset value | O(1) |
| getrange key start end | O(n)，n是字符串长度，由于获取字符串非常快，如果字符串不是很长，可以视同为O(1) |


<div id="hash"></div>

### 哈希命令

| 命令 | 时间复杂度 |
| --- | --- |
| hset key field value | O(1) |
| hget key field | O(1) |
| hdel key field [field ...] | O(k)，k是field个数 |
| hlen key | O(1) |
| hgetall key | O(n)，n是field总数 |
| hmget key field value [field value ...] | O(k)，k是field个数 |
| hmset key field value [field value ...] | O(k)，k是field个数 |
| hexists key field | O(1) |
| hkeys key | O(n)，n是field总数 |
| hvals key | O(n)，n是field总数 |
| hsetnx key field value | O(1) |
| hincrby key field increment | O(1) |
| hincrbyfloat key field increment | O(1) |
| hstrlen key field | O(1) |


<div id="list"></div>

### 列表命令

| 命令 | 时间复杂度 |
| --- | --- |
| rpush key value [value ...] | O(k)，k是元素个数 |
| lpush key value [value ...] | O(k)，k是元素个数 |
| linsert key before&#124;after pivot value | O(n)，n是pivot距离列表头或尾的距离 |
| lrange key start end | O(s+n)，s是start偏移量，n是start到end的范围 |
| lindex key index | O(n)，n是索引的偏移量 |
| llen key | O(1) |
| lpop key | O(1) |
| rpop key | O(1) |
| lrem key count value | O(n)，n是列表长度 |
| ltrim key start end | O(n)，n是要裁剪的元素总数 |
| lset key index value | O(n)，n是索引便宜量 |
| blpop brpop | O(1) |


<div id="unordered_set"></div>

### 无序集合命令

| 命令 | 时间复杂度 |
| --- | --- |
| sadd key element [element ...] | O(k)，k是元素个数 |
| srem key element [element ...] | O(k)，k是元素个数 |
| scard key | O(1) |
| sismember key element | O(1) |
| srandmember key [count] | O(count) |
| spop key | O(1) |
| smembers key | O(n)，n是元素总数 |
| sinter key [key ...] 或者 sinterstore | O(m*k)，k是多个集合中元素最少的个数，m是键个数 |
| sunion key [key ...] 或者 sunionstore | O(k)，k是多个集合元素个数和 |
| sdiff key [key ...] 或者 sdiffstore | O(k)，k是多个集合元素个数和 |


<div id="ordered_set"></div>

### 有序集合命令

| 命令 | 时间复杂度 |
| --- | --- |
| zadd key score member [score member ...] | O(k*log(n))，k是添加成员的个数，n是当前有序集合成员个数 |
| zcard key | O(1) |
| zscord key | O(1) |
| zrank key member <br> zrevrank key member | O(log(n))，n是当前有序集合成员个数 |
| zrem key member [member ...] | O(k*(log(n)))，k是删除成员的个数，n是有序集合成员个数 |
| zincreby key increment member | O(log(n))，n是当前有序集合成员个数 |
| zrange key start end [withscores] <br> zrevrange key start end [withscores] | O(log(n)+k)，k是要获取的成员个数，n是当前有序集合成员个数 |
| zrangebyscore key min max [withscores] <br> zrevrangebyscore key min max [withscores] | O(log(n)+k)，k是要获取的成员个数，n是当前有序集合成员个数 |
| zcount key | O(log(n))，n是当前有序集合成员个数 |
| zremrangebyrank key start end | O(log(n)+k)，k是要删除的成员个数，n是当前有序集合成员个数 |
| zremrangebyscore key min max | 0(log(n)+k)，k是要删除的成员个数，n是当前有序集合成员个数 |
| zinterstore destination numkeys key [key ...] | O(n*k)+O(m*log(m))，n是成员数最小的有序集合成员个数，k是有序集合个数，m是结果集中成员个数 |
| zunionstore destination numkeys key [key ...] | O(n)+O(m*log(m))，n是所有有序集合成员个数和，m是结果集中成员个数 |
