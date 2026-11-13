## Henry Zhang

I build trading platforms and then I run them. The engineering is the easy half; deciding
what should exist, and what should never ship, is the job.

Fifteen years building the production systems behind systematic investing — data platforms,
research platforms, and live trading pipelines. Eight years at **BlackRock**, then **PIMCO**,
and currently at a global asset manager in Los Angeles.

Three times over, the same problem: closing the gap between quant research and production,
so researchers can ship models without an engineering bottleneck in the way.

The trading side is the point: one code path from backtest to live, risk that fails closed, and
research that is allowed to say "no edge" before money finds out.

**Start here**: three projects, each solving a different problem, each with a live page or code you can try:
[autonomous-quant-researcher](https://henryzhangpku.github.io/autonomous-quant-researcher/) (deciding what is true: an LLM proposes, code decides) ·
[research2prod](https://github.com/henryzhangpku/research2prod) (shipping it: research code that is already production code) ·
[mft-engine](https://henryzhangpku.github.io/mft-engine/) (running it: one Rust code path for backtest and live)

### Papers

All November 2026, Henry Zhang, Independent Researcher. Each one pre-registered, with the code public.

- **[Hard to Fool: A Bounded LLM Research Loop for Quantitative Finance, and What Two Dozen Campaigns Found](https://arxiv.org/abs/2611.06607)** · [arXiv:2611.06607](https://arxiv.org/abs/2611.06607) · [SSRN](https://ssrn.com/abstract=7682019)
  An LLM proposes trading hypotheses, trusted code decides, and most of what two dozen campaigns found was a documented no.
- **[Short Windows, Unmodelled Costs, Unknown Cutoffs: A Pre-Registered Evidence Audit of 91 LLM Trading Papers](https://ssrn.com/abstract=7687481)** · [SSRN](https://ssrn.com/abstract=7687481) · [data and code](https://github.com/henryzhangpku/llm-trading-evidence-audit)
  Of 75 papers with a trading test, half deduct no costs, the median test window is 12 months, and 98% of those whose test may overlap the model's training data do not control for it.
- **[Testing the Premises Behind Popular Technical-Analysis Scripts under Pre-Registration](https://ssrn.com/abstract=7687483)** · [SSRN](https://ssrn.com/abstract=7687483)
  The shared premises behind popular drawn indicators (Fibonacci levels, regression channels, ribbons, squeezes), each tested with one frozen rule: none is supported, and every one did worse than being long in validation.
- **[The Zero-Days-to-Expiry Put-Credit Premium from Traded Option Bars: Real, Mostly Not Drift, and Priced by First-Day Shocks](https://ssrn.com/abstract=7687498)** · [SSRN](https://ssrn.com/abstract=7687498)
  Priced from traded option bars, the 0DTE SPY put-spread premium is real and mostly not market drift, but it misses the pre-registered bar because its losses come on the first day of shocks nobody forecasts.

Work in progress: [A Pre-Registered Forward Test of an LLM News Reader in Event Contracts](https://osf.io/qu983) (pre-registered on OSF).

### Autonomous Quant Researcher

An LLM proposes trading hypotheses; trusted code decides whether they are true.
My own idea: an autonomous quant researcher, a bounded research loop that
borrows the fixed experiment contract of Karpathy's `autoresearch` and the
loop-as-artifact discipline of Loop Engineering, then adds what finance forces
on you: the model never writes code (declarative JSON
hypotheses, trusted interpretation), three chronological stages with a one-use
holdout, acceptance as a gate set rather than a metric, admission-time
de-duplication, and a hash-chained ledger that keeps every refutation.

Most of what comes back is a documented no, and the ledger keeps those too — a
refutation nobody wrote down gets rediscovered, at cost, by the next person.
**Now open source**: the runner, the declarative contract, fixed validators,
the options backtest mechanics, a public pre-registration with its
hash-chained ledger, and 500+ tests that need neither network nor keys.

**[→ github.com/henryzhangpku/autonomous-quant-researcher](https://github.com/henryzhangpku/autonomous-quant-researcher)**

**Paper:** [Hard to Fool: A Bounded LLM Research Loop for Quantitative Finance, and What Two Dozen Campaigns Found](https://arxiv.org/abs/2611.06607) (arXiv:2611.06607, November 2026; also on [SSRN](https://ssrn.com/abstract=7682019), doi:10.2139/ssrn.7682019)

---

### research2prod — research to production, with no handover

The guided self-service model from my PIMCO work, rebuilt in the open. A researcher who can write working Python
still has no idea what happens after "the backtest looks good" — and the
usual answer is a quant developer rebuilding the signal from a notebook,
followed by weeks of finding out why the two disagree. `research2prod` removes the
conversion step entirely: the project template makes the research code
already be production code. One decorator, an as-of view a signal cannot
reach past, data contracts, a mechanical promotion gate (look-ahead,
determinism, declaration, contract, backtest floors), an immutable
certificate with a golden output, and `research2prod export` — a deployable bundle
with a runner, a Dockerfile and a schedule, generated without translating
anything. Every command ends by naming the next one.

**[→ github.com/henryzhangpku/research2prod](https://github.com/henryzhangpku/research2prod)**

---

### mft-engine: mid-frequency trading, reasoning signals gated by code

The systematic-trading discipline from my PIMCO work, on a modern Rust stack: an engine for mid-frequency trading, where decisions are made on minute
bars and positions last minutes to hours. The reasoning signals come from where
markets now talk: live Kalshi strike ladders turned into an implied
distribution, and public posts scored by a fast System One classifier at
about 120 ms a post. Code, not the model, decides.

One event loop runs backtest and live paper alike, so research and production
cannot disagree. Risk fails closed; replay is deterministic to the decision
fingerprint; every idea tried goes on a hash-chained experiment ledger, kept or
killed; and a test fails the build if an order path or a secret ever appears.
The engine decides in about 2 microseconds.

It reads 331 live perpetuals across five venues and where the top wallets are
positioned. Results after costs are published as they came out.

**[→ Live demo, and the code](https://henryzhangpku.github.io/mft-engine/)**

---

### Three short books on options

<table>
<tr>
<td width="33%" valign="top">
<a href="https://github.com/henryzhangpku/art-of-options-war"><img src="https://raw.githubusercontent.com/henryzhangpku/art-of-options-war/main/cover.jpg" alt="The Art of Options War" width="160"></a>
<br><br>
<b><a href="https://github.com/henryzhangpku/art-of-options-war">The Art of Options War</a></b> · 期权兵法
<br>
Sun Tzu's thirteen chapters, read against one trade: the defined-risk credit spread.
</td>
<td width="33%" valign="top">
<a href="https://github.com/henryzhangpku/options-underwriter"><img src="https://raw.githubusercontent.com/henryzhangpku/options-underwriter/main/cover.jpg" alt="The Options Underwriter" width="160"></a>
<br><br>
<b><a href="https://github.com/henryzhangpku/options-underwriter">The Options Underwriter</a></b> · 期权承保
<br>
The same trade, run as an insurance company: policy, price, reserves, claims, catastrophe.
</td>
<td width="33%" valign="top">
<a href="https://github.com/henryzhangpku/the-counted-trade"><img src="https://raw.githubusercontent.com/henryzhangpku/the-counted-trade/main/cover.jpg" alt="The Counted Trade" width="160"></a>
<br><br>
<b><a href="https://github.com/henryzhangpku/the-counted-trade">The Counted Trade</a></b> · 算而后战
<br>
The buyer's book: the Thirty-Six Stratagems, read for the buyer of asymmetric options.
</td>
</tr>
</table>

All three bilingual and free to read. No forecasts, no signals, no performance claims.

---

### Other languages

For reference, the same discipline outside Python, each with a live page: [tickforge](https://henryzhangpku.github.io/tickforge/) (C++20 tick store and parameter sweeps) · [java-bidder](https://henryzhangpku.github.io/java-bidder/) (Java 21, hard-deadline bidder) · [rails-nl-screen](https://henryzhangpku.github.io/rails-nl-screen/) (Rails 8 plain-English screen).

---

### Selected repositories

| | |
|---|---|
| **[autonomous-quant-researcher](https://github.com/henryzhangpku/autonomous-quant-researcher)** | An LLM proposes trading hypotheses, trusted code decides — staged holdouts, gate sets, and a hash-chained ledger of every refutation. Paper: [arXiv:2611.06607](https://arxiv.org/abs/2611.06607), [SSRN](https://ssrn.com/abstract=7682019) |
| **[research2prod](https://github.com/henryzhangpku/research2prod)** | Write the signal once; it is already production code — the guided bridge from quant research to a scheduled, audited job |
| **[mft-engine](https://github.com/henryzhangpku/mft-engine)** | Mid-frequency trading in Rust: Kalshi probability ladders and classifier-scored posts as signals, code as the gate, one code path for backtest and live paper, an experiment ledger |

Everything else is on [the repositories tab](https://github.com/henryzhangpku?tab=repositories).

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

[LinkedIn](https://www.linkedin.com/in/henryzhang99/) · [Substack](https://henryzhang.substack.com) · [officialhenryzhang.com](https://www.officialhenryzhang.com/) · [ORCID](https://orcid.org/0009-0000-1891-3607) · [SSRN](https://papers.ssrn.com/sol3/cf_dev/AbsByAuth.cfm?per_id=3016152) · [arXiv](https://arxiv.org/a/zhang_h_21)
