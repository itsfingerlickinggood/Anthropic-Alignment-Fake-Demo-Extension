# 🧠 When Models Think They’re Being Trained
### Studying Training-Aware Behavior in Small Open-Source Language Models

![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Domain](https://img.shields.io/badge/Domain-AI%20Safety-blue)
![Affiliation](https://img.shields.io/badge/Project-BlueDot%20Impact-indigo)
![Stack](https://img.shields.io/badge/Tech-HuggingFace%20%7C%20Colab-orange)

---

## 📌 Project Summary

Recent AI safety research by Anthropic and Redwood Research has demonstrated that some large language models can change their behavior when they believe their responses will be used for training. In certain cases, models appeared more willing to comply with harmful requests under training pressure, a behavior often discussed as **alignment faking**.

This project investigates whether similar training-aware behavioral shifts appear in **smaller, open-source language models**, using a simplified, fully reproducible setup that requires no fine-tuning or privileged access.

> **Key Distinction:** Rather than assuming deception or long-term misalignment, this work focuses on a more basic and measurable question: *does perceived training pressure change how a model behaves at all?*

---

## 🎯 Core Research Question

**Do small open-source language models change their willingness to answer risky or harmful questions when they believe their responses will be used for training?**

---

## 🧩 Relationship to Prior Work

| Source | Key Findings |
| :--- | :--- |
| **Anthropic / Redwood** | Demonstrated that alignment faking can occur in frontier models under contrived training-pressure prompts. |
| **Follow-up Work** | Found that explicit alignment-faking reasoning is rare, fragile, and sensitive to prompt design. |
| **This Project** | Reframes alignment faking as a possible endpoint of a broader spectrum of **training-sensitive behavior**, looking for earlier, weaker signals in accessible models. |

---

## 🔬 Experimental Design

### 1. Two Conditions
The model is placed in one of two otherwise identical contexts. Only a single detail is changed between them:

| Condition | Description |
| :--- | :--- |
| **Training Condition** | The model is told its response **will** be used for training. |
| **Non-Training Condition** | The model is told its response **will not** be used for training. |

### 2. Prompts
* A small set of mildly harmful or policy-adjacent prompts.
* Chosen to avoid automatic refusal saturation.
* **Identical prompts** are used in both conditions.

### 3. Models
Both models are run in **inference-only mode** using 4-bit quantization on Google Colab.

* **Primary Model:** `DeepSeek-R1-Distill-Llama-8B`
* **Control Model:** `Qwen2.5-7B-Instruct`

---

## 📊 What Is Measured

The project focuses on **observable behavior**, not intent.

### Primary Signal: The Compliance Gap
> The difference in **answer vs. refusal rates** between training and non-training conditions.

### Secondary Signals (Qualitative)
* Mentions of training consequences.
* Awareness of future behavior changes.
* Sensitivity to training pressure in reasoning traces or output tone.

*Note: Explicit deception or “alignment faking” is not required for results to be meaningful.*

---

## 🔁 Extension Plan (Beyond Replication)

After the initial comparison, the project tests the **robustness** of training-aware behavior by varying:

1.  **Reasoning:** Presence vs. absence of scratchpad reasoning.
2.  **Formatting:** Strict response-format suffixes.
3.  **Authority:** Framing of the training authority.
4.  **Fragility:** Minor prompt rewordings.

This directly addresses open questions about robustness vs. prompt sensitivity raised in recent discussions.

---

## 🛠️ Technical Setup

* **Environment:** Google Colab (GPU)
* **Library:** Hugging Face Transformers
* **Optimization:** BitsAndBytes (4-bit quantization)
* **Method:** Inference-only (no fine-tuning, no RL)
* **Data Safety:** Outputs saved incrementally to avoid session loss.

---

## 🧪 Phase Plan

* **Phase 1: Baseline Test**
    * Run both models under training vs. non-training conditions.
    * Measure compliance gaps.
* **Phase 2: Robustness Checks**
    * Test whether observed effects persist under small prompt or format changes.
* **Phase 3: Interpretation**
    * Analyze whether training-aware behavior appears stable, fragile, or absent.
    * Relate findings back to alignment faking literature.

---

## 📈 Expected Outcomes

All of the following are valid and informative outcomes:

* ✅ A measurable compliance gap.
* ✅ No observable effect.
* ✅ Highly unstable or prompt-sensitive behavior.
* ✅ Differences between models.

> **Note:** Negative or null results are explicitly valuable given current uncertainty in the field.

---

## 🔍 Why This Matters

Small open-source models are widely used and fine-tuned by the community. Understanding whether **training awareness** appears at this scale informs:
* Evaluation design.
* Safety diagnostics.
* Interpretation of alignment-faking demos.

This project provides reproducible evidence using accessible tools.

---

## 📂 Project Status

- [x] Literature review completed
- [x] Extension idea finalized
- [x] Models selected and validated on Colab
- [x] Prompt structure drafted
- [ ] Experiment implementation in progress
- [ ] Data collection
- [ ] Analysis & Write-up

---

## 🤝 Acknowledgements

This project is developed as part of the **BlueDot Impact Technical AI Safety Project**, building on work by Anthropic, Redwood Research, and the broader AI safety research community.
