####Rides篇
#####一般命令
```angular2html
redis-server --port 6380 指定端口启动redis服务
redis-server configPath(配置文件)
redis-cli -h 127.0.0.1 -p 6379                      //连接测试
redis-cli                                           //进入交互模式
redis-cli PING                                      //测试连接
incr foo                                            //整数回复
GET  foo                                            //字符串回复
KEYS  *                                             //多行回复
redis> CONFIG SET loglevel warning                  //交互模式下热更新配置(部分配置)
CONFIG GET command                                  //获取配置
SELECT 1                                            //切换数据库(默认16个)
KEYS pattern                                        //获得符合规则的键名列表
SET bar 1                                           //创建 bar[键名] 1[键值] 的键
EXISTS bar                                          //bar的键是否存在
DEL bar                                             //删除bar的键
type bar                                            //获得键是bar的数据类型
LPUSH bar                                           //当type是list类型时则增加元素(反之创建)
STRLEN                                              //统计字符串的长度
MGET/MSET                                           //批量设置或获取
------------------------计数形式
set qty (自增1 同等++ 第二参数可加指定数量)
incr(redis计数形式) incr qty:count（count关键字）
----------命令拾遗
incrby key increment                                //增加指定整数
incrby mylist 9(例)
decr key             decrby key decrement           //减少指定的整数
decr mylist(例-自减1)  decrby mylist 9(例)
incrbyfloat key increment                           //增加浮点型
append key " world"(append在获取key的value同时追加第二参数)
---------位操作
GETBIT FOO 0
SETBIT FOO 6 0
一个字节由8个二进制组成（通过位操作能大大提高效率进行i/o）
------------------------散列类型
HSET cat color red
HSET cat price 500
HGET cat price (500)
HMGET cat price color                                //同时获取多个字段
HEXISTS cat price（不存在返回0-字段或键）
HSETNX(等同于HSET区别是当字段存在时HSETNX不尽兴任何操作)
HDEL cat color2                                      //删除字段
HKEYS cat                                            //字段列表
HVALS cat                                            //值列表
HLEN cat                                             //字段的数量
------------------------列表类型
LPUSH                                                //左侧插入数据
RPUSH                                                //右侧插入数据
LPOP                                                 //左侧弹出数据
RPOP                                                 //右侧弹出数据
LLen                                                 //返回列表的长度
LRANGE key 0 2（LRANGE composer -2 -1）               //获取列表片段
LINDEX key number (LINDEX composer 8)                 //获取指定key的值
LINDEX composer -1(最右边索引-1开始)
LSET key 索引 value (LSET composer 0 1222)             //通过索引赋值
LTRIM KEY START END（lrtrim composer 0 1）  //保留片段值
------------------------集合类型
SADD kiss a b c d e f                                  //创建集合
srem kiss d e f                                        //删除集合
SMEMBERS kiss                                          //集合列表展示
-----集合运算
SDIFF  KEY  {ka = a b c,kb = b,c}例: sdiff ka kb = a
SINTER KEY  {ka = a b c,kb = b,c}例: sdiff ka kb = a
SUNION KEY
------------------------有序集合类型
-inf=负无穷，+inf=正无穷
zadd key soure member [score member ...]               //增加元素
例:zadd lm 89 tom 67 peter 100 david
zadd lm 33 tom                                         //修改元素值
ZSCORE lm tom                                          //获取元素值
ZRANGE key strt stop [WITHSCORES]例:zrange lm 0 2      //根据范围获取列表
ZRANGE key strt stop [WITHSCORES]例:zrange lm 0 2 WITHSCORES //根据范围获取列表及值
zrangebyscore key min max 例:zrangebyscore lm 70 80    //根据值范围获取
释:zrangebyscore lm 70 (80； "（ "解释为70到80，但是不包含80
分页:
zrangebyscore lm 60 +inf limit 0 3 释:从第一条取3条
倒序
zrangebyscore lm 100 60 limit 0 3 释:从第一条取3条
叠加记录:
zincrby lm 69 Peter 同 修改元素值不同到是他会叠加
zcard lm                                               //获取元素数量
store key 集合类型的排序
订阅模式
subscribe msg（监听msg列表）
publish msg "111"(向msg推送数据)
模糊匹配订阅
psubscribe msg* (会监听到msg.code这种发布订阅)

-------------------------------------------------
glob
?    //匹配一个字符
*    //匹配任意字符
[]   //匹配括号间的任意字符，可以使用"-"表示一个范围,如a[b-d]可以匹配"ab","ac"等
\x   //匹配字符x，用于转义符号。如果要匹配&那么就是\&
-------------------------------------------------
redis-server /path/test.conf  --loglevel warning    //通过配置文件启动redis-server
PS:作者提供了配置文件的模板，通常存储于源代码的根目录中


事物(multi)
sadd "user:1:following" 2
sadd "user:1:following" 1
exec
生存时间(expire key)
set session:29e3d uid1314
expire session:29e3d 900（秒）
15分钟后当生存时间到了就会消失,返回值0/1
ttl key                         //查看剩余生存时间
persist key 清除生存时间
pexpire key 1000 (针对的是毫秒)
expireat key 截止时间 

```

PS相关小知识
```
string 类型的键最大容量是512 MB（字符串是其他4种类型的基础）
```