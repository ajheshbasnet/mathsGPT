# Math Decoder LM (~10M Params)

A decoder-only Transformer (~10M parameters) trained from scratch for mathematical reasoning. Built with modern components (RoPE, pre-norm) and trained using synthetic data plus RL fine-tuning for step-by-step reasoning.

---

## Overview

This project explores whether small language models can learn structured mathematical reasoning using:
- Synthetic, high-quality math data  
- Explicit reasoning traces  
- Reinforcement learning for deeper thinking  

---

## Architecture

- Model Type: Decoder-only Transformer  
- Parameters: ~10M  
- Attention: Multi-head self-attention  
- Positional Encoding: RoPE (Rotary Positional Embeddings)  
- Normalization: Pre-LayerNorm  
- Feedforward: GELU-based MLP  
- Residual Connections: Standard  
- Context Length: 256–512 tokens  

### Decoder Block

    x → LayerNorm → Self-Attention (RoPE) → Residual  
      → LayerNorm → MLP (GELU) → Residual  

---

## Training Pipeline

### 1. Pre-training
- Objective: Causal Language Modeling  
- Data: Fully synthetic math dataset  
- Domains:
  - Arithmetic  
  - Algebra  
  - Symbolic manipulation  

### 2. Synthetic Data
- Programmatically generated  
- Curriculum-based difficulty  
- Step-by-step reasoning supervision  

Example:

    Q: Solve 3x + 2 = 11  
    A: 3x = 9  
       x = 3  

### 3. RL Fine-Tuning (Deep Thinking)
- Improves reasoning beyond next-token prediction  
- Encourages structured, multi-step solutions  

Rewards based on:
- Final answer correctness  
- Logical consistency  
- Step coherence  

---

## Training Details

- Optimizer: AdamW  
- LR Schedule: Cosine decay  
- Loss: Cross-entropy (pre-training)  
- RL: PPO-style optimization  
- Token Budget: Configurable  

---

## Evaluation

- Exact match accuracy  
- Step-by-step correctness  
- Generalization to unseen problems  

---

## Limitations

- Limited general knowledge  
- Dependent on synthetic data quality  
- Small model capacity constraints  

---

## Research Goals

- Minimal scale for reasoning emergence  
- Effectiveness of synthetic data  
- Role of RL in reasoning improvement  

---

## Key Insight

Reasoning emerges from structure and supervision — not just scale.

---

## License

MIT License
