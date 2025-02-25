# MPLS VPN 跨域 OptionC



## 地址规划：

Loopback:10.0.0.X/32 (CE除外)

公网互联：10.0.AB.X/24

私网互联：10.1.AB.X/24

私网地址：10.1.1.X/32 (CE的Loopback)



## 组网说明：

AS100 和 AS200 内部 IGP 协议是 OSPF

PE1 <=> ASBR1 是 IBGP 对等体

ASBR2 <=> PE2 是 IBGP 对等体

ASBR1 <=> ASBR2 是 EBGP 对等体

PE1 <=> PE2 是多跳 MP-EBGP 对等体

PE1 <=> PE2 之间通过 ASBR1、ASBR2 传递 BGP LSP

PE* <=> CE* 是 EBGP 对等体


## 配置步骤：

1. IGP(OSPF)

2. MPLS + LDP

3. IBGP + EBGP

4. 多跳 MP-EBGP

5. label-route-capability

6. VPN-INSTANCE


## 测试结果：



## 说明： 


