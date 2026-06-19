# Source Code Generation & Autocomplete

Causal language models excel at code generation and inline autocomplete.

## 💡 Overview
Causal language models are trained on massive code repositories (like GitHub). During inference, the existing source code up to the cursor position is fed as context, and the model predicts the succeeding characters, lines, or blocks of code.

## 📊 Autocomplete Process Diagram

```mermaid
graph TD
    Context["Source Code Context:<br>def add(a, b):"] --> CLM[Causal Language Model]
    CLM --> Suggestion["Generated Completion:<br>    return a + b"]
    style Context fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style CLM fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
```

## 🛠️ Key Strategies
- **Causal Generation:** Generates code sequentially from left to right.
- **FIM (Fill-in-the-Middle):** Used extensively in IDE extensions to insert code in the middle of existing files by providing both prefix and suffix context.

---
[⬅️ Back to README](../README.md)
