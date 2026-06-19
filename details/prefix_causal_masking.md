# Prefix Causal Masking (Non-Causal Decoder)

Prefix Causal Masking (or Prefix LM) is an attention mechanism that combines bidirectional attention for a prompt (prefix) and causal attention for the generated continuation.

## 💡 Overview
Unlike standard autoregressive models where even the prompt tokens are masked causally, Prefix LM allows all tokens in the prompt to attend to each other bidirectionally. This helps build a richer context representation of the input before starting sequence generation.

## 📊 Masking Diagram

```mermaid
graph TD
    subgraph Prompt (Bidirectional)
        P1[Prompt 1] <--> P2[Prompt 2]
    end
    subgraph Generation (Causal)
        P1 --> G1[Gen 1]
        P2 --> G1
        G1 --> G2[Gen 2]
        P1 --> G2
        P2 --> G2
    end
    style P1 fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style P2 fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style G1 fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
    style G2 fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
```

## 🛠️ Mechanism
- For indices $i, j \le \text{prefix\_length}$, attention is fully bidirectional: no mask is applied.
- For indices $i > \text{prefix\_length}$, attention is causal: token $i$ can only attend to indices $j \le i$.

---
[⬅️ Back to README](../README.md)
