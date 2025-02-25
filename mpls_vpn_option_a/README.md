# MPLS 跨域 VPN (OptionA)



## 组网说明：
- AS500、AS600 内部使用 OSPF 作为 IGP 协议
- PE1 <=> ASBR1 之间是 MP-IBGP 关系
- PE2 <=> ASBR2 之间是 MP-IBGP 关系
- ASBR1 <=> ASBR2 之间是 EBGP 关系


## 地址规划：
- 公网Loop：10.0.X.X/32
- 公网互联：10.0.AB.X/24
- 私网互联：10.1.AB.X/24
- 私网地址：10.1.X.X/32


## 配置步骤：
1. IGP(OSPF)
2. MP-IBGP
3. EBGP
4. VPN-INSTANCE


## 实验要求：
- CE1和CE3的loopback0可以互通，不能和CE2或CE4的loopback0互通。
- CE2和CE4的loopback0可以互通，不能和CE1或CE1的loopback0互通。
- 使用 ping  -a  src.ip  dst.ip 进行测试。


## 说明： 


