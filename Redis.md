### Memcache与Redis区别：
- 在数据结构上
- 持久化上，
- 容灾恢复机制上
- 内存回收上，Memchached过期数据的删除策略只用了惰性删除，而Redis同时使用了惰性删除和定期删除
- 集群模式上，Memchached没有原生的集群模式，但是Redis目前是原生支持cluster模式的
- Redis支持发布订阅模型、lua脚本、事务等功能，而Memcached不支持。并且，Redis支持更多的编程语言。

### Redis数据类型与应用场景

### Redis持久化机制

### Redis缓存过期与内存淘汰机制

### Redis主从复制原理

### Redis哨兵机制
