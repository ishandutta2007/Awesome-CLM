# Conversational AI Agents (Chatbots)

Causal Language Models serve as the core generative engine for modern conversational agents.

## 💡 Overview
Causal language models are adapted for dialogue by formatting multi-turn conversations as single, continuous text sequences. The dialogue history acts as the preceding context (prefix) and the chatbot's response is generated autoregressively.

## 📊 Conversation Flow Diagram

```mermaid
graph TD
    History["System: You are an assistant<br>User: Hello!<br>Assistant: Hi, how can I help you?"] --> NewInput["User: How does CLM work?"]
    NewInput --> Combined["Concatenated Prompt<br>(History + New Input + 'Assistant:')"]
    Combined --> CLM[Autoregressive Generator]
    CLM --> Response["Assistant: CLM works by..."]
    style History fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style NewInput fill:#1e1b4b,stroke:#06b6d4,stroke-width:2px,color:#fff
    style CLM fill:#311042,stroke:#ec4899,stroke-width:2px,color:#fff
```

## 🛠️ Mechanism
- User inputs and assistant outputs are appended to the context.
- Special chat templates (like ChatML or Llama templates) structure the turns with tokens like `<|im_start|>` and `<|im_end|>`.
- The model generates the next sequence of tokens until it outputs the end-of-turn token.

---
[⬅️ Back to README](../README.md)
