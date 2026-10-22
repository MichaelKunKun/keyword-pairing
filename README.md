# keyword-pairing

**Turn a job description into search pairs that return 20 right people instead of 2,000 wrong ones.**

The method: extract an **Anchor Term** and **Pairing Terms** from a JD, multiply them into pairs, and treat every pair as one requirement from the JD. One keyword finds a crowd. Two keywords find a market.

> Method notes from a retained search desk: 10 years, energy & commodities, financial data, now AI for Science and deep tech in China.

---

## The core idea

| Term | What it is | Example |
|---|---|---|
| **Anchor** | The technical floor — decides whether a person is in the field at all | `jax`, `pytorch`, `agentic workflow` |
| **Pairing term** | The discriminator — decides whether they fit *this* role | `dft`, `crystal`, `materials` |
| **Pair** | Anchor × Pairing Term | `jax × dft` |

**The anchor decides which crowd you fish in. The pairing term decides whether the fish is the right species.**

## Five rules

### 1. Never a single keyword

`"jax"` returns every ML engineer on earth. `"jax" "dft" "phd"` returns the dozen people who matter. Two terms minimum, both must hit.

### 2. The anchor is your product's shape, not a technology

Ask one question: **what form does the client's product take?** That is the anchor.

| Client | Wrong anchor | Right anchor | Why |
|---|---|---|---|
| Materials foundation-model startup | `LLM` | `jax` / `pytorch` × `dft` | The product is a materials model, not a chatbot |
| Scientific-agent product | `AI for Science` | `agentic workflow` × `AI for science` | The product is an agent; AI4S is the domain filter |
| Wrong-anchor result | 88% overseas, or 73% no domain fit | — | Wrong crowd, not wrong query syntax |

### 3. Multi-layer pairing

| Layer | Name | Job | Required |
|---|---|---|---|
| L0 | Anchor | in the field at all | yes, 1-2 |
| L1 | Domain | in *our* field | yes, at least 1 |
| L2 | Capability | senior/real enough | optional |

`Anchor × Anchor` (two technologies) gives a generic crowd: technically right, domain wrong. **Every pair needs an L1 domain term.**

### 4. One pairing term per JD requirement

Each term must point back to a sentence in the JD. If you cannot cite the sentence, the term is decoration and will only add noise.

### 5. Log every pair you have run

By round three you will re-run round one. Keep a matrix file with `searched / not searched` per pair.

## Company-anchored search is a different rule set

When the anchor is a **company name**, it already does the narrowing. Adding terms makes results *worse*.

| Company size | Pairing terms | Reason |
|---|---|---|
| < 200 people | **none** | Everyone at the company is already the whole list |
| few hundred to few thousand | 1 precise term (`pytorch`, `DFT`) | Enough to separate roles |
| tens of thousands | 2-3 terms including a domain term | Otherwise you get 10,000 people |

Measured on one 40-person startup: company name alone returned 4 correct people. Company name + a common word returned 7, all wrong (an accountant, a sales manager, a journal editor). **Adding a generic word destroys the anchor.**

Two more rules for company anchors:

- Write the name in **both languages with OR**: `("TSMC" OR "台积电")` (illustration only — substitute your target). Measured on one company: English-only 2 hits, Chinese-only 4, OR-combined 9. The OR beats the sum.
- **Do not exclude former employers.** People write `Former X`, and the former employee is often the better candidate.

## Filters: two kinds, never mixed

| Kind | Goes into the query? | Examples |
|---|---|---|
| **Explicit** | yes | `site:cn.linkedin.com/in`, `Beijing`, `Hangzhou`, `Tsinghua` |
| **Judgment** | **never** | nationality/citizenship, currently-enrolled student, professor vs industry, already contacted, actual fit |

Nobody writes "I am Chinese" on a profile. A judgment filter is applied *after* the results come back, by you or by a script — not by the search engine.

### The location trap

School and company names describe where someone **studied or worked**, not where they **are**.

| Anchor | What it actually filters |
|---|---|
| `Tsinghua` | people who studied at Tsinghua — including those who moved abroad |
| `Google` | people who worked at Google — including those who left |
| `site:cn.linkedin.com/in` | people **currently located in mainland China** — the only reliable location filter |

Measured cost of getting this wrong: three rounds of mostly overseas candidates who would not relocate.

## Workflow

```
1. Read the JD. Identify the product shape -> anchor (1-2 terms)
2. Read each requirement -> one pairing term each (6-8 terms)
3. Classify: L0 anchor / L1 domain / L2 capability
4. Predict before searching: how many hits? will it be right-but-wrong-domain?
5. Test 3-5 pairs small, compare with the prediction
6. Log searched pairs, then scale
```

Step 4 is the cheapest step in the process and the one most often skipped.

## Prediction table (run this before spending anything)

| Prediction | Action |
|---|---|
| large and accurate | run |
| large, not accurate | do not run — add an L1 domain term |
| small but accurate | run — narrow and right beats broad and wrong |
| small and inaccurate | change the terms |

## Reporting

Every round reports four numbers, not one:

```
pairs run: 14 | profiles returned: 61 | fit after screening: 9 | mainland share: 78%
```

A hit count without a fit count is not a result.

## Licence

MIT.
