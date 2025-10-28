# DivMin

Code for the ECAI 2025 paper "Stealing Knowledge from Auditable Datasets".

## Overview

This repository provides a minimal implementation of the *DivMin* attack, which is designed to learn task-relevant knowledge from copyright-protected datasets while effectively suppressing provenance signals such as watermarks and fingerprints.

The core idea of DivMin is to minimize output divergence through:
- Anchor-only contrastive learning
- Backpropagation-free prototype classifier
(Please refer to Section 4 of the paper for details.)

These components instantiate the divergence minimization principle, which limits the upper bound of mutual information between available evidence and provenance variable exploitable by data auditors (Please refer to Section 3 of the paper for details).

This repository offers a compact and coherent demonstration of the effectiveness of DivMin’s effectiveness, using:
- The MobileCLIP (s0) vision encoder  
- The DTD fine-grained texture classification dataset

