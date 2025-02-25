# MPLS 跨域 VPN (OptionB)


## 组网说明：
- AS100、AS200 使用 OSPF 作为 IGP 协议
- PE1 <=> ASBR1 是 MP-IBGP 关系
- ASBR2  <=> PE2 是MP-IBGP 关系
- ASBR1  <=> ASBR2 是 MP-EBGP 关系
- PE1 <=> PE2 之间的私网路由通过 MP-BGP VPNv4传递


## 地址规划：
- 公网Loop: 10.0.0.X/32
- 公网互联：10.0.AB.X/24
- 私网互联：10.1.AB.X/24
- 私网Loop：10.1.1.X/32


## 配置步骤：
1. OSPF
2. MPLS+LDP
2. VPN-INSTANCE
3. MP-BGP


## 实验要求：
CE1和CE3的loopback0可以互通，不能和CE2或CE4的loopback0互通，
CE2和CE4的loopback0可以互通，不能和CE1或CE3的loopback0互通。
使用 ping -a src.ip dst.ip 进行测试。

## 说明： 


