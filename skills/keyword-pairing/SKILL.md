---
name: keyword-pairing
description: Build sourcing search pairs from a job description - Anchor Term x Pairing Term - so a search returns a small number of right profiles instead of thousands of wrong ones. Use when sourcing candidates, mapping a market, designing LinkedIn or Google searches, when a keyword search returns only big-tech generalists, or when search results keep missing the domain.
---

# keyword-pairing

Convert a JD into `Anchor x Pairing Term` pairs, one pair per JD requirement.

## Terms

- **Anchor (L0)**: the technical floor. Decides whether the person is in the field at all.
- **Pairing term, domain (L1)**: the domain discriminator. **Required in every pair.**
- **Pairing term, capability (L2)**: seniority / real-world evidence. Optional.
- **Pair**: one Anchor x one Pairing Term.

## Procedure

1. **Read the JD for the product shape.** Ask: what form does the client's product take? That is the anchor. Not "what technology does the person know".
2. **Extract candidate terms without filtering.** Every requirement line yields one.
3. **Classify** into L0 / L1 / L2. If unsure, it is L1 (domain).
4. **Predict before searching.** For each pair: how many results, and will they be right-technology-wrong-domain?
5. **Test small** — 3 to 5 pairs — and compare against the prediction.
6. **Log the pair** as searched. Never re-run a logged pair.
7. **Report four numbers**: pairs run, profiles returned, fit after screening, target-region share.

## Non-negotiable rules

1. **Two terms minimum, both must hit.** One keyword finds a crowd.
2. **No pair without an L1 domain term.** `Anchor x Anchor` returns generalists: right stack, wrong industry.
3. **One pairing term per JD line.** If you cannot cite the JD sentence, drop the term.
4. **Never mix terms across clients.** Two clients in the same space often need opposite anchors. Keep a separate matrix per role.
5. **Anchor on the product, not the person's skill list.**

## Company-anchored search

When the anchor is a company name, it already narrows. More terms make it worse.

| Size | Pairing terms |
|---|---|
| < 200 people | none |
| hundreds to thousands | 1 precise, non-generic term |
| tens of thousands | 2-3 including an L1 |

- Write the company name in both languages with OR: `("English Name" OR "native name")`. The OR combination returns more than the two searches combined.
- Do not exclude former employees. `Former X` is a legitimate and often better candidate.
- Do not use generic words (`AI`, `algorithm`, `materials`) next to a company anchor: they dissolve the anchor. Use proper nouns only (`pytorch`, `DFT`, `VASP`).
- A company funded or founded less than six months ago usually has no profiles on the network yet. Skip it or go through the founder or investor pages.

## Filters

**Explicit** (goes into the query): `site:cn.linkedin.com/in`, city names, institution names used as *history* filters.

**Judgment** (never in the query; applied after results return): nationality or citizenship, currently enrolled, professor vs industry, already contacted, actual fit.

- Location is a position, not a history. `Tsinghua` and `Google` filter where someone studied or worked, not where they are. For current location use the regional subdomain: `site:cn.linkedin.com/in`.
- Nobody writes their nationality on a profile. Apply it as a post-filter on name script, surname, region terms and institution signals — never as a search term.

## Output

```
<project>/keyword_matrix_<role>_<date>.md
  - Anchor list (1-2)
  - Pairing term list (6-8), each citing the JD line
  - Pair matrix, each row marked searched / not searched
  - Filter plan: explicit terms + judgment filters
  - Search log: pairs run, hits, fit
```

## Reporting

```
pairs run: N | returned: M | fit: K | target-region: X% | spend: Y
```

Hit count without fit count is not a result.

## Licence

MIT.
