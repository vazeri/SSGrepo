---
layout: post
title: Traceroute
tags: 🌐
categories: 🌐-NET
---

## Traceroute Mac:
1. 网络实用工具 → TraceRoute

2. 终端命令: 
	traceroute www.baidu.com

traceroute to www.bai.com (221.5.71.179), 64 hops max, 52 byte packets
 1  172.19.16.1 (172.19.16.1)  1.604 ms  1.076 ms  1.154 ms
// 公司网关
 2  172.19.30.1 (172.19.30.1)  1.457 ms  2.395 ms  1.603 ms
// 
 3  210.22.92.253 (210.22.92.253)  2.795 ms  1.783 ms  2.301 ms
// 公司 IP 
 4  58.247.221.177 (58.247.221.177)  2.622 ms  11.930 ms  2.039 ms

 5  139.226.205.149 (139.226.205.149)  4.251 ms  32.822 ms  6.414 ms
 6  * * \*  7  120.83.0.10 (120.83.0.10)  50.592 ms  43.977 ms  44.268 ms
 8  120.80.209.158 (120.80.209.158)  36.879 ms  36.682 ms  38.215 ms
 9  * * * 10  * \* \* 11  221.5.71.179 (221.5.71.179)  44.615 ms  49.477 ms  44.445 ms






## Traceroute Win:

	tracert www.baidu.com
会显示 你到百度网址  所有经过的 路由. 

	-h maximum_hops 指定搜索目标的最大跃点数.  默认最大30个跃点
tracert -h 50 www.baidu.com
// 最多可以支持 50个 跃点

##### Troubleshoot


#### 工作原理
通过向目标发送不同 IP 生存时间 (TTL) 值的“Internet 控制消息协议 (ICMP)”回应数据包，

Tracert诊断程序确定到目标所采取的路由。

要求路径上的每个路由器在转发数据包之前至少将数据包上的 TTL 递减 1。
数据包上的 TTL 减为 0 时，路由器应该将“ICMP 已超时”的消息发回源系统。

Tracert 先发送 TTL 为 1 的回应数据包，并随后的每次发送过程将 TTL 递增 1，直到目标响应或 TTL 达到最大值，从而确定路由。通过检查中间路由器发回的“ICMP 已超时”的消息确定路由。某些路由器不经询问直接丢弃 TTL 过期的数据包，这在 Tracert 实用程序中看不到。
Tracert 命令按顺序打印出返回“ICMP 已超时”消息的路径中的近端路由器接口列表。

如果使用 -d 选项，则 Tracert 实用程序不在每个 IP 地址上查询 DNS。







#### Troubleshoot

用 tracert 确定数据包在网络上的停止位置。

Tracert 实用程序对于解决大网络问题非常有用，

-j host-list 指定 Tracert 实用程序数据包所采用路径中的路由器接口列表。
-w timeout 等待 timeout 为每次回复所指定的毫秒数。
target\_name 目标主机的名称或 IP 地址。

使用 tracert 命令跟踪路径
打开命令提示符，然后键入：

例如，要跟踪从该计算机到的连接路由，请在命令提示行键入：
tracert [url]()





实例:  追踪 vpn 服务器
本机 IP : 172.19.16.166

	tracert 210.22.91.22
1. 172.19.16.1
2. 172.19.30.1 xujian-PC
3. 210.22.92.253
4. 210.22.91.22

分析: 
1. 16.16 DHCP 服务器 ?
2. 30.1 机房 Cisco 路由器
\3. 







