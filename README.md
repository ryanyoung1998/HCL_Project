# HCL_Project

## 项目简介
本项目是基于 **H3C Cloud Lab** 工具构建的网络实验集合，旨在模拟真实网络场景，验证 H3C 设备（如交换机、路由器）的配置与协议实现。实验涵盖以下方向：

- **基础网络配置**（VLAN、静态路由、DHCP）-未完成

- **动态路由协议**（OSPF、ISIS、BGP）-未完成

- **MPLS VPN**（跨域OptionA/OptionB/OptionC1/OptionC2）**已完成**


---

## 实验环境

- **工具与版本

- **实验平台**: H3C** Cloud Lab (版本: v5.10.3)

- **设备镜像**: H3C Comware V7 (版本: 7.1.075)

- **依赖工具**: Wireshark（抓包分析）、Xshell（终端连接）

---

## 实验文件结构
```plaintext
HCL_Project/
├─mpls_vpn_option_a              # MPLS跨域OptionA实验
│  ├─ConfigDisk                # 设备镜像
│  ├─DeviceConfig              # 设备配置文件
│  ├─SerialFile                # 设备串口日志
│  ├─.gitignore                # Git忽略文件
│  ├─ConfigDisk_backup.zip     # 设备镜像备份
│  ├─deviceversion.txt         # 设备版本信息
│  ├─mpls_vpn_option_a.net       # 实验拓扑
│  ├─mpls_vpn_option_a.png       # 实验拓扑图
│  ├─project.json              # 实验配置文件
│  └─README.md                 # 实验说明文档
├─其他LAB项目
└── README.md                  # 项目说明文档
```

---

## 实验清单

- **1. MPLS跨域VPN(OptionA)实验**
**实验目的**：理解MPLS跨域VPN(OptionA)的工作原理，验证MPLS跨域VPN(OptionA)的配置与实现。

  ![MPLS跨域VPN(OptionA)实验拓扑](./mpls_vpn_option_a_complated/mpls_vpn_option_a.png)


- **2. MPLS跨域VPN(OptionB)实验**
**实验目的**：理解MPLS跨域VPN(OptionB)的工作原理，验证MPLS跨域VPN(OptionB)的配置与实现。

  ![MPLS跨域VPN(OptionB)实验拓扑](./mpls_vpn_option_b_complated/mpls_vpn_option_b.png)


- **3. MPLS跨域VPN(OptionC1)实验**
**实验目的**：理解MPLS跨域VPN(OptionC1)的工作原理，验证MPLS跨域VPN(OptionC1)的配置与实现。

  ![MPLS跨域VPN(OptionC1)实验拓扑](./mpls_vpn_option_c_1_complated/mpls_vpn_option_c_1.png)



- **4. MPLS跨域VPN(OptionC2)实验**
**实验目的**：理解MPLS跨域VPN(OptionC2)的工作原理，验证MPLS跨域VPN(OptionC1)的配置与实现。

  ![MPLS跨域VPN(OptionC2)实验拓扑](./mpls_vpn_option_c_2_complated/mpls_vpn_option_c_2.png)



---

## 挖坑清单

- **1. MPLS跨域VPN-OptionA：**
1. ASBR2 未在 BGP VPN 实例中激活对等体
2. PE1 的 VPN 实例配置中，RT 配置与 ASBR1 的 RT 配置不匹配
3. P2 的 OSPF 配置中，区域号配置错误
4. PE2 的接口配置中，绑定 VPN 实例配置错误
5. ASBR1 的 BGP 配置中， 未在 VPNv4 地址簇激活对等体


- **2. MPLS跨域VPN-OptionB：**
1. ASBR1 未取消对 VPNv4 路由进行 VPN Tag 过滤
2. PE1 VPN 实例配置与 PE2 不匹配
3. P2 OSPF 配置不完整
4. PE2 接口绑定 VPN 实例配置错误
5. CE4 未将业务地址通告至 BGP 中
6. ASBR2 互联接口未启用 MPLS


- **3. MPLS跨域VPN-OptionC1：**
1. ASBR1 peer 10.0.0.1 未使能 label-route-capability
2. ASBR2 route-policy 未应用 mpls-label
3. PE1 peer 10.0.0.6 未配置 ebgp-max-hop
4. PE2 vpn-instance B 未引入 vpn-target 100:2
5. CE4 ipv4 地址簇未通告 Loopback


- **4. MPLS跨域VPN-OptionC2：**
1. ASBR1 route-policy 未添加 mpls-label
2. ASBR2 OSPF 未引入 BGP 路由（PE1 loopback 接口）
3. PE2 peer 10.0.0.1 ebgp-max-hop 跳数太小
4. PE1 vpn-instance B 未引入 vpn-target 200:4
5. CE3 AS 号配置错误