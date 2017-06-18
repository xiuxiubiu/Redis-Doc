# 命令时间复杂度

<div id="string"></div>

###  字符串类型

| 命令 | 时间复杂度 |
| --- | --- |
| set key value | 0(1) |
| get key | 0(1) |
| del key [key ...] | 0(k)，k是键的个数 |
| mset key value [key value ...] | 0(k)，k是键的个数 |
| mget key [key ...] | 0(k)，k是键的个数 |
| incr key | 0(1) |
| decr key | 0(1) |
| incrby key increment | 0(1) |
| decrby key decrement | 0(1) |
| incrbyfloat key increment | 0(1) |
| append key value | 0(1) |
| strlen key | 0(1) |
| setrange key offset value | 0(1) |
| getrange key start end | 0(n)，n是字符串长度，由于获取字符串非常快，如果字符串不是很长，可以视同为0(1) |
