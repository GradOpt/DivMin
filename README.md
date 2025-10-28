# DivMin

Core implementation for the paper [Stealing Knowledge from Auditable Datasets (ECAI 2025 Spotlight)](https://ebooks.iospress.nl/volumearticle/75843).

## Overview

This repository provides a minimal implementation of the *DivMin* attack, which is designed to adapt pretrained models on copyright-protected datasets while suppressing provenance signals such as watermarks and fingerprints.

The core idea of DivMin (please refer to Section 4 of the paper) is to minimize output divergence through:
- Anchor-only contrastive learning
- Backpropagation-free prototype classifier

These components instantiate the *divergence minimization* principle, which limits the upper bound of mutual information between provenance variable and observable evidence that can be exploited by data auditors (please refer to Section 3 of the paper for details).

This repository offers a compact and coherent demonstration of DivMin’s effectiveness, using the MobileCLIP (s0) vision encoder and the DTD fine-grained texture classification dataset.

## Example Usage

**ZeroShot.ipynb:** Evaluates the zero-shot classification accuracy (ACC) and the BadNets watermark verification success rate (VSR) of the MobileCLIP model. Since the model has not been adapted to the auditable dataset (DTD), the VSR remains low (≈3%). However, the ACC is also low (≈50%) due to the lack of task-relevant knowledge in the pretrained model for texture classification.

**FF.ipynb:** Fully finetunes the MobileCLIP model on the BadNets watermarked dataset. The model successfully learns the texture classification task, with ACC increasing to nearly 70%. However, the fully finetuned model is entirely marked by the BadNets trigger, making it trivially detectable by the auditor, with a VSR close to 100%.

**DivMin:** Demonstrates our DivMin attack, which adapts the MobileCLIP model on the DTD dataset using Anchor-only Contrastive Learning and a Backpropagation-free Prototype Classifier. The task accuracy matches or slightly exceeds that of full finetuning (≈70%), while the provenance signals remain as weak as in the innocent zero-shot model (≤3%). This illustrates DivMin’s strong ability to absorb task-relevant knowledge while suppressing provenance signals via divergence minimization.

- **Note:** In this repository, we use the BadNets watermark for demonstration purposes, which may appear similar to *backdoor mitigation*. Actually, real-world data provenance techniques are far broader than backdoor triggers. Advanced auditors often rely on benign watermarks that do not induce misclassification, or non-invasive fingerprinting methods that leave no perceptible trace in the protected data—scenarios in which state-of-the-art backdoor defenses are entirely ineffective. In contrast, our DivMin attack effortlessly suppresses these provenance signals by minimizing output divergence without prior knowledge of the specific auditing method (please refer to Section 5.3 of the paper for details).
