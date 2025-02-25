# MPLS 跨域 VPN (OptionC 2)


## 组网说明：
- AS100、AS200 内部使用 OSPF 作为 IGP 协议
- ASBR1 <=> ASBR2 之间是 EBGP 关系
- PE1 <=> PE2 之间是 MP-EBGP 多跳关系
- PE1 <=> PE2 之间 LSP 通过 ASBR1、ASBR2 传递 BGP LSP
- PE1 <=> PE2 之间 Loopback 路由通过公网 EBGP 和公网 OSPF 传递
- PE* <=> CE* 之间是 EBGP 关系


## 地址规划：
- 公网Loop: 10.0.0.X/32
- 公网互联：10.0.1X.0/30
- 私网互联：10.1.1X.0/30
- 私网Loop：10.1.1.X/32


## 配置步骤：
1. IGP(OSPF)
2. MPLS + LDP
3. EBGP + route-policy
4. peer label-route-capability
5. MP-EBGP多跳
6. VPN-INSTANCE


## 测试结果：

- CE1 ping CE2

```shell
<CE1>ping -a 10.1.1.1 10.1.1.2
Ping 10.1.1.2 (10.1.1.2) from 10.1.1.1: 56 data bytes, press CTRL+C to break
56 bytes from 10.1.1.2: icmp_seq=0 ttl=253 time=4.020 ms
56 bytes from 10.1.1.2: icmp_seq=1 ttl=253 time=3.334 ms
56 bytes from 10.1.1.2: icmp_seq=2 ttl=253 time=3.667 ms
56 bytes from 10.1.1.2: icmp_seq=3 ttl=253 time=2.761 ms
56 bytes from 10.1.1.2: icmp_seq=4 ttl=253 time=3.286 ms

--- Ping statistics for 10.1.1.2 ---
5 packet(s) transmitted, 5 packet(s) received, 0.0% packet loss
round-trip min/avg/max/std-dev = 2.761/3.414/4.020/0.420 ms
<CE1>
```

- CE3 ping CE4

```shell
<CE3>ping -a 10.1.1.3 10.1.1.4
Ping 10.1.1.4 (10.1.1.4) from 10.1.1.3: 56 data bytes, press CTRL+C to break
56 bytes from 10.1.1.4: icmp_seq=0 ttl=253 time=4.813 ms
56 bytes from 10.1.1.4: icmp_seq=1 ttl=253 time=3.229 ms
56 bytes from 10.1.1.4: icmp_seq=2 ttl=253 time=3.170 ms
56 bytes from 10.1.1.4: icmp_seq=3 ttl=253 time=3.613 ms
56 bytes from 10.1.1.4: icmp_seq=4 ttl=253 time=3.324 ms

--- Ping statistics for 10.1.1.4 ---
5 packet(s) transmitted, 5 packet(s) received, 0.0% packet loss
round-trip min/avg/max/std-dev = 3.170/3.630/4.813/0.611 ms
<CE3>
```

## 说明： 


