---
title: CSFB
类别: Abbr
时间: 2026-03-20
---

### 英文全称

- Circuit Switched Fallback

### 中文释义

- 电路域回落

### 解释

CSFB 是 4G 早期部署阶段的语音解决方案，当 UE 在 LTE 网络发起语音呼叫时，回落到 2G/3G 电路交换网络进行通话，通话结束后再返回 LTE。

### 应用场景

- 4G 商用初期，IMS VoLTE 未部署时
- 作为 VoLTE 的语音回落备选方案

### 流程

1. UE 在 LTE 发起语音呼叫请求
2. 网络指示 UE 回落到 2G/3G
3. 在 CS 网络建立语音连接
4. 通话结束后，UE 返回 LTE

### 相关概念

- [[VoLTE]] - LTE 语音
- [[SRVCC]] - 切换中的语音连续性
- [[eNodeB]] - 4G 基站

