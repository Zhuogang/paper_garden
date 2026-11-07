# DeepSeek Series — Reading List

A pre-read map of the DeepSeek paper lineage: architecture, training recipe, and takeaways, organised so the
graph edges are visible before you read. Compiled 2026-11-05; checked against primary sources 2026-11-07.

**How this file works**
- Each entry carries a proposed note id. To read one: `cp templates/paper-note.md papers/<id>.md`, write your
  90-second take, then say **"ingest"**. Ingest ticks the box here and moves the paper into `index.md`.
- Tags listed per entry are canonical (registered in `meta/tags.md`). Lineage lines are *candidate* edges;
  they become real edges in `meta/edges.md` only when both ends have notes.
- ⚠ marks facts that could not be confirmed against a primary source (see *Verification notes* at the end).
  Benchmark numbers are as reported by the authors, including where they were checked against the paper.

---

## Queue

Status: `[ ]` to read · `[x]` noted and in `index.md`.

| # | Status | id | Date | Track | One-liner |
|---|---|---|---|---|---|
| 1 | [ ] | `2024-deepseek-llm` | 2024-01 | Core | 7B/67B dense; scaling-law study that set the data/compute philosophy |
| 2 | [ ] | `2024-deepseekmoe` | 2024-01 | Arch | Fine-grained experts + shared experts; the MoE design used ever since |
| 3 | [ ] | `2024-deepseek-coder` | 2024-01 | Code | 1.3B–33B code models, 2T tokens, repo-level data, FIM |
| 4 | [ ] | `2024-deepseekmath` | 2024-02 | Reasoning | 7B math model; **introduces GRPO** |
| 5 | [ ] | `2024-deepseek-vl` | 2024-03 | Multimodal | First VLM; hybrid SigLIP+SAM encoder; keep text data to avoid forgetting |
| 6 | [ ] | `2024-deepseek-v2` | 2024-05 | Core | 236B/21B MoE; **introduces MLA**; 93% KV-cache cut |
| 7 | [ ] | `2024-deepseek-prover` | 2024-05 | Formal math | Lean 4 prover from 8M synthetic autoformalised proofs |
| 8 | [ ] | `2024-deepseek-coder-v2` | 2024-06 | Code | V2 checkpoint + 6T code/math tokens; 338 languages; 128K |
| 9 | [ ] | `2024-esft` | 2024-07 | Arch | Fine-tune only task-relevant experts |
| 10 | [ ] | `2024-deepseek-prover-v1-5` | 2024-08 | Formal math | RL from Lean feedback (GRPO) + RMaxTS tree search |
| 11 | [ ] | `2024-fire-flyer-ai-hpc` | 2024-08 | Infra | 10k PCIe-A100 cluster co-design; HFReduce, 3FS, HAI-Platform |
| 12 | [ ] | `2024-aux-loss-free` | 2024-08 | Arch | Expert-wise routing bias replaces the balance loss; the method V3 adopts |
| 13 | [ ] | `2024-janus` | 2024-10 | Multimodal | Decoupled visual encoders for unified understanding + generation |
| 14 | [ ] | `2024-janusflow` | 2024-11 | Multimodal | Janus with rectified-flow generation |
| 15 | [ ] | `2024-deepseek-vl2` | 2024-12 | Multimodal | MoE + MLA VLM with dynamic tiling |
| 16 | [ ] | `2024-deepseek-v3` | 2024-12 | Core | 671B/37B; aux-loss-free balancing, MTP, FP8 training, DualPipe |
| 17 | [ ] | `2025-deepseek-r1` | 2025-01 | Reasoning | Pure-RL reasoning (R1-Zero), 4-stage R1 pipeline, distillation; Nature 2025 |
| 18 | [ ] | `2025-janus-pro` | 2025-01 | Multimodal | Janus scaled to 7B with synthetic aesthetic data |
| 19 | [ ] | `2025-codeio` | 2025-02 | Reasoning | Code input/output prediction as general reasoning data |
| 20 | [ ] | `2025-nsa` | 2025-02 | Arch | Native Sparse Attention, trainable + hardware-aligned; ACL 2025 best paper |
| 21 | [ ] | `2025-open-infra-week` | 2025-02 | Infra | FlashMLA, DeepEP, DeepGEMM, DualPipe, EPLB, 3FS, inference overview (repos, no paper) |
| 22 | [ ] | `2025-deepseek-grm` | 2025-04 | Reasoning | Generative reward models with Self-Principled Critique Tuning; inference-time scaling of the RM |
| 23 | [ ] | `2025-deepseek-prover-v2` | 2025-04 | Formal math | 671B prover; subgoal decomposition cold start + RL; miniF2F 88.9% |
| 24 | [ ] | `2025-deepseek-v3-insights` | 2025-05 | Arch/Infra | Why V3 looks the way it does; hardware wishlist (ISCA 2025) |
| 25 | [ ] | `2025-deepseek-r1-0528` | 2025-05 | Reasoning | R1 update, more post-training compute (release notes only) |
| 26 | [ ] | `2025-deepseek-v3-1` | 2025-08 | Core | Hybrid think/non-think in one checkpoint; agent/tool-use focus (release notes only) |
| 27 | [ ] | `2025-deepseek-v3-2-exp` | 2025-09 | Core | **DeepSeek Sparse Attention (DSA)** via continued training (GitHub report) |
| 28 | [ ] | `2025-deepseek-ocr` | 2025-10 | Multimodal | Contexts optical compression: 10x text→vision-token compression at ~97% precision |
| 29 | [ ] | `2025-deepseekmath-v2` | 2025-11 | Reasoning | Self-verifiable proofs: generator + verifier trained together; IMO 2025 gold |
| 30 | [ ] | `2025-deepseek-v3-2` | 2025-12 | Core | Production DSA + scaled RL + agentic task synthesis; Speciale variant |
| 31 | [ ] | `2025-mhc` | 2025-12 | Arch | Manifold-constrained Hyper-Connections: stable widened residual stream |
| 32 | [ ] | `2026-engram` | 2026-01 | Arch | Conditional memory lookup as a second sparsity axis beside MoE |
| 33 | [ ] | `2026-deepseek-ocr-2` | 2026-01 | Multimodal | DeepEncoder V2: visual tokens reordered by learned causal flow |
| 34 | [ ] | `2026-deepseek-v4` | 2026-04 | Core | V4-Pro 1.6T/49B, V4-Flash 284B/13B, 1M context, CSA+HCA attention, mHC, Muon |
| 35 | [ ] | `2026-dspark` | 2026-07 | Arch | Confidence-scheduled speculative decoding; beats the MTP-1 serving baseline, replaces MTP in V4.1-Flash |
| 36 | [ ] | `2026-cordis` | 2026-08 | Agents | Spatiotemporal composability paradigm; the plugin substrate under DeepSeek Harness |
| 37 | [ ] | `2026-deepseek-harness` | 2026-08 | Agents | **DeepSeek Harness (`dsh`)**: "Everything is a Plugin" agent harness (repo + docs, no paper) |
| 38 | [ ] | `2026-dsec` | 2026-09 | Infra | DeepSeek Elastic Compute: sandbox infra for agentic RL at scale |
| 39 | [ ] | `2026-deepseek-v4-1-flash` | 2026-09 | Core | KV-cache compression to the limit (CSA2, FP4 KV); multimodal 1M-context MoE |

