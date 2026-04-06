---
title: SRVCC
类别: Abbr
时间: 2026-03-20
---

### 英文全称

- Single Radio Voice Call Continuity

### 中文释义

- 单射频语音呼叫连续性

### 解释

SRVCC 是 LTE 语音（VoLTE）切换到 2G/3G 电路域时的语音连续性技术，确保用户在语音通话过程中从 LTE 移动到 2G/3G 覆盖时语音不中断。

### 触发场景

- VoLTE 用户移出 LTE 覆盖，进入 2G/3G 区域
- LTE 覆盖突然变差需要切换

### 切换流程

1. LTE 无线质量变差，触发 SRVCC 测量
2. IMS 发起 SRVCC 切换请求
3. 在目标 2G/3G 小区建立语音通道
4. 完成切换，释放 LTE 资源

### 与 eSRVCC

- **SRVCC**: 切换到 2G/3G CS 网络
- **eSRVCC**: 增强型 SRVCC，切换更快

### 相关概念

- [[VoLTE]] - LTE 语音
- [[CSFB]] - 电路域回落
- [[IMS]] - IP 多媒体子系统
- [[eNB]] - 4G 基站

