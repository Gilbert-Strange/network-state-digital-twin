# Network State Vector Design

## V1.0  
  
### State Vector  
  
state_vector = [  
latency_mean,  
latency_std,  
path_length  
]  
  
### Feature Description  

| Feature      | Meaning                        |
| ------------ | ------------------------------ |
| latency_mean | average latency across flows   |
| latency_std  | standard deviation of latency  |
| path_length  | average hop count              |
  
### Motivation  
  
These features describe the basic latency characteristics of the network at each timestamp.  
  
### Limitations  
  
Does not capture anomaly information.


## V2.0

### Time Features

state_vector = [
latency_mean
latency_std
path_length
anomaly_ratio
]

### Added Feature

| Feature       | Meaning                 |
| ------------- | ----------------------- |
| anomaly_ratio | ratio of anomalous flow |

### Motivation

Anomaly ratio reflects abnormal network behavior detected by anomaly detection module


## V3

### Node Features

node_features = [
degree
packet_rate
flow_count
queue_length
cpu_usage
memory_usage
]

### Added Features

| Feature      | Meaning         | Computable |
| ------------ | --------------- | ---------- |
| degree       | 主机：节点连接数目       | yes        |
| packet_rate  | 主机，路由器：包速率      |            |
| flow_count   | 主机，路由器，交换机：并发流数 |            |
| queue_length | 路由器：排队长度        |            |
| cpu_usage    | 路由器：cpu处理占用     |            |
| memory_usage | 路由器：内存使用情况      |            |

### Edge Features

edge_features =

[
delay
bandwidth
packet_loss
link_utilization
jitter
throughput
]

### Added Features


| Feature          | Meaning            | Computable |
| ---------------- | ------------------ | ---------- |
| delay            | 略                  | yes        |
| bandwidth        | 略                  | yes        |
| packet_loss      | 略                  |            |
| link_utilization | 链路利用率：所用带宽和最大带宽百分比 |            |
| jitter           | 抖动                 |            |
| throughput       | 吞吐量：所用带宽值          |            |

### Time-series Features

time-series_features =  [
latency_mean
latency_std
loss_rate
throughput_mean
packet_rate_std
]

### Added Features


| Feature         | Meaning        | Computable |
| --------------- | -------------- | ---------- |
| latency_mean    | 某条路径           |            |
| latency_std     | 略              |            |
| loss_rate       | 某个时间窗口取均值      |            |
| throughput_mean | 整条路径，一般受限于瓶颈链路 |            |
| packet_rate_std | 针对特定主机/路由器     |            |


# Network State Representation V1.1

## Feature List
node_features  
edge_features  
time_features

---

## Network State Representation

network_state = {
topology,
node_features,
edge_features,
time_features
}

Represents the multi-dimensional state of the network at time t.

---

### Node Features

node_features = [
degree  
packet_rate  
flow_count  
queue_length  
cpu_usage  
memory_usage
]

---

### Edge Features

edge_features = [  
delay  
bandwidth  
packet_loss  
link_utilization  
jitter  
throughput  
]

---

### Time Features  
  
time_features = [  
latency_mean  
latency_std  
loss_rate  
throughput_mean  
packet_rate_std  
]

---

## State Vector V1.1

### Definition  
  
The network state at time t is represented as a state vector:

state_vector_t = [  
degree  
packet_rate
queue_length  
delay  
bandwidth  
packet_loss  
latency_mean  
loss_rate 
]

---

### Time Index
- The network state is indexed by time.  
- t represents a timestamp or time window during which network metrics are collected.  
- The exact time window size will be determined during the data collection and experiment stage.

---

## Data Pipeline


```text
Topology
↓
Node / Edge Metrics Collection
↓
Feature Extraction
↓
Time Aggregation
↓
State Vector
↓
Dataset
```

Network metrics are collected from topology, nodes and edges,  
then aggregated over time windows to construct state vectors  
for dataset generation.

---

## Feature Specification V1.1

| Feature      | Type | Source        | Description               | Computable |
| ------------ | ---- | ------------- | ------------------------- | ---------- |
| degree       | node | topology      | number of connected links | yes        |
| packet_rate  | node | traffic stats | packets per second        | later      |
| flow_count   | node | flow table    | number of active flows    | later      |
| queue_length | node | router buffer | queue size                | later      |
| delay        | edge | link metric   | link latency              | yes        |
| bandwidth    | edge | link config   | link capacity             | yes        |
| packet_loss  | edge | traffic stats | packet loss ratio         | later      |
| latency_mean | time | aggregation   | mean latency in window    | yes        |
| latency_std  | time | aggregation   | latency deviation         | yes        |
| loss_rate    | time | aggregation   | packet loss rate          | yes        |
