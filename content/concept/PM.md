---
类别: Abbr
时间: 2026-03-11
---
### 英文全称

- Performance Management

### 中文释义

- 性能管理

### 解释

1. **定义与背景**：  
    性能管理（PM）是电信管理网络（[[TMN]]）五大功能域（[[FCAPS]]：故障、配置、计费、性能、安全）之一。它指的是对通信网络及其网元（如基站、核心网设备、传输设备等）的运行效率和有效性进行监控、测量、分析和报告的过程。
    
2. **核心作用**：
    
    - **监控网络健康度**：通过采集关键性能指标（KPIs, Key Performance Indicators），实时了解网络运行状态。
    - **发现潜在问题**：在用户感知到故障之前，通过性能趋势分析发现网络拥塞、干扰或硬件劣化等问题。
    - **优化网络质量**：为网络优化（Network Optimization）提供数据支撑，例如调整天线参数、扩容带宽、优化切换策略等。
    - **容量规划**：基于历史性能数据预测未来流量增长，指导网络建设和扩容。
3. **常见 PM 计数器/指标示例**：
    
    - **无线接入网** (RAN)：
        - **RRC Connection Setup Success Rate** (RRC连接建立成功率)
        - **ERAB Drop Rate** (E-RAB掉线率)
        - **Throughput** (吞吐量：上行/下行)
        - **Latency** (时延)
        - **PRB Utilization** (物理资源块利用率)
    - **核心网** (Core Network)：
        - **Attach Success Rate** (附着成功率)
        - **PDU Session Establishment Success Rate** (PDU会话建立成功率)
        - **CPU/Memory Usage** (CPU/内存利用率)
    - **传输网** (Transport)：
        - **Bit Error Rate** (BER) (误码率)
        - **Packet Loss Rate** (丢包率)
        - **Jitter** (抖动)
4. **工作流程**：  
    通常包括：**数据采集** (Collection) -> **数据预处理** (Pre-processing) -> **数据存储** (Storage) -> **统计分析** (Analysis) -> **可视化展示** (Visualization/Reporting) -> **告警/优化行动** (Action