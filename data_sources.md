# Data Sources — Factory Farming Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Factory Farming: Protein Demand Floor) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_ghg_carbon`

GHG emissions, carbon opportunity cost, land use

*Full citations: paper §4 (available SSRN).*

### `C2_water_pollution`

Water pollution, nutrient runoff, dead zones

*Full citations: paper §4 (available SSRN).*

### `C3_pandemic_amr`

Pandemic risk, antimicrobial resistance

*Full citations: paper §4 (available SSRN).*

### `C4_air_pollution`

Air pollution mortality from ammonia, particulates

*Full citations: paper §4 (available SSRN).*

### `C5_animal_welfare`

Animal welfare destruction (AQALY shadow pricing)

*Full citations: paper §4 (available SSRN).*

### `C6_governance`

Subsidy distortion, regulatory capture, ag-gag laws

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $67.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Factory Farming (Protein Demand Floor)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
