# Do Large Language Models Understand Data Visualization Principles?

> **Martín Sinnona, Valentín Bonás, Emmanuel Iarussi, Viviana Siless**  
> Universidad Torcuato Di Tella · CONICET · Universidad de Buenos Aires  

[![arXiv](https://img.shields.io/badge/arXiv-Read%20Paper-b31b1b.svg)](https://arxiv.org/pdf/2602.20084)

---

## 📌 Abstract

Data visualization principles—derived from decades of research in perception and design—ensure proper visual communication. While prior work has shown that large language models (LLMs) can generate charts or flag misleading figures, it remains unclear whether they—and their vision-language counterparts (VLMs)—can reason about and enforce visualization principles directly.

Constraint-based systems encode these principles as logical rules for precise automated checking, but translating them into formal specifications requires expert knowledge. This motivates the use of LLMs and VLMs as flexible principle checkers capable of reasoning about visual design without explicit symbolic rule encoding.

We present the first systematic evaluation of both LLMs and VLMs on visualization principle reasoning using hard-verification ground truth derived from Answer Set Programming (ASP). We compiled a set of visualization principles expressed as natural-language rules and generated a controlled dataset of approximately 2,000 Vega-Lite specifications annotated with explicit principle violations, complemented by over 300 real-world charts.

We evaluate both **checking** (violation detection) and **fixing** (specification repair) tasks. Gemini-2.5-Flash achieved the strongest checking performance (F1 = 0.678 text-only, 0.716 multimodal) and 94.3% enforcement in fixing. However, performance drops sharply for subtler perceptual principles (F1 < 0.10), revealing a persistent gap between frontier language models and symbolic solvers.

---

## 🧠 Motivation

Clear visualization is essential for trustworthy data communication. Decades of research have distilled design best practices into actionable principles that prevent distortion and misinterpretation.

Symbolic systems such as **Draco** encode these principles as logical constraints, enabling exact automated verification. However, maintaining and extending symbolic rule sets requires substantial expertise and manual effort.

Recent work suggests that LLMs and VLMs may provide a scalable alternative. While models can detect misleading patterns in images or answer chart comprehension questions, it remains unclear whether they can reason about and enforce explicit design principles at the specification level.

---

## ⚙️ Problem Setting

We evaluate whether LLMs and VLMs can:

1. Read a Vega-Lite specification  
2. Reason about formal visualization principles  
3. Detect explicit rule violations  
4. Repair flawed specifications while preserving structure  

Unlike prior work, our evaluation ties each violation to **solver-verified ASP ground truth**, ensuring precise correctness signals.

---

## 📊 Dataset

- ~2,000 synthetic Vega-Lite specifications  
- >300 real-world Vega-Lite charts  
- Violations derived from ASP-encoded principles  
- Principles translated into natural-language descriptions  

Each chart instance contains:

- The Vega-Lite specification  
- One or more annotated principle violations  
- Structured prompt variants  
- Ground-truth violation labels  

---

## 🧪 Evaluation Tasks

### 1️⃣ Checking (Detection)

Models must identify which principle violations are present.

- Outputs required in strict JSON schema
- Macro-averaged F1 across principles
- Prompt-adherence measured separately

### 2️⃣ Fixing (Repair)

Models are prompted to minimally modify a specification to enforce a target principle.

We measure:

- Compilability (CO)
- Enforcement Rate (ER)
- Compliance Ratio (CR)

---

## 📈 Results

### Detection (Checking)

- **Gemini-2.5-Flash**
  - F1 = 0.678 (text-only)
  - F1 = 0.716 (multimodal)
- GPT-4o follows closely
- Open-source models trail behind
- Subtle perceptual principles: F1 < 0.10

### Repair (Fixing)

- Frontier models achieve up to **94.3% enforcement**
- Notable asymmetry: models are often better at correcting violations than reliably detecting them

---

## 🔍 Key Findings

- LLMs can detect common structural violations reliably.
- Multimodal input improves performance modestly.
- Subtle perceptual rules remain challenging.
- A consistent gap remains between language-based reasoning and symbolic ASP verification.
- Fixing performance exceeds detection performance, revealing a fixing–detection asymmetry.

---

## 📚 Citation

```bibtex
@misc{sinnona2026largelanguagemodelsunderstand,
      title={Do Large Language Models Understand Data Visualization Principles?}, 
      author={Martin Sinnona and Valentin Bonas and Viviana Siless and Emmanuel Iarussi},
      year={2026},
      eprint={2602.20084},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2602.20084}, 
}
