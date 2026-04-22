---
title: QoS
类别: Abbr
时间: 2026-04-21
---

### 英文全称

- Quality of Service

### 中文释义

- 服务质量

### 解释

QoS 是网络通信中用于区分和保障不同业务流量性能的机制。通过对流量分类、标记和调度，确保关键业务（如语音、视频）获得优先处理。

### QoS 层级架构（5GC）

#### 5G QoS Model (基于 QoS Flow)

| 层级 | 说明 |
|------|------|
| **Session (PDU Session)** | 用户会话，一个 PDU Session 可包含多个 QoS Flow |
| **QoS Flow** | 5GC 最细粒度的 QoS 单元，[[SMF]] 根据 [[QCI]] 决定每个 Flow 的处理方式 |
| **DRB (Data Radio Bearer)** | 空口承载，无线资源调度的基本单位 |

#### 映射关系

```
UE → QoS Flow → DRB → 无线空口
```

### QCI (QoS Class Identifier)

| QCI | 资源类型 | 优先级 | 时延要求 | 业务示例 |
|-----|---------|--------|---------|---------|
| 1 | GBR | 2 | 100 ms | Conversational Voice |
| 2 | GBR | 4 | 150 ms | Conversational Video |
| 3 | GBR | 3 | 50 ms | Real Time Gaming |
| 4 | GBR | 5 | 300 ms | Buffered Streaming Video |
| 65 | GBR | 0.7 | 75 ms | Mission Critical Voice (如 TCCA) |
| 66 | GBR | 2 | 150 ms | Mission Critical Video |
| 69 | GBR | 0.5 | 60 ms | Mission Critical Data |
| 70 | GBR | 5.5 | 200 ms | V2X |
| 8 | Non-GBR | 80 | 300 ms | 普通互联网业务 |
| 9 | Non-GBR | 90 | 300 ms | 视频（默认 bearer） |

### 4G LTE QoS 架构

LTE 使用 EPS Bearer 体系：

| 层级 | 说明 |
|------|------|
| **EPS Bearer** | 端到端的承载，从 UE 到 P-GW |
| **E-RAB** | UE 到 eNB 的无线承载 |
| **S1 Bearer** | eNB 到 S-GW 的承载 |
| **S5/S8 Bearer** | S-GW 到 P-GW 的承载 |

### 5G vs 4G QoS 对比

| 特性 | 5GC (SA) | EPC (NSA/LTE) |
|------|----------|---------------|
| **最小粒度** | QoS Flow（精细化） | EPS Bearer |
| **核心差异** | [[SMF]] 动态下发 QoS 规则 | PCRF 预配置策略 |
| **反射式 QoS** | 支持（终端可自主触发） | 不支持 |
| **网络切片 + QoS** | 切片内可独立配置 | 无切片概念 |

### 关键参数

| 参数 | 说明 |
|------|------|
| **MBR (Maximum Bit Rate)** | 最大比特率 |
| **GBR** | 保证比特率（语音、视频通话必需） |
| **Non-GBR** | 不保证速率（如浏览、视频缓冲） |
| **ARP (Allocation and Retention Priority)** | 资源分配优先级 |
| **5QI** | 5G QoS 指示器（对应 QCI） |

### 相关概念

- [[QCI]] - QoS Class Identifier
- [[SMF]] - 会话管理，决定 QoS 策略
- [[UPF]] - 用户面执行 QoS 调度
- [[eMBB]] - 大带宽业务，需高 QoS
- [[URLLC]] - 超低时延业务，最高优先级
- [[VoNR]] / [[VoLTE]] - 语音业务，GBR 保障

> 反向链接: [[QCI]] 决定了每个业务的优先级和调度策略，是理解 QoS 的入口
