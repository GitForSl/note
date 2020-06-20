### Redis的数据结构
* String 最简单也是最通用的数据类型，需要注意的是字符串长度最大为512M<br/>
1.分布式锁，setnx（使用锁一定要注意一点，设置同步设置超时时间expire，redis版本2.8之后，将setnx和expire合并成一个命令保证了原子性操作）<br/>
2.分布式自增id，incr（最大为LONG.MAX）<br/>
3.序列化存储用户信息<br/>
4.命令:set,get,del,mset,mget<br/>

* list 结构是个快速链表（zplist）而不是个数组，所以插入删除操作很快，定位很慢<br/>
1.用来做异步队列<br/>
2.右进左出队列，rpush,lpop,blpop,brpop;llen获取长度<br/>
3.右进右出栈，rpush,rpop

* hash 相当于java里的hashmap，结构数组加链表，存储的值只能为string<br/>
1.命令hset,hget,hgetall,hlen,hmset<br/>
2.内部单个key也可以用来计数<br/>

* set 集合，内部元素是无序的，且是唯一的，字典里的所有value都为NULL<br/>
1.可以用来存储用户中奖的id，点赞id，保证不会重复<br/>
2.命令：sadd，smembers，smember，scard，spop<br/>

* zset 有序集合，key的唯一性，对应的value赋予一个score，进行排序<br/>
1.用来做粉丝列表，key为粉丝id，score为关注时间<br/>
2.用来做成绩排名，key为学生id，score为学生的总成绩<br/>



