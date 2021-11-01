### Keepalived高可用
两台业务系统启动着相同的服务，如果有一台故障，另一台自动接管，我们将这个称为高可用
### Keepalived原理
- Keepalived高可用服务对之间的故障切换转移，是通过 VRRP (Virtual Router Redundancy Protocol ,虚拟路由器冗余协议）来实现的。

- 在 Keepalived服务正常工作时，主 Master节点会不断地向备节点发送（多播的方式）心跳消息，用以告诉备Backup节点自己还活看，当主 Master节点发生故障时，就无法发送心跳消息，备节点也就因此无法继续检测到来自主 Master节点的心跳了，于是调用自身的接管程序，接管主Master节点的 IP资源及服务。而当主 Master节点恢复时，备Backup节点又会释放主节点故障时自身接管的IP资源及服务，恢复到原来的备用角色。

- 那么，什么是VRRP呢？
VRRP ,全 称 Virtual Router Redundancy Protocol ,中文名为虚拟路由冗余协议 ，VRRP的出现就是为了解决静态踣甶的单点故障问题，VRRP是通过一种竞选机制来将路由的任务交给某台VRRP路由器的。

### Keepalived脑裂现象
- 概念

由于某些原因,导致两台keepalived高可用服务器在指定时间内,无法检测到对方存活心
- 可能出现的原因
  - 1、服务器网线松动等网络故障; 
  - 2、服务器硬件故障发生损坏现象而
  - 3、主备都开启了firewalld 防火墙。
  - 4、在Keepalived nginx 架构中,当Nginx宕机,
  
- 解决方案

所以需要编写一个检测nginx的存活状态的脚本,如果nginx不存活,则kill掉宕掉的ngin


### Keepalived双主热备
在Keepalived双机主备基础上，设置互为主备就是双主热备
Keepalived采用dns轮询访问主机