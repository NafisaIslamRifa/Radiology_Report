# Vision-Language Models for Medical Report Generation

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> A parameter-efficient Vision-Language Model (VLM) for automated radiology report generation featuring Target-Free Sequence-Level Explainability. This framework achieves state-of-the-art semantic translation and clinically accurate visual grounding in a single forward pass.

## 📑 Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Key Features](#key-features)
- [Results \& Evaluation](#results--evaluation)


## 📖 Overview
Current VLM paradigms struggle to balance computational efficiency with mathematically verifiable spatial accountability. This repository contains the codebase for bridging that gap by embedding visual grounding directly within a parameter-efficient (PEFT) Q-Former bottleneck, entirely eliminating the need for bounding boxes or complex contrastive alignment. 

This framework prioritizes semantic clinical reasoning over rote memorization, anchoring fluent natural language generation in actual diagnostic pathology.

## 🧠 Architecture
The model relies on three integrated components:
* **Vision Encoder (Rad-DINO):** A frozen, radiology-specific encoder pretrained on MIMIC-CXR for robust chest X-ray feature extraction.
* **Bridging Module (Q-Former):** A trainable bottleneck utilizing 64 query vectors to explicitly handle cross-modal alignment and structural spatial mapping.
* **Large Language Model (Qwen):** A generative decoder optimized via 4-bit Quantized Low-Rank Adaptation (QLoRA) for clinical instruction following.

## ✨ Key Features
* **Native Sequence-Level Explainability:** Extracts highly localized, faithful anatomical saliency maps directly from native Q-Former cross-attention weights.
* **Extreme Computational Efficiency:** Generates visual grounding maps in a single forward pass (**0.038 seconds**), operating exponentially faster than perturbation baselines like Score-CAM (98.3 seconds) with significantly lower memory overhead.
* **Target-Free Holistic XAI Pipeline:** Evaluates visual spatial accountability against the joint log-probability of the full generated report, bypassing brittle token-level attribution and avoiding gradient-shattering artifacts.

## 📊 Results & Evaluation
The framework is rigorously evaluated on a multi-dimensional pipeline:
1. **Report Generation:** Achieves strong semantic reasoning and diagnostic accuracy, establishing a state-of-the-art METEOR score (0.340) and high BERTScore F1 (0.876).
2. **Clinical Efficacy:** Demonstrates robust clinical entity extraction with a CheXbert Micro F1 of 0.439 and RadGraph F1 of 0.269.
3. **Visual Grounding:** Outperforms post-hoc XAI baselines in faithfulness and efficiency, achieving a superior Insertion AUC of 0.9934.




