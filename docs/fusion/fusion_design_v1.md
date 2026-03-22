## Fusion Design V1

## Data Sources

- Topology
- Node features
- Edge features
- Time-series features

---

## Fusion Strategy

We adopt feature-level fusion:

- Node, edge and time features are concatenated
- The fused representation forms a unified state vector

---

## Relation to Existing Methods

According to survey literature, this corresponds to:

- Feature-level fusion
- Early fusion

---

## Motivation

- Simple and effective
- Suitable for our structured network data
- Easy to implement and debug
- Compatible with future models (MLP, GNN, etc.)
