---
title: SBA
类别: Abbr
时间: 2026-04-21
---

### 英文全称

- Service-Based Architecture

### 中文释义

- 基于服务的架构

### 解释

SBA 是 5GC（5G核心网）的核心设计理念，将传统电信网元拆分为多个独立的网络功能（NF），每个 NF 通过标准化的 HTTP/2 API 接口提供服务，实现解耦和灵活调用。

### SBA vs 传统电信架构

| 特性 | SBA (5GC) | 传统架构 (EPC/2G/3G) |
|------|-----------|---------------------|
| **网元形态** | 网络功能 (NF)，可软件化部署 | 专用硬件设备 |
| **接口方式** | 服务化接口 (HTTP/2 API) | 专有协议（如 GTP、Diameter） |
| **调用方式** | NF 间可直接发现并调用服务 | 点对点硬编码连接 |
| **弹性伸缩** | 基于云原生，支持容器化扩缩容 | 扩缩容困难 |
| **创新速度** | 新功能可通过软件升级快速部署 | 依赖硬件更换 |

### 5GC 主要网络功能 (NF)

| NF | 全称 | 功能 |
|----|-----|------|
| [[AMF]] | Access and Mobility Management Function | 接入和移动性管理 |
| [[SMF]] | Session Management Function | 会话管理 |
| [[UPF]] | User Plane Function | 用户面数据转发 |
| **UDM** | Unified Data Management | 统一数据管理（用户数据存储） |
| **AUSF** | Authentication Server Function | 认证服务器 |
| **PCF** | Policy Control Function | 策略控制功能 |
| **NEF** | Network Exposure Function | 网络能力开放 |
| **NRF** | Network Repository Function | 网络注册/发现功能 |
| **NSSF** | Network Slice Selection Function | 网络切片选择 |
| **NWDAF** | Network Data Analytics Function | 网络数据分析 |

### 服务化接口 (SBI)

| 接口 | 协议 | 说明 |
|------|------|------|
| **Namf** | HTTP/2 | AMF 对外服务接口 |
| **Nsmf** | HTTP/2 | SMF 对外服务接口 |
| **Nudm** | HTTP/2 | UDM 对外服务接口 |
| **Nausf** | HTTP/2 | AUSF 对外服务接口 |
| **Npcf** | HTTP/2 | PCF 对外服务接口 |
| **Nnrf** | HTTP/2 | NRF 注册/发现服务 |
| **Nnssf** | HTTP/2 | NSSF 切片选择服务 |
| **Nnef** | HTTP/2 | NEF 能力开放服务 |

### NRF (网络注册功能) - 服务发现机制

NRF 是 SBA 的"服务注册中心"：

1. **注册**：各 NF 启动时向 NRF 注册自己提供的服务
2. **发现**：需要调用服务的 NF 向 NRF 查询可用的服务提供者
3. **选择**：NRF 根据负载、策略等选择合适的 NF 实例

```
UE → gNB → AMF → NRF (查询 SMF/UPF) → SMF → UPF → Data Network
```

### SBA 与网络切片的关系

SBA 架构天然支持网络切片：

- 每个切片可以包含不同的 NF 实例组合
- [[AMF]] 可服务多个切片（跨切片）
- [[SMF]] / [[UPF]] 按需实例化到特定切片
- 切片间资源隔离，独立演进

### 相关概念

- [[5GC]] - SBA 的载体
- [[AMF]] - 接入管理功能
- [[SMF]] - 会话管理功能
- [[UPF]] - 用户面功能
- [[NRF]] - 网络注册功能（服务发现）
- [[SBI]] - 服务化接口

> 反向链接: [[5GC]] 采用 SBA 架构，所有网元通过 HTTP/2 接口互联，实现了真正的云原生核心网
