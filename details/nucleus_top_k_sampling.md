# Nucleus Sampling (Top-p) & Top-k

Nucleus (top-p) and Top-k sampling are stochastic decoding methods that introduce controlled randomness to improve text diversity.

## 💡 Overview
Stochastic decoding prevents models from falling into repetitive, boring text generation loops. Instead of picking the argmax, these methods restrict the sampling vocabulary dynamically.

- **Top-k Sampling:** Restricts the next token choices to the top $k$ most likely options.
- **Nucleus (Top-p) Sampling:** Dynamically adjusts the selection pool to include the smallest set of tokens whose cumulative probability exceeds the threshold $p$.

## 📊 Comparison Diagram

```mermaid
graph TD
    Vocab[All Tokens in Vocabulary] --> TopK[Top-k Filter: Keep top k tokens]
    Vocab --> TopP[Top-p Filter: Keep tokens summing to p]
    TopK --> Normalization[Re-normalize & Sample]
    TopP --> Normalization
    style Vocab fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style TopK fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
    style TopP fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
```

---
[⬅️ Back to README](../README.md)
