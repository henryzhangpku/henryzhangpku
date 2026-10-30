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

**Start here**, each with a live page you can try in the browser:
[equity-scout](https://henryzhangpku.github.io/equity-scout/) (a plain-English idea becomes a checked stock screen) ·
[mft-engine](https://henryzhangpku.github.io/mft-engine/) (Rust trading engine, one code path for backtest and live) ·
[autonomous-quant-researcher](https://henryzhangpku.github.io/autonomous-quant-researcher/) (an LLM proposes, code decides)

### mft-engine: mid-frequency trading, reasoning signals gated by code

A Rust engine for mid-frequency trading, where decisions are made on minute
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

### equity-scout: a plain-English idea, screened and explained with citations

Write an investment observation the way a trader would say it — *profitable
mid-caps that have pulled back 20% from their highs but are still growing
revenue* — and a model turns it into a typed screen spec. Code checks every
field, operator and threshold against a whitelist and refuses the rest, then
screens about 3,800 US-listed companies on point-in-time data and computes every
number. For the top names the model reads the latest earnings release, the
MD&A and the news, and explains why the stock and the fundamentals might
disagree; code deletes any claim whose quote does not appear verbatim in its
source.

The same rule as everything else here: the model proposes, deterministic code
decides. The browser demo re-runs the screen on a recorded snapshot with no
key, and the learning loop's hypotheses are shown with their excess after
costs, the corrected bar, and the decision.

**[→ Live demo, and the code](https://henryzhangpku.github.io/equity-scout/)**

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

### research2prod — research to production, with no handover

The other half of the problem. A researcher who can write working Python
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
| **[mft-engine](https://github.com/henryzhangpku/mft-engine)** | Mid-frequency trading in Rust: Kalshi probability ladders and classifier-scored posts as signals, code as the gate, one code path for backtest and live paper, an experiment ledger |
| **[research2prod](https://github.com/henryzhangpku/research2prod)** | Write the signal once; it is already production code — the guided bridge from quant research to a scheduled, audited job |
| **[autonomous-quant-researcher](https://github.com/henryzhangpku/autonomous-quant-researcher)** | An LLM proposes trading hypotheses, trusted code decides — staged holdouts, gate sets, and a hash-chained ledger of every refutation |
| **[equity-scout](https://github.com/henryzhangpku/equity-scout)** | A plain-English observation becomes a whitelisted screen over ~3,800 US equities, with explanations whose every quote is checked verbatim |

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

[LinkedIn](https://www.linkedin.com/in/henryzhang99/) · [officialhenryzhang.com](https://www.officialhenryzhang.com/)
