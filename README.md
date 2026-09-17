## Henry Zhang

Quantitative engineer. Fifteen years building the production systems behind systematic
investing — data platforms, research platforms, and live trading pipelines. Eight years at
**BlackRock**, then **PIMCO**, and currently at a global asset manager in Los Angeles.

Three times over, the same problem: closing the gap between quant research and production,
so researchers can ship models without an engineering bottleneck in the way.

Lately the same question, asked of a market rather than a team: what does it take to turn a
pile of published prices into a number somebody could settle a contract against — and how do
you know when the honest answer is that you cannot?

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

### Token Price Index

The same question asked of LLM inference, and a different answer: **most of this
market cannot carry an index at all.** A frontier model has exactly one seller,
so there is no second price to discover and an average of one company's list
price is that company's list price wearing an index's name. Open weights are the
opposite — the same weights served by many sellers competing on price — and that
is the only place a token benchmark means anything.

Collected daily from live per-seller pricing. Six contracts, and the refusals are
the product: one withheld on dispersion, one refused by construction.

Building it turned up something I did not expect. **Fifteen of twenty-seven
sellers of the same weights quote an identical price**, so the median *is* that
price, more than half the deviations from it are zero, and the median absolute
deviation is zero — the dispersion gate reported perfect agreement on a market
spanning six times. Qn fails identically, because more than a quarter of pairwise
differences are also zero. The compute benchmark has no such problem: no two GPU
providers quote alike, because rental prices are set independently while token
prices are copied from a publisher's reference rate.

Two indices, two scale estimators, and the justification is measured rather than
stylistic.

**[→ The findings, with the numbers](https://github.com/henryzhangpku/token-price-index/blob/main/docs/FINDINGS.md)**

---

### Autonomous Quant Researcher

An LLM proposes trading hypotheses; trusted code decides whether they are true.
A bounded research loop that takes the fixed experiment contract from Karpathy's
`autoresearch` and the loop-as-artifact discipline from Loop Engineering, then
adds what finance forces on you: the model never writes code (declarative JSON
hypotheses, trusted interpretation), three chronological stages with a one-use
holdout, acceptance as a gate set rather than a metric, admission-time
de-duplication, and a hash-chained ledger that keeps every refutation.

Most of what comes back is a documented no, and the ledger keeps those too — a
refutation nobody wrote down gets rediscovered, at cost, by the next person.
**Now open source**: the runner, the declarative contract, fixed validators,
the options backtest mechanics, ~50 preregistered experiments, 17 missions with
their findings, and 329 tests that need neither network nor keys.

**[→ github.com/henryzhangpku/autonomous-quant-researcher](https://github.com/henryzhangpku/autonomous-quant-researcher)**

---

### Selected repositories

| | |
|---|---|
| **[QuantDev](https://github.com/henryzhangpku/QuantDev)** | Working code from the [QuantDev](https://www.youtube.com/@QuantDevXYZ) channel — quant research notebooks |
| **[autonomous-quant-researcher](https://github.com/henryzhangpku/autonomous-quant-researcher)** | An LLM proposes trading hypotheses, trusted code decides — staged holdouts, gate sets, and a hash-chained ledger of every refutation |
| **[gpu-price-index](https://github.com/henryzhangpku/gpu-price-index)** | A GPU rental price benchmark built like a settlement index — waterfall, robust estimation, gates that withhold |
| **[token-price-index](https://github.com/henryzhangpku/token-price-index)** | A price benchmark for LLM inference, and the goods it refuses to index |

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
