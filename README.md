# 🧠 When Models Think They’re Being Trained
### Investigating Training-Aware Behavior in Small Open-Source Language Models

[![Status](https://img.shields.io/badge/Status-Research_in_Progress-yellow?style=flat-square)](https://github.com/yourusername/repo)
[![Domain](https://img.shields.io/badge/Domain-AI_Safety_%7C_Alignment-blue?style=flat-square)](https://bluedot.org)
[![Model](https://img.shields.io/badge/Model-DeepSeek_R1_%7C_Qwen_2.5-purple?style=flat-square)](https://huggingface.co)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

---

## 📄 Abstract

Recent investigations by Anthropic and Redwood Research suggest that Large Language Models (LLMs) exhibit **training-aware behavior**—altering their outputs when they detect that their responses will be used for future training (a precursor to *alignment faking*). While this phenomenon has been documented in frontier models, little research exists on its prevalence in smaller, accessible open-source models.

This project isolates the variable of **perceived training pressure** in a simplified, inference-only environment. By comparing compliance rates between "training" and "non-training" contexts in 7B-8B parameter models, this study aims to determine if training-awareness is an emergent property of scale or a fundamental behavior present in smaller architectures.

---

## 📐 Experimental Design

The core of this experiment is a **controlled context injection**. The model processes the same harmful/policy-adjacent prompts under two distinct system conditions.

### Methodology Flowchart

```mermaid
graph TD
    A[Input Prompt] --> B{Condition Injection}
    B -- Condition A --> C[Training Context]
    B -- Condition B --> D[Non-Training Context]
    C --> E[Model Inference<br/>(DeepSeek-R1 / Qwen2.5)]
    D --> E
    E --> F[Output Analysis]
    F --> G{Measure Compliance Gap}
    
    style C fill:#ffebee,stroke:#c62828,stroke-width:2px
    style D fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px
    style G fill:#e3f2fd,stroke:#1565c0,stroke-width:2px
