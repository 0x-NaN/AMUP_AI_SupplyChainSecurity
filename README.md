# Securing AI Supply Chains via Update Instability Analysis

<p align="center">
  <img src="https://img.shields.io/badge/IEEE%20Connect-Accepted%202026-blue?style=flat-square&logo=ieee" alt="IEEE Accepted"/>
  <img src="https://img.shields.io/badge/PyTorch-2.x-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" alt="PyTorch"/>
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Datasets-CIFAR--10%20%7C%20STL--10-green?style=flat-square" alt="Datasets"/>
  <img src="https://img.shields.io/badge/Status-Research%20Prototype-orange?style=flat-square" alt="Status"/>
</p>

> **Research prototype** accompanying the IEEE Connect 2026 paper:  
> *"Update Instability Score: Structural Validation for Secure AI Supply Chains"*

---

## Overview

Modern AI supply chains distribute pretrained model weights across teams, vendors, and deployment environments. Standard validation — accuracy testing — **fails to detect malicious parameter perturbations** that preserve performance metrics while introducing behavioral instability.

This repository introduces two contributions:

| Contribution | Description |
|---|---|
| **AMUP** | *Adversarial Model Update Poisoning* — a threat model for covert weight-level attacks on AI supply chains |
| **UIS** | *Update Instability Score* — a lightweight detection metric requiring no labeled data, retraining, or architectural access |

**Key result:** >100× separation between benign and malicious updates at equal accuracy on CIFAR-10 and STL-10.

---

## Threat Model (AMUP)

Traditional supply chain attacks modify model behavior detectably — accuracy drops, outputs shift. AMUP models an adversary who:

- Perturbs model parameters within a carefully bounded region
- **Preserves task accuracy** on standard evaluation sets
- Introduces latent behavioral instability that activates under specific conditions

This makes AMUP-style attacks invisible to accuracy-based validation pipelines.

---

## Detection: Update Instability Score (UIS)

UIS detects AMUP-style attacks by measuring **structural instability in parameter updates** rather than output behavior.

**Properties:**
- No labeled data required
- No retraining required
- No architectural access required
- Operates purely on parameter delta statistics

---

## Results

| Dataset | Benign UIS | Malicious UIS | Separation |
|---|---|---|---|
| CIFAR-10 | baseline | >100× | ✅ |
| STL-10 | baseline | >100× | ✅ |

Both datasets evaluated at **equal task accuracy** between benign and poisoned models.

---

## Repository Structure

```
AMUP_AI_SupplyChainSecurity/
├── notebooks/          # Experiment notebooks
├── src/                # UIS implementation
├── results/            # Evaluation outputs
└── README.md
```

---

## Citation

> Paper accepted at IEEE Connect 2026. DOI forthcoming (expected September 2026).

If you use this work, please cite once the DOI is available.

---

## Disclaimer

This is a research prototype demonstrating a threat model and detection metric. It is not intended for production deployment. The AMUP threat model is documented for defensive research purposes.
