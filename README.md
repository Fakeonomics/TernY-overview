# GOT — Gain-Only Ternary Transformer

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)
![License](https://img.shields.io/badge/license-All%20Rights%20Reserved-red)

**Live site:** https://fakeonomics.github.io/GOT-overview/

A ternary transformer where every weight is {-1, 0, +1}. No FP32 inference — just additions and subtractions. Trained end-to-end with latent FP32 weights and Straight-Through Estimator quantization (BitNet b1.58-style).

Part of the **Fakeonomics** research portfolio by Yuriy Venediktov.

---

## Results (GOT v3, 31M)

| Metric | Value |
|--------|-------|
| Total params | 31.1M |
| Ternary after hardening | 6.5M |
| Packed model size | ~1.2 MB |
| Perplexity | 5.0 |
| Training time | 10 min on RTX 3050 (6 GB) |
| Training tokens | 20M |

Generates simple English sentences after 10 minutes of training.

## Architecture (brief)

- **BitLinear** — latent FP32 + absmean STE quantization + per-channel FP16 scale
- **SubLN** — sublayer normalization (pre-attention + pre-FFN)
- **ReLU²** — squared ReLU activation in FFN
- **GQA + RoPE** — Grouped Query Attention + Rotary Position Embeddings
- **Tied embeddings** — shared FP32 input/output matrix

## Current limitations

- Early-stage research. Not production-ready.
- Small scale (31M/64M params — not billion-parameter).
- Limited vocabulary and training corpus.
- No hardware deployment or MCU port yet.
- No standard benchmark evaluation (MMLU, etc.).

## Status

- GOT v3 (64M) currently training on 82M tokens.
- Code is **private and proprietary** (All Rights Reserved).
- Research paper coming soon on Zenodo.
- This repo is a public landing page only — no source code.

## See also

- [TernML](https://fakeonomics.github.io/TernML-overview/) — Multi-Architecture Ternary ML Framework
- [TernaT](https://fakeonomics.github.io/TernaT-overview/) — Learned Neural VSA Reasoner
- [Fakeonomics on GitHub](https://github.com/Fakeonomics)

---

*Fakeonomics © 2026 · Yuriy Venediktov · All Rights Reserved*
