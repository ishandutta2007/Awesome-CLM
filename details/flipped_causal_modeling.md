# Flipped Causal Modeling (Infilling / FIM)

Fill-in-the-Middle (FIM) or Infilling is a data formatting approach that allows causal language models to learn text infilling.

## 💡 Overview
Causal language models normally only generate text forward. FIM reformats documents at the training level by splitting a text into three chunks: Prefix, Middle, and Suffix. The model is trained on a rearranged sequence of: `<PRE> Prefix <SUF> Suffix <MID> Middle`. This allows the model to learn to predict the middle section given the surrounding context.

## 📊 Formatted Sequence Diagram

```mermaid
graph TD
    Original[Original Text: "Prefix Middle Suffix"] --> Rearranged[Rearranged: "<PRE> Prefix <SUF> Suffix <MID> Middle"]
    Rearranged --> CausalModel[Causal Training Loop]
    style Original fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style Rearranged fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style CausalModel fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
```

## 🛠️ Mechanism
- During preprocessing, text is split randomly.
- Sentinel tokens (`<PRE>`, `<SUF>`, `<MID>`) are inserted.
- The standard next-token prediction loss is applied to the rearranged sequence, preserving the autoregressive training framework.

---
[⬅️ Back to README](../README.md)
