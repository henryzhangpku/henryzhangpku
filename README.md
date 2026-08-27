## Henry Zhang

Quantitative engineer. Fifteen years building the production systems behind systematic
investing — data platforms, research platforms, and live trading pipelines. Eight years at
**BlackRock**, then **PIMCO**, and currently at a global asset manager in Los Angeles.

Three times over, the same problem: closing the gap between quant research and production,
so researchers can ship models without an engineering bottleneck in the way.

Lately I've been interested in how far that idea goes when you remove the human from the
loop entirely.

---

### Autonomous Quant Researcher

An agent-driven research system that generates hypotheses, runs experiments, applies
validation gates, and records verdicts — continuously, without manual prompting.
386 research sessions to date, with every trial including the refutations kept on a
permanent ledger.

The loop: `Ask → Compile → Propose → Admit → Evaluate → Verdict → Learn`

**[→ Architecture and research discipline](https://github.com/henryzhangpku/autonomous-quant-researcher)**

---

### GPU Compute Price Benchmark

A daily rental price index for GPU compute, built the way a settlement benchmark
has to be built rather than the way a dashboard can be. Five indices over ~20
clouds, from live public pricing.

The engineering is the easy half. The hard half is deciding what an "H100-hour"
even is when a PCIe card on Ethernet and an SXM card on an NVLink fabric differ
threefold and are not substitutes — then defending that decision to a
counterparty who lost money on the print.

A three-tier waterfall, MAD-based outlier screening, per-provider weight caps,
and publication gates that **withhold rather than guess**: two of the five
indices decline to print on a typical day, and both refusals are correct.
Storage is bitemporal and append-only, so *what did the tape say on the 25th,
as known on the 26th?* stays answerable after any correction.

**[→ Methodology, and what the data turned out to show](https://github.com/henryzhangpku/gpu-price-index)**

---

### Selected repositories

| | |
|---|---|
| **[autonomous-quant-researcher](https://github.com/henryzhangpku/autonomous-quant-researcher)** | Agent-driven research loop — gates, immutable evaluators, and a ledger that records failures |
| **[QuantDev](https://github.com/henryzhangpku/QuantDev)** | Working code from the [QuantDev](https://www.youtube.com/@QuantDevXYZ) channel — quant research notebooks |
| **[gpu-price-index](https://github.com/henryzhangpku/gpu-price-index)** | A GPU rental price benchmark built like a settlement index — waterfall, robust estimation, gates that withhold |

---

### Background

| | |
|---|---|
| **Global asset manager** | Lead Quantitative Engineer, VP — research platform (2025 – present) |
| **PIMCO** | Quantitative Developer / Architect, VP — systematic futures & FX trading |
| **BlackRock** | Quantitative Developer, VP — systematic equity signals, 8 years |
| **Morgan Stanley** | Commodities Developer — trading systems, Shanghai / Singapore |

MS Software Engineering, Peking University · BS Computer Science, Nankai University

---

[LinkedIn](https://www.linkedin.com/in/henryzhang99/) · [officialhenryzhang.com](https://www.officialhenryzhang.com/)
