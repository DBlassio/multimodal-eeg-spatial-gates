# multimodal-spatial-gates

Multimodal sexism detection in memes with topographic EEG representations and per-channel spatial gates.

---

## Research Questions

**Primary.** Does preserving the topographic structure of EEG improve multimodal sexism detection compared to a flat EEG representation?

**Secondary.** Can per-channel EEG gates conditioned on text reveal anatomically grounded patterns of neural relevance, consistent with cognitive neuroscience literature on social cognition?

---

## Models

Four architectures of increasing complexity, all built on the same text (mDeBERTa-v3) and vision (ALIGN) encoders.

| # | Model | EEG Representation | Gating | Key Contribution |
|---|---|---|---|---|
| M1 | Flat EEG Baseline | 80-dim vector → MLP → d=768 | Scalar per modality | Control: replicate EXIST 2026 without ET/HR |
| M2 | Channel-Gated EEG | Flat, text-conditioned gate per channel | α_i per channel (×16) | Interpretability without added representational complexity |
| M3 | EEG Channel Transformer | Each channel = token with topographic positional embeddings | — | Spatial inter-region interactions |
| M4 | EEG Transformer + Channel Gates | Transformer-enriched tokens | α_i per channel, text-conditioned | Topographic representation + interpretable gates |

Expected ordering: **M1 < M2 < M3 < M4**

Even modest performance gains are scientifically valuable if gates reveal regionally consistent patterns (e.g., frontal theta/alpha for social cognition, occipital beta for visual processing).