---

## Recommended reading order

**Core path (15 papers plus 2 companions, ~the whole story).** Read in this order and every later paper will feel like a diff.

1. `2024-deepseek-llm` — the scaling philosophy.
2. `2024-deepseekmoe` — the FFN design.
3. `2024-deepseek-v2` — MLA + MoE at scale; the backbone through V3.2.
4. `2024-deepseekmath` — GRPO; the RL algorithm behind everything after.
5. `2024-deepseek-v3` — the flagship recipe: FP8, MTP, aux-loss-free balancing, DualPipe.
6. `2025-deepseek-r1` — reasoning from RL; read the Nature version for the extra training detail.
7. `2025-deepseek-v3-insights` — the hardware reasoning behind V3's choices.
8. `2025-nsa` → `2025-deepseek-v3-2-exp` → `2025-deepseek-v3-2` — the sparse-attention arc, research → production.
9. `2025-mhc` → `2026-engram` — the two architecture papers behind the V4 generation (mHC ships in V4, Engram only
   in V4.1-Flash).
10. `2026-deepseek-v4` — 1M context, hybrid attention, Muon.
11. `2026-deepseek-v4-1-flash` — the same goal taken further: CED, CSA2, FP4 KV, plus Engram and DSpark.
12. `2026-deepseek-harness` (+ `2026-cordis`, `2026-dsec`) — the agentic layer around the models.

**Side quests by interest.**
- *RL and reward design*: `2025-deepseek-grm` → `2025-deepseekmath-v2` → `2025-codeio`.
- *Formal math*: `2024-deepseek-prover` → `2024-deepseek-prover-v1-5` → `2025-deepseek-prover-v2`.
- *Code*: `2024-deepseek-coder` → `2024-deepseek-coder-v2`.
- *Multimodal*: `2024-deepseek-vl` → `2024-deepseek-vl2`; `2024-janus` → `2024-janusflow` → `2025-janus-pro`; `2025-deepseek-ocr` → `2026-deepseek-ocr-2`.
- *Systems*: `2024-fire-flyer-ai-hpc` → `2025-open-infra-week` → `2025-deepseek-v3-insights` → `2026-dsec`.
- *Efficiency detours*: `2024-aux-loss-free` (after V3), `2026-dspark` (after V4).

---

## Evolution at a glance

| Axis | DeepSeek LLM (2024-01) | V2 (2024-05) | V3 (2024-12) | V3.2 (2025-12) | V4 (2026-04) |
|---|---|---|---|---|---|
| Size (total / active) | 67B dense | 236B / 21B | 671B / 37B | 671B / 37B | 1.6T / 49B (Pro), 284B / 13B (Flash) |
| Attention | MHA (7B), GQA (67B) | **MLA** (latent KV) | MLA | MLA + **DSA** (lightning indexer, top-k) | **CSA + HCA** hybrid (compressed sparse + heavily compressed) |
| FFN | dense | DeepSeekMoE (shared + fine-grained routed) | DeepSeekMoE + aux-loss-free balancing | same | MoE; mHC residuals; no Engram (future work in V4, ships in V4.1-Flash) |
| Context | 4K | 128K | 128K | 128K | 1M |
| Pretraining tokens | 2T | 8.1T | 14.8T | (continued from V3.1-Terminus) | 32–33T |
| Precision | BF16 | BF16 | **FP8 mixed** | FP8 | FP8; FP4 QAT for MoE experts and CSA indexer |
| Optimizer | AdamW | AdamW | AdamW | AdamW | **Muon** (AdamW for embeddings/head/norms) |
| Post-training | SFT + DPO | SFT + **GRPO** | SFT + GRPO, distil from R1 | **Scaled RL** (>10% of pretrain compute), agentic synthesis | Domain experts merged by **on-policy distillation**; 3 effort modes |
| Extra objective | — | — | **MTP** (multi-token prediction) | not discussed | MTP (kept) |

