# Next-Token Prediction (Standard CLM)

Next-token prediction is the standard objective for training autoregressive language models.

## 💡 Overview
Given a sequence of tokens $(x_1, x_2, \dots, x_{t-1})$, the model predicts the probability distribution of the next token $x_t$. The training objective is to minimize the negative log-likelihood (cross-entropy loss) over the training corpus.

## 📊 Training Loop Diagram

```mermaid
graph LR
    Input[Sequence: "The cat sat"] --> Model[CLM Model]
    Model --> Probabilities[Probability Distribution]
    Probabilities -->|Loss calculation against target "on"| Loss[Cross-Entropy Loss]
    style Input fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style Model fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style Loss fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
```

## 🛠️ Formulation
The loss function for a sequence of length $T$ is defined as:
$$\mathcal{L} = -\sum_{t=1}^T \log P(x_t \mid x_{1}, x_{2}, \dots, x_{t-1}; \theta)$$

---
[⬅️ Back to README](../README.md)
