---
title: Literature Review Survey
type: notes
created: 2026-01-07 04:07:38.230000
updated: 2026-01-07 04:07:38.230000
synced_from: VibeProject
---

# Literature Review Survey

## 1. Overview
We surveyed 15 papers from 2018-2023 regarding ML in NIDS.

## 2. Key Findings
- **Shone et al. (2018)**: Proposed a non-symmetric deep autoencoder (NDAE) which reduced training time by 98% while maintaining high accuracy.
- **Mirsky et al. (2018)**: Introduced "Kitsune", an ensemble of autoencoders running on edge routers.
- **Comparison**:
    - *Supervised (Random Forest)*: High accuracy but requires labeled data (cannot find zero-days).
    - *Unsupervised (Autoencoders)*: Lower precision but excellent at novelty detection.

## 3. Conclusion
We selected a Deep Autoencoder architecture similar to Kitsune but enhanced with LSTM layers for temporal context, as this offers the best balance for zero-day detection.
