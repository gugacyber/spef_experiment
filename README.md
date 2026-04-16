### 📝 README.md

````markdown
# SPEF - Secure Prompt Engineering Framework

**Empirical Evaluation of a Four-Layer Defensive Architecture against Prompt Injection and Data Leakage.**

---

## 🛡️ Project Overview

SPEF (Secure Prompt Engineering Framework) is an application-level defensive architecture designed to mitigate common vulnerabilities in Large Language Model (LLM) implementations. This project evaluates the framework's effectiveness using **Llama-3.3-70B** (via Groq API) against a standardized corpus of adversarial attacks.

This repository contains the experimental runner, the evaluation scripts, and the dataset used in the research paper: *"Secure Prompt Engineering: A Practical Framework for Mitigating Prompt Injection and Data Leakage in LLM-based Systems"*.

## 🏗️ The 4-Layer Architecture

The framework operates on a black-box principle, requiring no fine-tuning or access to model weights:

1.  **Layer 1: Prompt Structuring** – Enforces structural boundaries using delimiters and system-level instructions.
2.  **Layer 2: Input Sanitization** – Filters malicious keywords and known injection patterns.
3.  **Layer 3: Context Isolation** – Separates user-provided data from system instructions semantically.
4.  **Layer 4: Output Validation** – Inspects model responses for sensitive data leakage before final delivery.

## 📊 Key Results

In our controlled experiment with **85 test cases** (170 total interactions), SPEF demonstrated:

* **Baseline ASR (Attack Success Rate):** 8.8%
* **SPEF ASR:** 1.8%
* **Relative Reduction:** **79.5%**
* **Complete Mitigation (0% ASR):** Achieved in *Indirect Injection* and *Role Reassignment* categories.

## 🚀 Getting Started

### Prerequisites
* Python 3.10+
* Groq Cloud API Key (Free tier supported)

### Installation
1. Clone the repository:
   ```bash
   git clone [https://github.com/engguga/spef_experiment.git](https://github.com/engguga/spef_experiment.git)
   cd spef_experiment
````

2.  Create and activate a virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # Linux/macOS
    ```
3.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

### Running the Experiment

1.  Set your API Key in your terminal environment:
    ```bash
    export GROQ_API_KEY="your_gsk_key_here"
    ```
2.  Run the quick test (3 cases):
    ```bash
    python scripts/experiment.py quick
    ```
3.  Run the full experiment (85 cases):
    ```bash
    python scripts/experiment.py full
    ```
4.  Generate the statistical report:
    ```bash
    python scripts/scorer.py
    ```

## 📁 Repository Structure

  * `scripts/`: Python scripts for running experiments and scoring results.
  * `corpus/`: JSON files containing the adversarial prompt dataset.
  * `results/`: Raw JSON outputs from the LLM interactions.
  * `reports/`: Generated CSV files with final security metrics.

## 🎓 Citation

If you use this framework or dataset in your research, please cite:

> Viana, G. L. (2025). *Secure Prompt Engineering: A Practical Framework for Mitigating Prompt Injection and Data Leakage in LLM-based Systems*. Anhanguera Educacional.

-----

**Author:** [Gustavo Viana](https://www.google.com/search?q=https://github.com/engguga)
