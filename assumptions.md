# Monte Carlo Assumptions — Factory Farming / Protein Demand Floor

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $67.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 41.25 | Confirmed by N=100,000 draws |
| ΔW median (result) | $2,763.7B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_ghg_carbon` | lognormal | $500B | $800B | $1,200B | GHG emissions, carbon opportunity cost, land use |
| `C2_water_pollution` | lognormal | $250B | $420B | $650B | Water pollution, nutrient runoff, dead zones |
| `C3_pandemic_amr` | lognormal | $300B | $550B | $900B | Pandemic risk, antimicrobial resistance |
| `C4_air_pollution` | lognormal | $200B | $350B | $550B | Air pollution mortality from ammonia, particulates |
| `C5_animal_welfare` | lognormal | $212B | $530B | $850B | Animal welfare destruction (AQALY shadow pricing) |
| `C6_governance` | lognormal | $38B | $60B | $85B | Subsidy distortion, regulatory capture, ag-gag laws |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 5.0 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 5.0) = 0.0000%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 40.45 | 20% DC adj = 32.36 | 40% DC adj = 24.27

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $2,764B = 2.6% of world GDP ($106T) ✓
- **β_W range**: 41.25 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
