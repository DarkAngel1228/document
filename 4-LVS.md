### LVS负载均衡简介
LVS（Linux Virtual Server）即Linux虚拟服务器。
是由章文嵩博士主导的开源负载均衡项目，目前LVS已经被集成到Linux内核模块中。该项目在Linux内核中实现了基于IP的数据请求负载均衡调度方案。



### LVS的负载均衡算法
- 静态算法
静态：根据LVS本身自由的固定的算法分发用户请求。
1. 轮询（Round Robin 简写’rr’）：轮询算法假设所有的服务器处理请求的能力都一样的，调度器会把所有的请求平均分配给每个真实服务器。（同Nginx的轮
2. 加权轮询（Weight Round Robin 简写’wrr’）：安装权重比例分配用户请求。权重越高，被分配到处理的请求越多。（同Nginx的权重）
3. 源地址散列（Source Hash 简写’sh’）：同一个用户ip的请求，会由同一个RS来处理。（同Nginx的ip_hash）
4. 目标地址散列（Destination Hash 简写’dh’）：根据url的不同，请求到不同的RS。（同Nginx的url_hash）
- 动态算法
动态：会根据流量的不同，或者服务器的压力不同来分配用户请求，这是动态计算的。
1. 最小连接数（Least Connections 简写’lc’）：把新的连接请求分配到当前连接数最小的服务器。
2. 加权最少连接数（Weight Least Connections 简写’wlc’）：服务器的处理性能用数值来代表，权重越大处理的请求越多。Real Server 有可能会存在性能上
动态获取不同服务器的负载状况，把请求分发到性能好并且比较空闲的服务器。



- 总结：LVS在实际使用过程中，负载均衡算法用的较多的分别为wlc或wrr，简单易用。
