---
title: Depth Pro
arxiv: arxiv.org/abs/2410.02073
authors: Bochkovskii et al. (Apple)
date_read: 2026-06-11
tags: [monocular-depth, zero-shot, efficient-inference]
---

**What it does** — Zero-shot metric monocular depth, sharp at boundaries, ~0.3s per image at high res.

**Why it matters** — No camera intrinsics needed; multi-scale ViT gives clean edges where prior models smear.

**Doubts** — Real metric accuracy on out-of-distribution scenes; how it degrades on reflective/transparent surfaces.

**Note** — Two-stage encoder pattern worth comparing against FastVLM's CNN-then-attention idea.
