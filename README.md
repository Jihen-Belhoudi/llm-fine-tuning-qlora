# LLM Fine-Tuning with QLoRA (PEFT)

This repository demonstrates a **production-oriented approach to fine-tuning Large Language Models (LLMs)** using **QLoRA (Quantized Low-Rank Adaptation)** under realistic compute constraints.

The goal is not to maximize benchmark scores, but to **adapt model behavior reliably and cost-efficiently**, as required in real-world AI systems.

---

## Project Overview

**Objective**

Adapt a general-purpose LLM to consistently generate **structured business outputs (strict JSON)** suitable for downstream systems (APIs, dashboards, automation).

**Key questions addressed**
- When is fine-tuning actually worth it?
- How can we fine-tune LLMs on limited hardware (Kaggle GPU)?
- How do we evaluate fine-tuning beyond training loss?

---

### Why PEFT / QLoRA?
- Full fine-tuning is computationally expensive and unnecessary for behavior adaptation
- QLoRA enables:
  - 4-bit quantized base model (low memory)
  - Training only ~0.1% of parameters
  - Stable fine-tuning on free GPUs

### Why Structured Outputs?
Generic tasks (e.g. “define customer churn”) are already mastered by modern LLMs.  
Fine-tuning becomes valuable when **strict format compliance** is required.

This project fine-tunes the model to always output **valid JSON** with fixed keys:
```json
{
  "definition": "",
  "business_impact": "",
  "example": ""
}
