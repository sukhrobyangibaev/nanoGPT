# nanoGPT Model Learning Progress

## 📅 Session 1: Jan 19, 2026

### What we covered today:
We started a bottom-up exploration of `model.py` to understand how a GPT model is built from scratch.

#### 1. `GPTConfig` (The Blueprint)
- **Concept:** A `dataclass` that holds all the hyperparameters.
- **Key Terms:**
    - `block_size`: The context window (how many tokens the model sees).
    - `vocab_size`: The model's dictionary size (padded for GPU efficiency).
    - `n_layer` / `n_head` / `n_embd`: The depth, perspective, and width of the model.
- **Analogy:** The DNA or traits of the "student."

#### 2. `MLP` (The Individual Thinker)
- **Concept:** Multi-Layer Perceptron. Handles computation for each token individually.
- **Process:** Expands the vector (4x), applies `GELU` activation (filtering), and contracts it back to the original size.
- **Analogy:** Individual homework time where a word processes its own meaning.

#### 3. `LayerNorm` (The Volume Control)
- **Concept:** Standardizes the mathematical values across a layer to keep them stable.
- **Process:** Sets the mean to 0 and the variance to 1, then allows the model to re-scale/shift using `weight` and `bias`.
- **Analogy:** Standardizing test scores so you can compare students from different schools fairly.

---

## 🗓️ Plan for Tomorrow: "The Conversation"

Tomorrow, we will move from individual processing to how words interact.

1.  **`CausalSelfAttention` (Line 29):**
    - The most important part of the Transformer.
    - We will learn about **Queries, Keys, and Values**.
    - We will understand **Causal Masking** (why the model can't see the future).
2.  **`Block` (Line 94):**
    - How `Attention` and `MLP` are combined into a single repeating unit.
    - The magic of **Residual Connections** (`x = x + ...`).
3.  **`GPT` Main Class (Line 118):**
    - The final assembly.
    - How word embeddings and position embeddings work.
    - How the model turns math back into words (`lm_head`).
