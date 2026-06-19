# Awesome-CLM
## Causal Language Modeling (CLM): Variants, Types, & Applications

Causal Language Modeling (CLM)—often referred to as autoregressive language modeling—is the dominant training paradigm for modern Large Language Models (LLMs). The core objective is simple: given a sequence of tokens, predict the exact next token in the sequence. It enforces a strict causal mask, ensuring that the model cannot look ahead into the future when predicting the present.

---

## 1. Core Architectural & Masking Variants

These variants define how the underlying attention mechanism enforces causality or optimizes how tokens are processed.

| Variant | Details | Year | First Paper |
| :--- | :--- | :--- | :--- |
| [**Standard Autoregressive Masking**](details/standard_autoregressive_masking.md) | *Mechanism:* Uses a lower-triangular attention mask to zero out future tokens mathematically.<br>*Behavior:* Each token at index $i$ can only attend to tokens at indices $\le i$. | 2017 | [Attention Is All You Need](https://arxiv.org/abs/1706.03762) |
| [**Prefix Causal Masking (Non-Causal Decoder)**](details/prefix_causal_masking.md) | *Mechanism:* Allows fully bidirectional (non-causal) attention over an input prompt (the prefix), but applies strict causal masking for the generated tokens.<br>*Pros:* Enhances understanding of the input context before initiating sequence generation. | 2019 | [Unified Language Model Pre-training for Natural Language Understanding and Generation (UniLM)](https://arxiv.org/abs/1905.03197) |
| [**Bidirectional-to-Causal Hybrid (Enc-Dec)**](details/bidirectional_to_causal_hybrid.md) | *Mechanism:* Pairs a completely bidirectional encoder network with a strictly causal decoder network.<br>*Pros:* Separates the comprehension phase from the generation phase entirely. | 2017 | [Attention Is All You Need](https://arxiv.org/abs/1706.03762) |

---

## 2. Advanced Training & Objective Types

These variations alter how the causal objective is calculated, evaluated, or augmented during the optimization phase.

| Type | Details | Year | First Paper |
| :--- | :--- | :--- | :--- |
| [**Next-Token Prediction (Standard CLM)**](details/next_token_prediction.md) | *Objective:* Minimizes the cross-entropy loss over every single token sequentially across the entire training document. | 2018 | [Improving Language Understanding by Generative Pre-Training (GPT-1)](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) |
| [**Multi-Token Prediction (MTP)**](details/multi_token_prediction.md) | *Objective:* Modifies the architecture to predict multiple future tokens simultaneously (e.g., predicting $n+1$, $n+2$, and $n+3$ all at once).<br>*Pros:* Significantly improves training efficiency, boosts generation throughput, and encourages long-term planning. | 2024 | [Better & Faster LLMs via Multi-Token Prediction](https://arxiv.org/abs/2404.19737) |
| [**Flipped Causal Modeling (Infilling / FIM)**](details/flipped_causal_modeling.md) | *Objective:* Randomly splits documents into Prefix, Middle, and Suffix blocks, rearranging them so a causal model learns to fill in blanks (Fill-in-the-Middle).<br>*Pros:* Retains the efficient causal training loop while enabling bidirectional text editing capabilities. | 2022 | [Efficient Training of Language Models to Fill in the Middle](https://arxiv.org/abs/2207.14255) |

---

## 3. Real-World Downstream Applications

Because causal models excel at open-ended generation, they serve as the backbone engine for most consumer-facing AI systems.

| Application | Details | Year | First Paper |
| :--- | :--- | :--- | :--- |
| [**Conversational AI Agents (Chatbots)**](details/conversational_ai_agents.md) | *Application:* Generates fluid, context-aware dialogue by appending user queries to a running chat history text block. | 2019 | [DialoGPT: Large-Scale Generative Pre-training for Conversational Response Generation](https://arxiv.org/abs/1911.00536) |
| [**Source Code Generation & Autocomplete**](details/source_code_generation.md) | *Application:* Powers code assistants by reading the existing codebase causally up to the cursor position and generating the logically succeeding lines of code. | 2021 | [Evaluating Large Language Models Trained on Code (Codex)](https://arxiv.org/abs/2107.03374) |
| [**Creative Writing & Content Generation**](details/creative_writing.md) | *Application:* Produces long-form articles, essays, and stories based on short, open-ended structural text prompts. | 2019 | [Language Models are Unsupervised Multitask Learners (GPT-2)](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) |

---

## 4. Sampling & Inference Execution Variants

These runtime variations do not change model weights, but dictate how the causal output distribution is decoded into text.

| Variant | Details | Year | First Paper |
| :--- | :--- | :--- | :--- |
| [**Greedy Search Decoding**](details/greedy_search_decoding.md) | *Type:* Selects the single highest-probability token at every step.<br>*Behavior:* Highly deterministic, but prone to getting stuck in repetitive text loops. | 2014 | [Sequence to Sequence Learning with Neural Networks](https://arxiv.org/abs/1409.3215) |
| [**Nucleus Sampling (Top-p) & Top-k**](details/nucleus_top_k_sampling.md) | *Type:* Dynamically samples from the smallest set of tokens whose cumulative probability exceeds a threshold $p$, or truncates options to the top $k$ choices.<br>*Behavior:* Introduces controlled creativity and prevents nonsensical text generations. | 2018 (Top-k)<br>2019 (Top-p) | Top-k: [Hierarchical Neural Story Generation](https://arxiv.org/abs/1805.04833)<br>Top-p: [The Curious Case of Neural Text Degeneration](https://arxiv.org/abs/1904.09751) |
| [**Speculative Decoding**](details/speculative_decoding.md) | *Type:* Uses a tiny, fast "draft" causal model to generate a batch of candidate tokens, which are then verified in a single forward pass by a massive "target" model.<br>*Behavior:* Drastically scales up token generation speed without sacrificing final text quality. | 2022 | [Fast Inference from Transformers via Speculative Decoding](https://arxiv.org/abs/2211.17106) |
