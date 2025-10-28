# DivMin

Core implementation for the paper [Stealing Knowledge from Auditable Datasets (ECAI 2025 Spotlight)](https://ebooks.iospress.nl/volumearticle/75843).

## Overview

This repository provides a minimal implementation of the *DivMin* attack, which is designed to adapt pretrained models on copyright-protected datasets while suppressing provenance signals such as watermarks and fingerprints.

The core idea of DivMin (please refer to Section 4 of the paper) is to minimize output divergence through:
- Anchor-only contrastive learning
- Backpropagation-free prototype classifier

These components instantiate the *divergence minimization* principle, which limits the upper bound of mutual information between provenance variable and observable evidence that can be exploited by data auditors (please refer to Section 3 of the paper for details).

This repository offers a compact and coherent demonstration of DivMin’s effectiveness, using the MobileCLIP (s0) vision encoder and the DTD fine-grained texture classification dataset.

