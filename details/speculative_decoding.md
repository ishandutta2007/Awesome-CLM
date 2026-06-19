# Speculative Decoding

Speculative Decoding accelerates autoregressive decoding by generating candidate tokens with a smaller model and validating them with a larger target model.

## 💡 Overview
Autoregressive decoding is slow because each step requires running the entire model for a single token. Speculative decoding speeds this up by using a lightweight "draft" model to speculate several future tokens (e.g., 4 or 5 tokens). These are verified in a single forward pass by the primary "target" model, keeping the target model's output distribution.

## 📊 Speculative Validation Diagram

```mermaid
graph TD
    Draft[Draft Model: Generates 5 tokens] --> Verification[Target Model Validation in 1 Forward Pass]
    Verification -->|Accept 3 tokens| Accept[Append 3 tokens to context & continue]
    Verification -->|Reject 4th token| Reject[Resample 4th token & discard 5th]
    style Draft fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style Verification fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style Accept fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
    style Reject fill:#ec4899,stroke:#ec4899,stroke-width:2px,color:#fff
```

---
[⬅️ Back to README](../README.md)
