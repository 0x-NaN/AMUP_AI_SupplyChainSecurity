
# Securing AI Supply Chains via Update Instability Analysis (AMUP)

Implementation-driven research prototype demonstrating Adversarial Model Update Poisoning (AMUP) and behavioral instability detection for AI supply chain security.

This repository accompanies an IEEE Connect submission.

---

## Overview

Modern AI supply chains distribute pretrained model weights across teams, vendors, and deployment environments. Traditional validation methods such as accuracy testing may fail to detect malicious parameter perturbations that preserve performance while introducing behavioral instability.

This project demonstrates:

* A reproducible ML training pipeline using CIFAR-10
* A simulated supply-chain attack via parameter perturbation
* Behavioral divergence measurement between clean and modified models
* Attack-strength (λ) tradeoff analysis
* Ensemble-level validation
* Cross-dataset validation (CIFAR → STL)

The focus is clarity, reproducibility, and deployment realism rather than state-of-the-art accuracy.

---

## Project Structure

```
IEEE_CONNECT_AMUP/
│
├── data/
│   ├── cifar-10-python.tar.gz
│   ├── cifar-100-python.tar.gz
│   └── stl10_binary.tar.gz
│
├── notebooks/
│   └── AMUP_AI_SUPPLY_CHAIN_Ver5_Debugged_Fixed.ipynb
│
├── report/
│   ├── conference-template-a4.docx
│   ├── conference-template-a4.pdf
│   └── IEEE_Connect_AMUP_Draft.docx
│
├── src/
│   ├── datasets/
│   └── models/
│       ├── base_model.pt
│       ├── clean_model.pt
│       └── poisoned_update.pt
│
├── requirements.txt
└── README.md
```

---

## Core Components

### 1. Clean Model Training

* Dataset: CIFAR-10
* Architecture: ResNet-18 (modified final layer for 10 classes)
* Optimizer: Adam
* Loss: CrossEntropy
* Deterministic seeds for reproducibility

A clean checkpoint is saved to simulate a trusted model artifact in a supply chain.

---

### 2. Simulated Supply-Chain Attack (AMUP)

A malicious update is created by introducing small Gaussian perturbations to trained model parameters.

This simulates:

* Post-training tampering
* Malicious weight distribution
* Silent behavioral manipulation

The poisoned model maintains comparable accuracy while exhibiting altered prediction behavior.

---

### 3. Behavioral Instability Detection

Rather than relying on accuracy degradation, the notebook measures prediction divergence between:

* Clean model
* Modified (poisoned) model

The evaluation includes:

* Prediction divergence fraction
* Attack–defense tradeoff under λ sweep
* Ensemble-level validation
* Cross-dataset validation
* Comparison with prior stability-style baselines

All experiments are deterministic and reproducible.

---

## Experimental Workflow

The notebook implements:

1. Reproducibility and device setup
2. Dataset loading and preprocessing
3. Clean model training
4. Model checkpoint saving
5. Parameter perturbation attack simulation
6. Behavioral divergence evaluation
7. λ-based tradeoff experiments
8. Ensemble validation
9. Cross-dataset validation

The entire pipeline is contained in a single reproducible notebook.

---

## How to Run

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Launch the notebook

```bash
jupyter notebook notebooks/AMUP_AI_SUPPLY_CHAIN_Ver5_Debugged_Fixed.ipynb
```

### 3. Execute sequentially

Run all cells in order from top to bottom to reproduce results.

---

## Saved Model Artifacts

Located in:

```
src/models/
```

| File               | Description                  |
| ------------------ | ---------------------------- |
| base_model.pt      | Initial trusted baseline     |
| clean_model.pt     | Clean trained model          |
| poisoned_update.pt | Simulated adversarial update |

These simulate distributed supply-chain artifacts.

---

## Design Philosophy

* No retraining-based detection
* No heavy interpretability frameworks
* No reliance on accuracy degradation
* Lightweight and deployment-oriented
* Focused on behavioral validation of model updates

This repository serves as a proof-of-concept demonstration for AI supply chain risk analysis.

---

## Limitations

* Simulated perturbation-based attack
* Limited dataset scale (CIFAR / STL)
* Prototype-level evaluation
* Not validated on large-scale production models

This work demonstrates feasibility rather than a production-ready security system.

---

## Paper

Draft paper located in:

```
report/IEEE_Connect_AMUP_Draft.docx
```

---

## Keywords

AI Security
Supply Chain Security
Model Update Poisoning
Behavioral Instability
Adversarial Machine Learning
Model Integrity

---
