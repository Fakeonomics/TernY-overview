[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX) [![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red)]() [![TernY Site](https://img.shields.io/badge/TernY-Live%20Site-rose?style=for-the-badge)](https://fakeonomics.github.io/TernY-overview/)

# TernY: Ternary Transformer by Yuriy

A BitNet-style ternary transformer with **{-1, 0, +1}** weights.  
**31.1M params · Perplexity 5.0 · 1.2 MB packed · 10 min training**

Latent FP32 weights with absmean STE quantization to ternary. Per-channel FP16 scale. SubLN + ReLU² + GQA + RoPE. All weights trainable — no frozen random.

## Key Results

| Metric | Value |
|--------|:-----:|
| Total parameters | 31.1M |
| Architecture | d=384, L=4, heads=6, KV=3, d_ff=1536 |
| Best loss | **1.6083** |
| Perplexity | **5.0** |
| Packed size | **~1.2 MB** |
| Training time | **10 min** on RTX 3050 6 GB |
| Training tokens | 20M |

Generates grammatically coherent English sentences. 37× better perplexity than frozen-random approach.

## Architecture

- **BitLinear** — latent FP32 weights with absmean STE quantization, per-channel FP16 scale
- **SubLN** — sublayer normalization (double LayerNorm: pre-attention + pre-FFN)
- **ReLU²** — squared ReLU activation in FFN
- **GQA + RoPE** — Grouped Query Attention (8Q/4KV) with Rotary Position Embeddings
- **Tied embeddings** — shared FP32 input/output matrix
- **No bias terms** — clean, lean decoder-only design

## Novel Contributions

1. **BitNet-style ternary transformer** — all weights trainable, no frozen random layers
2. **Perplexity 5.0 in 10 minutes** on consumer laptop GPU
3. **SubLN + ReLU²** architecture optimized for ternary computation
4. **TernY-DL (Domain Layer)** — 200 binary scale-delta modules, ~2.7 KB each, proven concept
5. **Full scaling law confirmation** — more data = better quality (82M tokens for 64M model)

## Comparison: TernY vs GOT

| Metric | TernY v3 (BitNet) | GOT v2 (Frozen) |
|--------|:-----------------:|:----------------:|
| Approach | Train all weights | 97% frozen random |
| Perplexity | **5.0** | ~28 |
| Training time | 10 min | 12+ min |
| Text generation | Coherent sentences | None |

TernY's v3 breakthrough: training all weights in latent FP32 with STE quantization works. Frozen random ternary does not.

## Status

- **TernY v3 (31M)** — working, perplexity 5.0
- **TernY v3 (64M)** — currently training on 82M tokens (d=768, L=6)
- Code is **private and proprietary** (All Rights Reserved)
- Research paper coming soon on Zenodo
- This repo is a public landing page only — no source code

## See also

- [TernML](https://fakeonomics.github.io/TernML-overview/) — Multi-Architecture Ternary ML Framework
- [TernaT](https://fakeonomics.github.io/TernaT-overview/) — Learned Neural VSA Reasoner
- [Fakeonomics on GitHub](https://github.com/Fakeonomics)

---

*Fakeonomics © 2026 · Yuriy Venediktov · All Rights Reserved*
