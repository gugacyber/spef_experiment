# SPEF — Secure Prompt Engineering Framework

**Research framework for adversarial LLM evaluation, prompt injection analysis, and Attack Success Rate (ASR) scoring reliability.**

---

## Overview

SPEF (Secure Prompt Engineering Framework) is an experimental framework focused on evaluating the reliability of adversarial Large Language Model (LLM) security assessment methodologies.

The project investigates how scorer implementation choices directly affect reported Attack Success Rate (ASR) metrics in prompt injection and adversarial evaluation experiments.

This repository contains:
- adversarial evaluation scripts
- scorer implementations
- experimental datasets
- statistical evaluation utilities
- reproducible security experiments

The framework was evaluated using **Llama-3.3-70B** via the :contentReference[oaicite:0]{index=0} against an OWASP-aligned adversarial corpus.

---

## Research Paper

### ASR Does Not Measure What You Think It Measures

*A Comparative Analysis of Attack Success Scoring Methods in Adversarial LLM Evaluation*

📄 Zenodo DOI:  
https://doi.org/10.5281/zenodo.20245521

📚 Publication Page:  
https://zenodo.org/records/20245521

---

## Main Research Findings

The study demonstrates that scorer design alone can significantly distort adversarial LLM evaluation results.

### Experimental Results

| Metric | Scorer A | Scorer B |
|---|---|---|
| F1 Score | 33.3% | 76.9% |
| False Positive Rate | 7.1% | 1.4% |

### Key Discovery

Changing only the evaluation logic produced:

- **+130.9% F1 improvement**
- **−80.3% False Positive Rate reduction**

without changing:
- the model
- the dataset
- the attack corpus
- the prompts

---

## Identified Scorer Failure Modes

The research identifies three major evaluation failures in adversarial LLM scoring systems:

1. **Refusal-Mention Ambiguity**  
   Defensive responses mentioning sensitive terms are incorrectly classified as successful attacks.

2. **Library Coverage Problem**  
   Pattern-based scorers fail to detect successful attacks outside predefined vocabularies.

3. **Indirect Injection Scoring Gap**  
   Hybrid responses in retrieval-based attacks resist heuristic classification approaches.

---

## Refusal-First Standard

The project proposes a minimal standard for adversarial LLM scoring systems:

1. Refusal detection must precede compromise detection
2. Success requires affirmative compliance
3. Ambiguous cases default to defense
4. False Positive Rate (FPR) must be reported alongside ASR

---

## Repository Structure

```text
scripts/     Experimental runners and scorers
corpus/      Adversarial prompt datasets
results/     Raw model outputs
reports/     Statistical evaluation reports
```

---

## Getting Started

### Requirements

- Python 3.10+
- Groq API Key

### Installation

```bash
git clone https://github.com/gugacyber/spef_experiment.git
cd spef_experiment

python3 -m venv venv
source venv/bin/activate

pip install -r requirements.txt
```

---

## Running Experiments

### Quick Evaluation

```bash
python scripts/experiment.py quick
```

### Full Evaluation

```bash
python scripts/experiment.py full
```

### Generate Statistical Reports

```bash
python scripts/scorer.py
```

---

## Citation

```bibtex
@misc{viana2026asr,
  author       = {Viana, Gustavo Lima},
  title        = {ASR Does Not Measure What You Think It Measures: A Comparative Analysis of Attack Success Scoring Methods in Adversarial LLM Evaluation},
  year         = {2026},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.20245521},
  url          = {https://doi.org/10.5281/zenodo.20245521}
}
```

---

## Research Areas

- LLM Security
- Prompt Injection
- Adversarial Evaluation
- AI Security
- Benchmark Reliability
- Secure Prompt Engineering
- Attack Success Rate (ASR)

---

## Author

**Gustavo Lima Viana**  
Independent Researcher — Brazil

GitHub: https://github.com/gugacyber  
ORCID: https://orcid.org/0009-0003-7211-6774
````
