---
title: NRF
类别: Abbr
时间: 2026-04-21
---

### 英文全称

- Network Repository Function

### 中文释义

- 网络功能注册与发现服务

### 解释

NRF 是 5GC（5G核心网）的核心网元之一，作为"服务注册中心"和"服务发现引擎"，支撑 [[SBA]] 架构中各网络功能（NF）之间的相互发现和调用。

### NRF 在 5GC 架构中的核心作用

```
┌─────────────────────────────────────────────────────────────┐
│                        5GC (SBA)                              │
│                                                              │
│  ┌─────────┐                                                  │
│  │  NRF   │  ← "服务注册与发现中心"                            │
│  └───┬─────┘                                                  │
│      │                                                        │
│  ┌───┴───┐ ┌───┴───┐ ┌───┴───┐ ┌───┴───┐ ┌───┴───┐           │
│  │ [[AMF]] │ │ [[SMF]] │ │ [[UPF]] │ │ [[UDM]] │ │ [[PCF]] │           │
│  │       │ │       │ │       │ │       │ │       │           │
│  │注册服务│ │发现服务│ │注册服务│ │注册服务│ │注册服务│           │
│  └───────┘ └───────┘ └───────┘ └───────┘ └───────┘           │
└─────────────────────────────────────────────────────────────┘
```

### 核心功能

| 功能 | 说明 |
|------|------|
| **服务注册 (NF Registration)** | 各 NF 启动时向 NRF 注册自己提供的服务 (如 AMF_1, SMF_2) |
| **服务发现 (NF Discovery)** | 需要服务的 NF 向 NRF 查询可用的服务提供者 |
| **服务选择 (NF Selection)** | NRF 根据负载、策略、切片等条件选择最优 NF 实例 |
| **订阅/通知 (Subscription)** | NF 可订阅 NRF 事件 (如某服务实例变更通知) |
| **切片感知** | NRF 支持按切片隔离服务发现 |

### 服务发现流程示例

**场景**: UE 接入时，[[AMF]] 需要选择一个 [[SMF]] 来建立会话

```
1. AMF 向 NRF 发送服务发现请求 (查询 SMF)
   POST /nnrf-disccovery/v1/smf-instances

2. NRF 返回可用的 SMF 列表 (按切片、负载等筛选)
   Response: [SMF_1, SMF_3, SMF_5]

3. AMF 选择一个 SMF (如 SMF_3) 并建立连接
   Nsmf_PDUSession_CreateSMContext
```

### NRF 的服务类型

| NF 类型 | 注册到 NRF 的服务 |
|--------|-----------------|
| [[AMF]] | Namf_Communication, Namf_EventExposure |
| [[SMF]] | Nsmf_PDUSession, Nsmf_EventExposure |
| [[UPF]] | Nupf_EventExposure, Nupf_Stats |
| [[UDM]] | Nudm_UECM, Nudm_SubscriberDataManagement |
| [[PCF]] | Npcf_PolicyControl, Npcf_AMPolicy |
| [[AUSF]] | Nausf_SoR, Nausf_UPUtentication |

### NRF 部署模式

| 模式 | 说明 |
|------|------|
| **国家级 NRF** | 部署在省级/大区，负责跨 [[AMF]] Pool 的 NF 发现 |
| **本地 NRF** | 部署在本地，支持低时延的 NF 发现 |
| **NRF 分层** | 主备 NRF + 本地 NRF，分层协同 |

### 相关概念

- [[SBA]] - NRF 是 SBA 架构的核心使能组件
- [[5GC]] - NRF 所在的 5G 核心网
- [[AMF]] / [[SMF]] / [[UPF]] - 使用 NRF 进行服务发现
- [[SBI]] - NRF 通过 HTTP/2 提供服务化接口

> 反向链接: [[SBI]] 接口体系中，所有 NF 通过 NRF 实现"发现"与"调用"解耦，这是 [[SBA]] 的核心特征
