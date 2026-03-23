# Data Model (Final)

## Network State

network_state = {
topology,
node_features,
edge_features,
time_features
}

---

## State Vector

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

## Dataset

dataset = {
state_vector_1,
state_vector_2,
...
state_vector_t
}