# SAPM Monte Carlo — Factory Farming / Protein Demand Floor

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Factory Farming (Protein Demand Floor).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **41.25** |
| β_W mean | 41.94 |
| β_W std | 7.68 |
| **90% CI** | **[30.7, 55.6]** |
| 99% CI | [27.1, 63.0] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$2,763.7B/yr** |
| Π (revenue) | $67.0B/yr |

**β_W = 41.25** means the factory farming industry destroys **$41.25 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 1 — Impossibility

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-factory-farming.git
cd sapm-mc-factory-farming
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 41.25` and `ΔW median : $2,763.7B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_ghg_carbon | $798.9B | [$531.8B, $1,198.2B] | Lognormal |
| C2_water_pollution | $419.7B | [$271.0B, $652.1B] | Lognormal |
| C3_pandemic_amr | $549.7B | [$336.2B, $899.4B] | Lognormal |
| C4_air_pollution | $350.3B | [$222.4B, $549.3B] | Lognormal |
| C5_animal_welfare | $529.0B | [$331.0B, $846.9B] | Lognormal |
| C6_governance | $60.0B | [$42.4B, $85.0B] | Lognormal |
| **Total ΔW** | **$2,763.7B** | **[$2,053.9B, $3,728.5B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 5.0 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0000%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Factory Farming (Protein Demand Floor)*.
> GitHub: epostnieks/sapm-mc-factory-farming.
> https://github.com/epostnieks/sapm-mc-factory-farming