**Training-recipe arc in one paragraph.** DeepSeek LLM fixed the scaling philosophy (model + data allocation by
non-embedding FLOPs/token, hyperparameter scaling laws). DeepSeekMath contributed GRPO: PPO without a critic,
baseline = group mean. V2 was the first flagship to post-train with GRPO; V3 added FP8 training, the MTP
auxiliary objective and aux-loss-free load balancing, and distilled reasoning from R1-lineage models. R1 showed
reasoning emerges from pure RL with rule-based rewards, then packaged it as cold-start SFT → reasoning RL →
rejection-sampling SFT → general RL, and distilled it into small dense models. V3.2 scaled RL compute past 10% of
pretraining and synthesised ~1.8K agentic environments. V4 trains domain experts separately and merges them
via on-policy distillation (replacing V3.2's mixed RL stage), swaps scalar reward models for a generative one,
and runs agent RL in the DSec sandbox.

---

## Track A — Core LLM line

### DeepSeek LLM: Scaling Open-Source Language Models with Longtermism
`2024-deepseek-llm` · arXiv [2401.02954](https://arxiv.org/abs/2401.02954) · 2024-01 · tags: deepseek, llm, scaling
- **What** — 7B and 67B dense models on 2T bilingual tokens, plus a scaling-law study.
- **Architecture** — LLaMA-style pre-norm decoder; 67B uses GQA; 4K context.
- **Recipe** — 2T tokens; SFT then DPO for chat. Scaling laws for batch size and LR; allocates model/data budget
  using non-embedding FLOPs per token rather than parameter count; shows data quality shifts the optimal allocation.
- **Takeaways** — 67B beats LLaMA-2 70B on code/math/reasoning; the "longtermism" framing (invest in scaling
  laws and data, not benchmark chasing) is the house philosophy.
- **Lineage** — root of the series.

### DeepSeek-V2: A Strong, Economical, and Efficient Mixture-of-Experts Language Model
`2024-deepseek-v2` · arXiv [2405.04434](https://arxiv.org/abs/2405.04434) · 2024-05 · tags: deepseek, llm, moe, attention
- **What** — 236B total / 21B active MoE, 128K context; the paper that introduced Multi-head Latent Attention.
- **Architecture** — MLA compresses K/V into a low-rank latent vector (decoupled RoPE key); DeepSeekMoE FFNs with
  2 shared + 160 routed experts, top-6; 60 layers. V2-Lite: 15.7B / 2.4B.
- **Recipe** — 8.1T tokens; SFT on 1.5M conversations; GRPO (first flagship to use it).
- **Takeaways** — vs DeepSeek 67B: 42.5% lower training cost, 93.3% smaller KV cache, 5.76x generation
  throughput. MLA + DeepSeekMoE is the backbone reused through V3 and V3.2 (DSA is instantiated under MLA). V4
  keeps DeepSeekMoE, but its CSA/HCA attention runs shared-KV MQA and the paper no longer mentions MLA.
- **Lineage** — extends `2024-deepseekmoe` (MoE at scale); extends `2024-deepseek-llm` (data, tokenizer);
  uses-method-from `2024-deepseekmath` (GRPO).

### DeepSeek-V3 Technical Report
`2024-deepseek-v3` · arXiv [2412.19437](https://arxiv.org/abs/2412.19437) · 2024-12 · tags: deepseek, llm, moe, low-precision, infra
- **What** — 671B / 37B active MoE, the open frontier model of its moment, trained for ~2.788M H800 GPU-hours.
- **Architecture** — MLA + DeepSeekMoE (1 shared + 256 routed, top-8, node-limited routing); **auxiliary-loss-free
  load balancing** via a per-expert bias term; **Multi-Token Prediction** (depth-1 sequential module, reusable
  for speculative decoding, ~1.8x TPS); 128K via two-stage YaRN extension.
- **Recipe** — 14.8T tokens; **FP8 mixed precision** with fine-grained (tile/block-wise) quantisation and
  increased-precision accumulation; **DualPipe** bidirectional pipeline parallelism overlapping compute and
  all-to-all; custom cross-node EP kernels. Post-training: SFT (1.5M) + GRPO; reasoning distilled from the R1
  lineage. No irrecoverable loss spikes, no rollbacks.
- **Takeaways** — Frontier quality at ~1/10 the reported compute of peers; the engineering (FP8, DualPipe,
  node-limited routing) is as important as the architecture. Base for R1, V3.1, V3.2.
- **Lineage** — extends `2024-deepseek-v2` (same backbone, new balancing/MTP/FP8); uses-method-from
  `2024-deepseekmath` (GRPO); extends `2024-fire-flyer-ai-hpc` (infra stack); uses-method-from
  `2024-aux-loss-free` (load balancing).

### DeepSeek-V3.1 (release notes; no paper)
`2025-deepseek-v3-1` · [api-docs.deepseek.com/news/news250821](https://api-docs.deepseek.com/news/news250821) · 2025-08 · tags: deepseek, llm, agents
- **What** — One checkpoint with thinking and non-thinking modes switched by chat template; stronger tool use.
- **Recipe** — Continued long-context pretraining on V3 (32K phase 630B + 128K phase 209B tokens, ~840B total);
  UE8M0 FP8 scale format for weights/activations. V3.1-Terminus (2025-09) followed as the base for V3.2-Exp.
- **Takeaways** — Thinking mode reaches R1-0528 quality with fewer tokens; first explicit pivot to agents.
- **Lineage** — extends `2024-deepseek-v3`.

### DeepSeek-V3.2-Exp: Boosting Long-Context Efficiency with DeepSeek Sparse Attention
`2025-deepseek-v3-2-exp` · [GitHub report (PDF)](https://github.com/deepseek-ai/DeepSeek-V3.2-Exp/blob/main/DeepSeek_V3_2.pdf) · 2025-09 · tags: deepseek, llm, sparse-attention, long-context
- **What** — Experimental model adding DSA to V3.1-Terminus through continued training.
- **Architecture** — **DSA** = a lightweight *lightning indexer* (few heads, FP8-friendly) scores past tokens,
  then fine-grained **top-k token selection** (k≈2048) feeds MLA. Indexer is still O(L²) but cheap.
- **Recipe** — Dense warm-up where only the indexer learns to mimic full-attention distributions (2.1B tokens),
  then sparse adaptation of all parameters (943.7B tokens). Kernels released in FlashMLA (attention), DeepGEMM
  (indexer logits), TileLang (readable reference).
- **Takeaways** — Parity with V3.1-Terminus (e.g., MMLU-Pro 85.0 vs 85.0, SWE Verified 68.4 vs 67.8) at much
  lower long-context cost; API price cut >50%. The first sparse attention shipped in a production DeepSeek model.
- **Lineage** — extends `2025-deepseek-v3-1` (Terminus base); uses-method-from `2025-nsa` (hardware-aligned
  sparse attention lineage); extends `2024-deepseek-v2` (built on MLA).

### DeepSeek-V3.2: Pushing the Frontier of Open Large Language Models
`2025-deepseek-v3-2` · arXiv [2512.02556](https://arxiv.org/abs/2512.02556) · 2025-12 · tags: deepseek, llm, sparse-attention, rl, agents
- **What** — Production DSA model plus **V3.2-Speciale**, a high-compute reasoning variant.
- **Architecture** — Only architectural change vs V3.1-Terminus is DSA.
- **Recipe** — Scaled RL framework with post-training compute reportedly >10% of pretraining; agentic task
  synthesis (1,827 environments, ~85K prompts) so reasoning transfers into tool use; Speciale trained with a
  relaxed length penalty on reasoning data.
- **Takeaways** — V3.2 reported comparable to GPT-5; Speciale claims gold-level at IMO, CMO, IOI and the ICPC World
  Finals 2025.
  Reasoning + tool use trained jointly, not bolted on.
- **Lineage** — extends `2025-deepseek-v3-2-exp` (DSA); uses-method-from `2025-deepseek-r1` (RL recipe);
  uses-method-from `2024-deepseekmath` (GRPO); uses-method-from `2026-dsec` (per the DSec paper; V3.2 does not name it).

### DeepSeek-V4: Towards Highly Efficient Million-Token Context Intelligence
`2026-deepseek-v4` · arXiv [2606.19348](https://arxiv.org/abs/2606.19348) · 2026-04 (preview 2026-04-24; arXiv record says submitted 2026-04-26 despite the `2606` id) · tags: deepseek, llm, moe, sparse-attention, long-context, agents
- **What** — V4-Pro (1.6T total / 49B active) and V4-Flash (284B / 13B), both with 1M-token context.
- **Architecture** — Interleaved hybrid attention: **Compressed Sparse Attention (CSA)** (compress every m tokens,
  DSA-style top-k plus a sliding window) and **Heavily Compressed Attention (HCA)** (dense over heavily compressed
  tokens), both as shared-KV MQA; **mHC** residual connections; **Muon** optimizer for most modules. Keeps
  DeepSeekMoE and MTP. Engram is not part of V4: the conclusion names it only as future work.
- **Recipe** — 32T (Flash) / 33T (Pro) pretraining tokens; FP8 mixed precision, plus FP4 quantisation-aware training
  for MoE expert weights and the CSA indexer. Post-training trains domain experts, then merges them via multi-teacher
  **on-policy distillation**, which replaces V3.2's mixed RL stage; swaps conventional scalar reward models for a
  rubric-guided generative reward model, with RL applied to the GRM itself; separate length penalties per
  reasoning-effort mode; agent RL in the DSec sandbox.
- **Takeaways** — At 1M tokens V4-Pro needs ~27% of V3.2's single-token FLOPs and ~10% of its KV cache.
  Muon at 1.6T scale is framed as a central contribution. Later releases: V4-Pro GA 2026-08-13, V4.1-Flash 2026-09-10.
- **Lineage** — extends `2025-deepseek-v3-2` (DSA → CSA); uses-method-from `2025-mhc`; uses-method-from
  `2025-nsa` (compression + selection + window); extends `2024-deepseekmoe`; uses-method-from `2026-dsec` (§5.2.5);
  uses-method-from `2025-deepseek-grm` (generative RM; the term matches, but V4 does not cite that paper).

### DeepSeek-V4.1-Flash: Pushing the Limits of KV Cache Compression
`2026-deepseek-v4-1-flash` · arXiv [2609.19969](https://arxiv.org/abs/2609.19969) · 2026-09 (API 2026-09-10; arXiv 2026-09-17) · tags: deepseek, llm, moe, sparse-attention, long-context, vlm, low-precision
- **What** — Multimodal MoE: 552B backbone + 196B Engram parameters, 8B active on prefill and 16B on decode, 1M context.
- **Architecture** — **Causal Encoder-Decoder** (20 + 20 layers, inspired by YOCO): decoder global KV is built from
  encoder outputs, nearly halving prefill. **CSA2** replaces the CSA + HCA hybrid and reuses global KV and Top-K
  indices across layers (Full / Reindex / Reuse modes). With an FP4 global KV cache this reaches 890 bytes/token,
  ~1/4 of V4-Flash; **SWA Bounded Replay** cuts persistent KV to ~1/8. Also Single-Pass mHC, Engram, a Hierarchical
  Sparse Indexer, and **DSpark** in place of MTP.
- **Recipe** — 45T-token pretraining from scratch on a multimodal corpus, with sparse attention trained from the start
  at 64K; RL runs in DSec across heterogeneous scaffolds.
- **Takeaways** — Vendor-reported DeepSWE v1.1: 74.2% vs 62.7% for V4-Pro, 54.4% for V4-Flash, 74.0% for Opus-5.
  Scaffold choice matters: the same checkpoint scores 74.2 on mini-SWE, 69.8 on Claude Code, and 72.6 / 70.5 / 67.6 on
  DeepSeek Harness Minimal / Standard / PTC. First model report to ship Engram. V4.1-Flash-1017 followed on the API on
  2026-10-17.
- **Lineage** — extends `2026-deepseek-v4`; uses-method-from `2026-engram`, `2025-mhc`, `2026-dspark`, `2026-dsec`,
  `2024-aux-loss-free` (modality-specific balancing), `2026-deepseek-harness` (RL and evals).

---

## Track B — Architecture research

### DeepSeekMoE: Towards Ultimate Expert Specialization in Mixture-of-Experts Language Models
`2024-deepseekmoe` · arXiv [2401.06066](https://arxiv.org/abs/2401.06066) · 2024-01 · tags: deepseek, moe
- **What** — The MoE design used in every DeepSeek model since.
- **Architecture** — **Fine-grained expert segmentation** (split each expert into m smaller ones, activate mK of
  mN) for combinatorial flexibility; **shared expert isolation** (always-on experts absorb common knowledge so
  routed experts specialise).
- **Takeaways** — 2B matches GShard 2.9B at ~1.5x less expert compute; 16B ≈ LLaMA-2 7B at ~40% of compute;
  145B preliminary ≈ DeepSeek 67B at a fraction of compute. Specialisation, not just sparsity, is the goal.
- **Lineage** — extends `2024-deepseek-llm`.

### Let the Expert Stick to His Last: Expert-Specialized Fine-Tuning for Sparse Architectural Large Language Models (ESFT)
`2024-esft` · arXiv [2407.01906](https://arxiv.org/abs/2407.01906) · 2024-07 · tags: deepseek, moe, fine-tuning
- **What** — Fine-tune only the experts a task actually routes to; freeze everything else.
- **Recipe** — Score expert relevance on task data (gate scores or token share), select, tune.
- **Takeaways** — Matches or beats full fine-tuning while preserving general ability; up to 90% storage and
  30% training-time savings. Only works because fine-grained MoE experts actually specialise.
- **Lineage** — extends `2024-deepseekmoe`; benchmarks-against full FT on `2024-deepseek-v2` (V2-Lite).

### Auxiliary-Loss-Free Load Balancing Strategy for Mixture-of-Experts
`2024-aux-loss-free` · arXiv [2408.15664](https://arxiv.org/abs/2408.15664) · 2024-08 · tags: deepseek, moe
- **What** — Keeps MoE expert load balanced without an auxiliary loss, so balancing adds no interference gradients.
- **Architecture** — Before top-K routing, add an expert-wise bias to each routing score; update each bias from that
  expert's recent load.
- **Takeaways** — Better performance and better balance than auxiliary-loss methods, validated up to 3B parameters and
  200B tokens. V3 adopts it at 671B; V4.1-Flash extends it to modality-specific balancing.
- **Lineage** — same-problem `2024-deepseekmoe` (MoE training); used by `2024-deepseek-v3`, `2026-deepseek-v4-1-flash`.

### Native Sparse Attention: Hardware-Aligned and Natively Trainable Sparse Attention
`2025-nsa` · arXiv [2502.11089](https://arxiv.org/abs/2502.11089) · 2025-02 · tags: deepseek, sparse-attention, long-context
- **What** — Trainable sparse attention designed around GPU arithmetic intensity; ACL 2025 best paper.
- **Architecture** — Three parallel branches per query: compressed coarse tokens, selected fine-grained blocks,
  sliding window; gated combination. Trained from scratch (27B MoE / 3B active, 64K context).
- **Takeaways** — Matches or beats full attention on general, long-context and reasoning evals while delivering
  up to ~11.6x decode speedup at 64K (also faster forward/backward). Thesis: sparsity must be *trained in* and
  *kernel-aligned*, not applied post hoc. Direct precursor of DSA and of V4's CSA.
- **Lineage** — same-problem `2024-deepseek-v2` (KV/attention cost); extended by `2025-deepseek-v3-2-exp`.

### Insights into DeepSeek-V3: Scaling Challenges and Reflections on Hardware for AI Architectures
`2025-deepseek-v3-insights` · arXiv [2505.09343](https://arxiv.org/abs/2505.09343) · 2025-05 · tags: deepseek, infra, low-precision, moe
- **What** — ISCA 2025 retrospective: how H800 constraints (memory, compute, interconnect) shaped V3.
- **Takeaways** — MLA for memory, MoE for compute/communication trade-off, FP8 for throughput, MTP for
  decode, multi-plane fat-tree for scale-out; 2,048 GPUs total. Ends with a hardware wishlist (native
  low-precision, unified scale-up/scale-out, smarter networks). The closest thing to a design rationale for V3.
- **Lineage** — extends `2024-deepseek-v3`; extends `2024-fire-flyer-ai-hpc`.

### mHC: Manifold-Constrained Hyper-Connections
`2025-mhc` · arXiv [2512.24880](https://arxiv.org/abs/2512.24880) · 2025-12 · tags: deepseek, architecture, scaling
- **What** — Makes widened residual streams (Hyper-Connections, n=4) stable at scale.
- **Architecture** — Constrain the residual mixing matrices to be doubly stochastic (Birkhoff polytope) via
  Sinkhorn–Knopp, restoring the identity-mapping property that unconstrained HC loses.
- **Takeaways** — Fixes signal divergence and training instability of HC; ~6.7% extra time at n=4 after fused
  TileLang kernels; validated to 27B. Adopted in V4, in Engram's reference stack, and as Single-Pass mHC in V4.1-Flash.
- **Lineage** — none inside the corpus (builds on ByteDance Hyper-Connections); used by `2026-deepseek-v4`.

### Conditional Memory via Scalable Lookup: A New Axis of Sparsity for Large Language Models (Engram)
`2026-engram` · arXiv [2601.07372](https://arxiv.org/abs/2601.07372) · 2026-01 (v2 2026-07-12) · tags: deepseek, architecture, moe, scaling
- **What** — Adds an O(1) hashed n-gram embedding lookup ("Engram") as a second sparsity axis beside MoE.
- **Architecture** — Tokenizer compression, multi-head hashing, contextualised gating, multi-branch integration;
  deterministic addressing lets huge tables live in host memory.
- **Takeaways** — U-shaped scaling law for splitting budget between experts and memory; Engram-27B beats
  iso-param / iso-FLOPs MoE; a 100B-parameter table offloaded to host memory adds <3% overhead. Thesis: static
  patterns should not be reconstructed by early transformer layers. V4 lists it as future work; it ships in V4.1-Flash.
- **Lineage** — same-problem `2024-deepseekmoe` (conditional compute); uses-method-from `2025-mhc` (backbone).

### DSpark: Confidence-Scheduled Speculative Decoding with Semi-Autoregressive Generation
`2026-dspark` · arXiv [2607.05147](https://arxiv.org/abs/2607.05147) · 2026-07 · tags: deepseek, llm, efficient-inference
- **What** — Speculative decoding for production serving: draft many tokens per pass, verify only as many as are likely
  to survive.
- **Architecture** — Semi-autoregressive drafter (parallel backbone + lightweight sequential module) to limit suffix
  decay; a confidence head predicts prefix survival, and a scheduler sets each request's verification length from those
  estimates and engine throughput profiles.
- **Takeaways** — Accepted length +26.7–30.9% over Eagle3 and +16.3–18.4% over DFlash on Qwen3 4B/8B/14B targets. In V4
  serving under live traffic, per-user speed +60–85% (Flash) and +57–78% (Pro) vs MTP-1 at matched throughput. Checkpoints
  and the DeepSpec training repo are open.
- **Lineage** — benchmarks-against `2024-deepseek-v3` (MTP-1 baseline); used by `2026-deepseek-v4-1-flash`.

---

## Track C — Reasoning and reinforcement learning

### DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models
`2024-deepseekmath` · arXiv [2402.03300](https://arxiv.org/abs/2402.03300) · 2024-02 · tags: deepseek, math, rl, reasoning
- **What** — 7B math model that introduced **GRPO**.
- **Recipe** — 120B math tokens mined from Common Crawl with an iterative fastText classifier; initialised from
  DeepSeek-Coder-Base-v1.5 7B; SFT; then **Group Relative Policy Optimization**: PPO without a value network,
  advantage = reward minus group mean over G samples of the same prompt, KL to reference in the loss.
- **Takeaways** — MATH 51.7% (7B, no tools), 60.9% with self-consistency@64; code pretraining helps math.
  GRPO's memory saving is why DeepSeek could afford RL at 671B scale later.
- **Lineage** — extends `2024-deepseek-coder` (init checkpoint); uses-method-from `2024-deepseek-llm`.

### DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning
`2025-deepseek-r1` · arXiv [2501.12948](https://arxiv.org/abs/2501.12948) · 2025-01 · Nature 645:633–638 (2025-09-17), [doi:10.1038/s41586-025-09422-z](https://doi.org/10.1038/s41586-025-09422-z) · tags: deepseek, rl, reasoning, distillation
- **What** — Shows reasoning emerges from pure RL (R1-Zero) and packages it into a usable model (R1).
- **Recipe** — *R1-Zero*: GRPO on V3-Base with rule-based accuracy + format rewards, no SFT; AIME 2024 pass@1
  15.6% → 77.9% in the current v2 text (71.0% in v1), 86.7% with majority voting; self-verification and "aha
  moments" emerge, but readability and language mixing suffer. *R1*: cold-start SFT on thousands of long CoTs →
  reasoning RL with a language-consistency reward → rejection-sampling SFT (~600K reasoning + ~200K general) → RL
  for helpfulness/harmlessness. *Distillation*: SFT Qwen2.5/Llama 1.5B–70B on ~800K R1 samples. PRMs and MCTS
  reported as failed attempts.
- **Takeaways** — Outcome-reward RL beats process supervision here; distillation beats RL on small models; the
  Nature version adds training details, intermediate checkpoints, a safety report, and discloses ~$294K for the
  RL stage (excluding the base model). First mainstream LLM to pass peer review.
- **Lineage** — uses-method-from `2024-deepseekmath` (GRPO); extends `2024-deepseek-v3` (base).

### DeepSeek-R1-0528 (release notes; no paper)
`2025-deepseek-r1-0528` · [HF model card](https://huggingface.co/deepseek-ai/DeepSeek-R1-0528) · 2025-05 · tags: deepseek, rl, reasoning
- **What** — Same architecture, more post-training compute.
- **Takeaways** — AIME 2025 70.0 → 87.5, LiveCodeBench 63.5 → 73.3; reasoning tokens per question ~12K → ~23K;
  enhanced function-calling support. Distilled R1-0528-Qwen3-8B scores 86.0 on AIME 2024. Useful as a
  data point on how far post-training compute alone moves reasoning.
- **Lineage** — extends `2025-deepseek-r1`.

### CodeI/O: Condensing Reasoning Patterns via Code Input-Output Prediction
`2025-codeio` · arXiv [2502.07316](https://arxiv.org/abs/2502.07316) · 2025-02 · tags: deepseek, reasoning, code
- **What** — Turn ~450K functions into ~3.5M "predict the output / predict the input" tasks with natural-language
  CoT, to teach general reasoning.
- **Recipe** — Two-stage: CodeI/O data then general instruction tuning; CodeI/O++ verifies by execution and
  revises wrong CoTs over multiple turns. (Collaboration with HKUST; code outside the deepseek-ai org.)
- **Takeaways** — Gains across symbolic, scientific, logic, math and commonsense reasoning, not just code.
  Evidence that code's *procedural structure* is a transferable reasoning curriculum.
- **Lineage** — same-problem `2024-deepseekmath` (reasoning data); weak link to `2024-deepseek-coder`.

### Inference-Time Scaling for Generalist Reward Modeling (DeepSeek-GRM, SPCT)
`2025-deepseek-grm` · arXiv [2504.02495](https://arxiv.org/abs/2504.02495) · 2025-04 · tags: deepseek, rl, reward-modeling
- **What** — Pointwise generative reward models that get better when you sample them more.
- **Recipe** — **Self-Principled Critique Tuning**: the RM generates its own principles, then critiques, then
  scores; rejective fine-tuning cold start, then rule-based online RL (GRPO-style). Inference: sample k times in
  parallel, vote, optionally guided by a meta-RM. Base: Gemma-2-27B.
- **Takeaways** — A 27B GRM with inference-time scaling rivals far larger RMs on RewardBench/PPE/RMB. The
  reward model becomes a reasoning model; this is the conceptual bridge to Math-V2's verifier.
- **Lineage** — uses-method-from `2024-deepseekmath` (GRPO); uses-method-from `2025-deepseek-r1` (rule-based RL).

### DeepSeekMath-V2: Towards Self-Verifiable Mathematical Reasoning
`2025-deepseekmath-v2` · arXiv [2511.22570](https://arxiv.org/abs/2511.22570) · 2025-11 · tags: deepseek, math, rl, reasoning, reward-modeling
- **What** — Train a proof *verifier* and a proof *generator* together so the model finds and fixes errors in its
  own natural-language proofs.
- **Recipe** — LLM verifier as reward model for the generator; generator rewarded for self-verified,
  self-corrected proofs; scale verification compute to auto-label hard proofs so the verifier stays ahead of the
  generator. Base: DeepSeek-V3.2-Exp.
- **Takeaways** — Gold-level IMO 2025 and CMO 2024; 118/120 on Putnam 2024 with scaled test-time compute.
  Argument: a correct final answer does not certify correct reasoning, so reward the proof, not the answer.
- **Lineage** — extends `2025-deepseek-r1` (RL for reasoning); uses-method-from `2025-deepseek-grm` (generative
  critique as reward); extends `2024-deepseekmath` (name and GRPO lineage).

---

## Track D — Code and formal mathematics

### DeepSeek-Coder: When the Large Language Model Meets Programming — The Rise of Code Intelligence
`2024-deepseek-coder` · arXiv [2401.14196](https://arxiv.org/abs/2401.14196) · 2024-01 · tags: deepseek, code, llm
- **What** — 1.3B–33B code models trained from scratch on 2T tokens (87% code, 10% code-related English, 3% Chinese).
- **Recipe** — Repository-level data construction (dependency-ordered files), fill-in-the-middle, 16K window;
  pretraining then instruction tuning, no RL.
- **Takeaways** — Instruct 33B beats GPT-3.5-Turbo on most reported code benchmarks; permissive licence.
  Its 7B base (v1.5) seeds DeepSeekMath.
- **Lineage** — extends `2024-deepseek-llm` (architecture); extended by `2024-deepseekmath`.

### DeepSeek-Coder-V2: Breaking the Barrier of Closed-Source Models in Code Intelligence
`2024-deepseek-coder-v2` · arXiv [2406.11931](https://arxiv.org/abs/2406.11931) · 2024-06 · tags: deepseek, code, moe
- **What** — Continue-pretrain an intermediate DeepSeek-V2 checkpoint on 6T more tokens (60% code, 10% math, 30% NL).
- **Recipe** — 16B (Lite) and 236B MoE variants; 338 languages (from 86); 128K context; RL stage with
  GRPO, using a reward model trained on compiler / test-case feedback because the raw 0-1 signal is noisy.
- **Takeaways** — Reported to match GPT-4-Turbo / Claude 3 Opus on code and math; HumanEval 90.2%, MATH 75.7%.
  Shows the V2 backbone absorbs a specialist continue-pretrain cleanly.
- **Lineage** — extends `2024-deepseek-coder`; extends `2024-deepseek-v2` (checkpoint); uses-method-from
  `2024-deepseekmath` (GRPO, math corpus).

### DeepSeek-Prover: Advancing Theorem Proving in LLMs through Large-Scale Synthetic Data
`2024-deepseek-prover` · arXiv [2405.14333](https://arxiv.org/abs/2405.14333) · 2024-05 · tags: deepseek, theorem-proving, math
- **What** — Lean 4 prover fine-tuned on ~8M synthetic formal statement/proof pairs.
- **Recipe** — Autoformalise competition problems → filter → generate proofs → verify in Lean → iterate.
  Base: DeepSeekMath-Base 7B, SFT only.
- **Takeaways** — miniF2F-test 46.3% whole-proof at 64 samples (52.0% cumulative) vs GPT-4 ~23%.
  Synthetic formal data at scale works when a verifier filters it.
- **Lineage** — extends `2024-deepseekmath`.

### DeepSeek-Prover-V1.5: Harnessing Proof Assistant Feedback for Reinforcement Learning and Monte-Carlo Tree Search
`2024-deepseek-prover-v1-5` · arXiv [2408.08152](https://arxiv.org/abs/2408.08152) · 2024-08 · tags: deepseek, theorem-proving, rl
- **What** — 7B prover with RL from Lean verification feedback and RMaxTS tree search.
- **Recipe** — SFT on enhanced proof data → GRPO with binary Lean-verified reward (RLPAF) → RMaxTS, an MCTS
  variant with intrinsic exploration reward for sparse-reward search.
- **Takeaways** — miniF2F-test 60.2% single-pass, 63.5% with RMaxTS (V1: 50.0%); ProofNet 25.3%.
  Verifier-as-reward is the whole trick; MCTS adds a few points on top.
- **Lineage** — extends `2024-deepseek-prover`; uses-method-from `2024-deepseekmath` (GRPO).

### DeepSeek-Prover-V2: Advancing Formal Mathematical Reasoning via Reinforcement Learning for Subgoal Decomposition
`2025-deepseek-prover-v2` · arXiv [2504.21801](https://arxiv.org/abs/2504.21801) · 2025-04 · tags: deepseek, theorem-proving, rl
- **What** — 7B and 671B Lean 4 provers with recursive subgoal decomposition.
- **Recipe** — DeepSeek-V3 writes a natural-language sketch and a Lean skeleton with `sorry` placeholders; the 7B
  prover fills subgoals; composed proofs + CoT become cold-start data; then GRPO with Lean reward.
- **Takeaways** — miniF2F-test 88.9% (pass@8192); PutnamBench 49/658; introduces ProverBench (325 problems,
  15 formalised AIME). Informal reasoning and formal proving unified in one model.
- **Lineage** — extends `2024-deepseek-prover-v1-5`; uses-method-from `2025-deepseek-r1` (long-CoT RL);
  uses-method-from `2024-deepseek-v3` (sketch generator).

---

## Track E — Multimodal

### DeepSeek-VL: Towards Real-World Vision-Language Understanding
`2024-deepseek-vl` · arXiv [2403.05525](https://arxiv.org/abs/2403.05525) · 2024-03 · tags: deepseek, vlm
- **What** — 1.3B / 7B VLMs on DeepSeek-LLM, built for real-world documents, charts and screenshots.
- **Architecture** — Hybrid encoder: SigLIP-L (384px, semantics) + SAM-B (1024px, detail) → 576 visual tokens via
  a two-layer MLP adaptor.
- **Recipe** — Stage 1 adaptor only; stage 2 joint VL pretraining keeping a large share of text data (~70%) to
  avoid forgetting; stage 3 SFT (also unfreezes SigLIP).
- **Takeaways** — Fine detail at a fixed token cost; the "don't lose the LLM" recipe becomes standard.
- **Lineage** — extends `2024-deepseek-llm`.

### Janus: Decoupling Visual Encoding for Unified Multimodal Understanding and Generation
`2024-janus` · arXiv [2410.13848](https://arxiv.org/abs/2410.13848) · 2024-10 · tags: deepseek, vlm, image-generation
- **What** — One autoregressive transformer, two visual encoders: SigLIP for understanding, a VQ tokenizer for
  generation.
- **Takeaways** — Decoupling removes the conflict between semantic features (understanding) and low-level codes
  (generation); 1.3B model matches task-specific baselines. Simple, and it stuck.
- **Lineage** — extends `2024-deepseek-vl` (understanding path); extends `2024-deepseek-llm` (backbone).

### JanusFlow: Harmonizing Autoregression and Rectified Flow for Unified Multimodal Understanding and Generation
`2024-janusflow` · arXiv [2411.07975](https://arxiv.org/abs/2411.07975) · 2024-11 · tags: deepseek, vlm, image-generation
- **What** — Janus with continuous rectified-flow generation instead of discrete VQ tokens.
- **Recipe** — Decoupled encoders plus representation alignment between them during unified training.
- **Takeaways** — 1.3B: MJHQ FID-30k 9.51, GenEval 0.63, DPG-Bench 80.09. Shows AR understanding and
  diffusion-style generation can share one LLM.
- **Lineage** — extends `2024-janus`.

### DeepSeek-VL2: Mixture-of-Experts Vision-Language Models for Advanced Multimodal Understanding
`2024-deepseek-vl2` · arXiv [2412.10302](https://arxiv.org/abs/2412.10302) · 2024-12 · tags: deepseek, vlm, moe
- **What** — VLM family on DeepSeekMoE + MLA language models with dynamic tiling for high-res, any-aspect images.
- **Architecture** — Vision encoder → adaptor → MoE LLM; Tiny / Small / base with 0.57B / 2.4B / 4.1B activated
  LLM params (HF cards quote 1.0B / 2.8B / 4.5B including vision).
- **Takeaways** — Competitive or SOTA at equal or fewer activated params; MLA makes multimodal serving cheap;
  dynamic tiling replaces the fixed SAM+SigLIP hybrid.
- **Lineage** — extends `2024-deepseek-vl`; uses-method-from `2024-deepseek-v2` (MLA); uses-method-from `2024-deepseekmoe`.

### Janus-Pro: Unified Multimodal Understanding and Generation with Data and Model Scaling
`2025-janus-pro` · arXiv [2501.17811](https://arxiv.org/abs/2501.17811) · 2025-01 · tags: deepseek, vlm, image-generation
- **What** — Janus scaled to 1B and 7B with a better schedule and ~72M synthetic aesthetic images (1:1 with real).
- **Takeaways** — 7B: MMBench 79.2 (Janus 69.4), GenEval ~0.80. Gains come from data and schedule, not a new
  architecture; synthetic aesthetic data stabilises text-to-image.
- **Lineage** — extends `2024-janus`.

### DeepSeek-OCR: Contexts Optical Compression
`2025-deepseek-ocr` · arXiv [2510.18234](https://arxiv.org/abs/2510.18234) · 2025-10 · tags: deepseek, vlm, ocr, long-context
- **What** — Can a page of text be stored as a few vision tokens? OCR is the testbed for "optical context compression".
- **Architecture** — DeepEncoder (SAM-base ~80M → 16x conv compressor → CLIP-large ~300M) feeding a
  DeepSeek-3B-MoE decoder (~570M active).
- **Takeaways** — Fox benchmark: ~97% OCR precision at <10x compression, ~60% at 20x; 200K+ pages/day on one
  A100-40G. Pitched as a path to cheap long-context memory; a third-party critique (arXiv 2601.03714) argues it
  leans on language priors.
- **Lineage** — uses-method-from `2024-deepseekmoe` (decoder); same-problem `2024-deepseek-vl` (document understanding).

### DeepSeek-OCR 2: Visual Causal Flow
`2026-deepseek-ocr-2` · arXiv [2601.20552](https://arxiv.org/abs/2601.20552) · 2026-01 · tags: deepseek, vlm, ocr
- **What** — Replaces DeepEncoder's CLIP half with an LLM-style encoder that learns to *reorder* visual tokens by
  content rather than raster order.
- **Architecture** — DeepEncoder V2: SAM-based tokenizer (16x compression) → Qwen2-0.5B-style transformer where
  learnable causal-flow queries form a causal suffix; 256–1,120 visual tokens; decoder unchanged (3B MoE; the
  paper's figure says A570M, its text about 500M active).
- **Takeaways** — OmniDocBench v1.5 91.09 (+3.73 over OCR 1); reading-order edit distance 0.085 → 0.057.
  The comparison is OCR 1 vs OCR 2; the paper has no ablation isolating causal flow.
- **Lineage** — extends `2025-deepseek-ocr`.

---

## Track F — Infrastructure and systems

### Fire-Flyer AI-HPC: A Cost-Effective Software-Hardware Co-Design for Deep Learning
`2024-fire-flyer-ai-hpc` · arXiv [2408.14158](https://arxiv.org/abs/2408.14158) · 2024-08 (SC'24) · tags: deepseek, infra
- **What** — The cluster DeepSeek trained on before V3: ~10,000 PCIe A100s, two-zone fat-tree, custom stack.
- **Takeaways** — HFReduce (CPU-assisted allreduce), HaiScale (parallelism), **3FS** (file system), HAI-Platform
  (scheduling); ~80% of DGX-A100 performance at ~50% cost and ~40% less energy (reported). Explains the
  cost discipline that shaped V2/V3.
- **Lineage** — root of the infra track; extended by `2024-deepseek-v3`, `2025-deepseek-v3-insights`.

### Open Infra Week + 3FS (repos and docs; no paper)
`2025-open-infra-week` · [open-infra-index](https://github.com/deepseek-ai/open-infra-index) · 2025-02 · tags: deepseek, infra, moe, low-precision
- **What** — Six days of production kernels: [FlashMLA](https://github.com/deepseek-ai/FlashMLA) (MLA decode,
  ~580 TFLOPS BF16 on H800), [DeepEP](https://github.com/deepseek-ai/DeepEP) (expert-parallel all-to-all),
  [DeepGEMM](https://github.com/deepseek-ai/DeepGEMM) (FP8 GEMM), [DualPipe](https://github.com/deepseek-ai/DualPipe),
  [EPLB](https://github.com/deepseek-ai/eplb), [profile-data](https://github.com/deepseek-ai/profile-data),
  [3FS](https://github.com/deepseek-ai/3FS) (6.6 TiB/s aggregate read on 180 nodes; CRAQ replication,
  FoundationDB metadata), smallpond, and the "V3/R1 Inference System Overview" (73.7K input / 14.8K output
  tokens/s per H800 node; theoretical 545% margin).
- **Takeaways** — The concrete artefacts behind V3's FP8/DualPipe/EP claims. Read alongside V3 §3 and the
  Insights paper. Record as one note or skip; it is not a paper.
- **Lineage** — uses-method-from `2024-deepseek-v3`; uses-method-from `2024-fire-flyer-ai-hpc` (3FS).

### DeepSeek Elastic Compute (DSec): A Sandbox Infrastructure for Effective Agentic Training at Scale
`2026-dsec` · arXiv [2609.22978](https://arxiv.org/abs/2609.22978) · 2026-09 · tags: deepseek, infra, agents, rl
- **What** — Unified sandbox platform (function-call, container, microVM, full VM) for agentic RL rollouts.
- **Takeaways** — A production unit spans ~160 nodes, ~3M sandboxes/day, 380K+ concurrent; serves RL for V3.2
  through V4.1; built on 3FS; 130+ authors (DeepSeek-AI, Tsinghua). The missing piece between "scaled RL" in
  V3.2 and "agent RL" in V4.
- **Lineage** — uses-method-from `2025-open-infra-week` (3FS); used by `2025-deepseek-v3-2`, `2026-deepseek-v4`,
  `2026-deepseek-v4-1-flash`.

---

## Track G — Agents and the DeepSeek Harness

### DeepSeek Harness (`dsh`): "Everything is a Plugin"
`2026-deepseek-harness` · [github.com/deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) · docs: [deepseek-harness.github.io](https://deepseek-harness.github.io/deepseek-harness) · 2026-08 (developer preview; repo created 2026-08-13) · tags: deepseek, agents
- **What** — Official, MIT-licensed, TypeScript agent / coding-agent harness from DeepSeek. Model adapter, tool
  registry, agent loop, session store and sandbox are all swappable plugins on the Cordis meta-framework.
  CLI `dsh`; Web UI via `npx @deepseek-ai/dsh web`. Shipped profiles: `web`, `headless`, `sdk`, `sdk-minimal`, `acp`. The
  *Minimal* preset is a bare persistent-bash runtime for RL and evals (earlier versions also had `str_replace_editor`).
- **Status** — Developer preview; README warns of breaking changes. No DeepSeek-authored paper; the README cites
  the Cordis paper (below). `benchmarks/` holds runtime and UI performance suites, not agent-task evals. Agent numbers
  are in V4.1-Flash §5.3.4: DeepSWE v1.1 72.6 / 70.5 / 67.6 and Terminal-Bench v2.1 90.6 / 85.8 / 85.8 in Minimal /
  Standard / PTC.
- **Takeaways** — DeepSeek treating the harness as a first-class, open research object rather than a product
  wrapper; V4.1-Flash is evaluated inside it. Companion: [dsh-superagent-prototype](https://github.com/deepseek-ai/dsh-superagent-prototype),
  a proactive repo-level coding agent (listens to GitHub/Feishu, opens work items, replies with PRs), explicitly
  labelled a research prototype.
- **Lineage** — uses-method-from `2026-cordis`; used by `2026-deepseek-v4-1-flash` (RL and evals).

### A Programming Paradigm for Spatiotemporal Composability (Cordis)
`2026-cordis` · arXiv [2608.25512](https://arxiv.org/abs/2608.25512) · 2026-08 · tags: deepseek, agents
- **What** — cs.PL paper: revertible effects (temporal composability via runtime-held inverses) plus reactive
  coeffects (spatial composability via dependency checks); [Cordis](https://github.com/cordiverse/cordis) is the
  TypeScript implementation, with hot module replacement. Koishi, a chatbot framework built on it with 4,000+ plugins,
  is the case study. Authors: Yifan Shi (Peking University, DeepSeek-AI), Wei Zhang (Peking University), Tianyi Cui (DeepSeek-AI).
- **Takeaways** — Relevant mainly as the substrate of the Harness, though the paper itself never names it. At 92 pages,
  read §1 and §5 for the plugin and hot-reload model; §3–4 are the formalism.
- **Lineage** — none inside the corpus; used by `2026-deepseek-harness`.

---

## Cross-cutting takeaways

**Architecture**
- Attention cost is attacked four times: MLA (compress KV), DSA/NSA (select which tokens), CSA/HCA (compress
  *and* select, then go dense over compressed), CSA2 (share KV and selections across layers). The idea compounds, but
  parts get replaced: the V4 paper no longer mentions MLA, and V4.1-Flash drops HCA.
- MoE stays fine-grained + shared-expert from 2024-01 onward; what changes is *balancing* (aux loss → bias term)
  and *what else is sparse* (Engram memory).
- Residual stream and optimizer only change in 2026 (mHC, Muon), after everything else was squeezed.
- Multimodal was "bolt a vision path onto the current LLM" until V4.1-Flash, which pretrains on multimodal data from
  the start. Before that, the novelty is in encoders (hybrid, dynamic tiling, DeepEncoder, causal flow), not the fusion.

**Training recipe**
- GRPO is the constant. Rewards move from scalar RMs → rule-based (R1) → generative critiques (GRM) → learned
  verifiers (Math-V2, Prover) → environment outcomes in sandboxes (V3.2, DSec, V4), with a generative RM back in
  V4 for hard-to-verify tasks.
- Synthetic data pipelines are a recurring edge: autoformalisation (Prover), CodeI/O, agentic task synthesis
  (V3.2), aesthetic synthetic images (Janus-Pro).
- Distillation closes every loop: R1 → small dense; R1 → V3; V4 experts → one model via on-policy distillation.

**Systems**
- Every flagship ships with the kernels (FlashMLA, DeepGEMM, DeepEP) and a hardware post-mortem. Read the
  model report and the infra artefacts as one unit.

---

## Mentioned, not in list

Repos and third-party items that are context, not reading-list entries:
- DeepSeek repos without papers of their own: DeepInfer (inference framework), DeepJIT (kernel JIT), DeepSpec (speculative
  decoding stack, released with `2026-dspark`), DeepSelect (top-k kernels for DSA), TileKernels, LPLB (LP-based
  expert load balancer), DeepEP-Ascend / DeepGEMM-Ascend (Huawei Ascend ports), deepseek-recipe,
  awesome-deepseek-agent.
- Hyper-Connections (ByteDance, 2024) — the paper mHC fixes.
- arXiv 2601.03714 — third-party critique of DeepSeek-OCR.
- "DeepSeek-V4-Flash-Vision-Exp" (API, 2026-08-21) and "DeepSeek-V4.1-Flash-1017" (API, 2026-10-17) — release notes
  only; no dedicated report found.
- *Exploring Super-agent Design: Towards a More Autonomous Agent System* — article named in the
  `dsh-superagent-prototype` README; dated 2026-10-31 by press coverage. The article itself was not located ⚠.
- Share authors with DeepSeek staff but left out as not part of the series: arXiv 2406.14024 (math verifier critics),
  2409.02795 (preference-learning survey), 2403.00231 (Multimodal ArXiv), 2402.16141 (PeriodicLoRA).
- Press claims of a "memory-offload training paper" (SCMP, 2026-01) — almost certainly Engram; not a separate item.

---

## Verification notes

- **Second pass, 2026-11-07.** arxiv.org, huggingface.co and GitHub were reachable, so every ⚠ from the first pass was
  rechecked against its primary source (PDF, model card, release notes or repo). Only the super-agent article keeps a ⚠.
- **What "checked" means.** Targeted text search of each PDF, with key passages read in context; no paper was read cover
  to cover. All 34 arXiv ids, titles and dates were compared with arXiv records, and all links were opened. For 2024–2025
  entries, 145 headline figures and terms were searched for in the PDF text: 141 direct hits, and 4 resolved by hand (one
  was the R1 correction below). A hit shows a figure appears, not that its context matches. Figures outside that search
  in unflagged bullets remain as compiled.
- **Corrected in this pass.**
  - R1: AIME 2024 is 77.9% in the current v2; the 71.0% came from v1.
  - R1-0528: dropped "JSON output", which neither the model card nor the API notes mention.
  - Cordis: the paper itself lists a DeepSeek-AI affiliation; Koishi is a case study built on Cordis, not its origin.
  - Harness: Minimal is bash-only; `benchmarks/` is not agent evals; the `benchmarks-against` candidate edge pointed the
    wrong way and is replaced by `2026-deepseek-v4-1-flash` uses-method-from `2026-deepseek-harness`.
  - V4: keeps MTP, uses a generative reward model, and trains with FP4 rather than merely mentioning it.
  - V2 / cross-cutting: MLA does not carry into the V4 paper.
  - Engram: the table is 100B parameters, not 100B entries.
  - DSec: dropped the unsupported `same-problem 2025-deepseek-r1` candidate edge (DSec's stated scope starts at V3.2).
  - Core path: the "12 papers" header undercounted.
- **First-pass open questions, now closed.** V4's date: arXiv records submission on 2026-04-26 despite the `2606` id, and
  does not explain the mismatch. Engram in V4: no, future work only; it first ships in V4.1-Flash. V4.1-Flash details:
  confirmed in the PDF, with CED, DSpark and 196B of Engram parameters added.
- **Coverage.** arXiv author searches on nine core DeepSeek authors found `2024-aux-loss-free` and `2026-dspark` missing.
  This is not proof of completeness: the same searches did not return two papers already listed (2510.18234, 2608.25512).
- Benchmark numbers are as reported by the authors.
