# Bidirectional-to-Causal Hybrid (Enc-Dec)

The Encoder-Decoder architecture separates context comprehension (bidirectional) from sequence generation (causal).

## 💡 Overview
Popularized by models like T5 and BART, this design processes the input prompt using a fully bidirectional Encoder. The resulting representations are passed to a Decoder via cross-attention, which uses standard causal masking to generate tokens autoregressively.

## 📊 Architecture Diagram

```mermaid
graph LR
    subgraph Encoder (Bidirectional)
        In1[Input 1] <--> In2[Input 2] <--> In3[Input 3]
    end
    subgraph Decoder (Causal)
        Out1[Output 1] --> Out2[Output 2]
    end
    Encoder ===|Cross-Attention| Decoder
    style In1 fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style In2 fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style In3 fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style Out1 fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
    style Out2 fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
```

## 🛠️ Mechanism
1. **Encoder:** Computes representations $H_{enc} = \text{Encoder}(X)$ where each token can attend to all other tokens.
2. **Decoder:** Computes self-attention on generated tokens causally, and performs cross-attention over $H_{enc}$ at every decoder layer.

---
[⬅️ Back to README](../README.md)
