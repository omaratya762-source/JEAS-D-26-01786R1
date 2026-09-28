# Optimization Parameters

## 1. Optimization Objective
The primary objective is to minimize the Net Present Cost (NPC) while ensuring reliable satisfaction of prioritized loads.

- **Objective Function:** Minimize NPC
- **Project Lifetime (T):** 25 years
- **Annual Discount Rate (i):** 6%
- **Optimization Platform:** HOMER Pro v3.16
- **Simulation Time Step:** Hourly (8,760 hours/year)

## 2. Economic Model
NPC is calculated as:

\[
C_{NPC} = C_{cap} + C_{rep} + C_{O\&M} + C_f + C_{EP} - R
\]

Where:
- \(C_{cap}\): Initial capital cost
- \(C_{rep}\): Present worth of replacement costs
- \(C_{O\&M}\): Operation and maintenance costs
- \(C_f\): Fuel and emissions penalties
- \(C_{EP}\): Cost of power purchased from grid (0 for off-grid)
- \(R\): Salvage value and grid sales revenue (0 for off-grid)

LCOE is calculated as:

\[
LCOE = \frac{NPC_{total}}{\sum_{t=1}^{T} \left( \frac{E_t}{(1+i)^t} \right)}
\]

Where \(E_t\) is the total electrical energy supplied in year \(t\).

## 3. Load Parameters
| Parameter | Value | Unit |
| :--- | :--- | :--- |
| Annual Electricity Demand | 685,016 | kWh/year |
| Peak Load | 136.6 | kW |
| Critical Load Share | 28% | (191,805 kWh/year) |
| Essential Load Share | 55% | (376,759 kWh/year) |
| Non-Essential Load Share | 17% | (116,452 kWh/year) |

## 4. Renewable Resource Parameters
| Resource | Value | Unit | Source |
| :--- | :--- | :--- | :--- |
| Annual Average Solar Irradiance | 6.08 | kWh/m²/day | NASA POWER |
| Clearness Index | 0.668 | – | NASA POWER |
| Annual Mean Wind Speed | 6.26 | m/s at 50 m | NASA POWER |
| Wind Turbine Hub Height | 36 | m | Eocycle EO20 |

## 5. Component Cost Assumptions (Table 5 in Paper)
| Component | Capacity | Capital Cost | Replacement Cost | O&M Cost | Lifetime | Efficiency |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| PV (Canadian Solar) | 1 kW | 1,000 $/kW | 800 $/kW | 10 $/yr | 25 years | 16.94% |
| Wind Turbine (Eocycle EO20) | 20 kW | 8,665 $/kW | 2,599.5 $/kW | 41 $/kW/yr | 20 years | – |
| Battery (EnerSys SBS92F) | 1 kWh | 120 $/kWh | 100 $/kWh | 2 $/kW/yr | 10 years | 97% |
| Converter | 1 kW | 180 $/kW | 180 $/kW | 3 $/kW/yr | 15 years | 95% |
| Diesel Generator | 100 kW | 200 $/kW | 200 $/kW | 34.1 $/op.hr | 15,000 hours | 41% |

## 6. Scenario Definitions
| Scenario | Description | Components |
| :--- | :--- | :--- |
| Scenario 1 | PV/Battery | PV + Battery |
| Scenario 2 | PV/DG/Battery | PV + Diesel Generator + Battery |
| Scenario 3 | PV/Wind/DG/Battery | PV + Wind + Diesel Generator + Battery |
| Baseline | Diesel-Only | 2 × 100 kW Diesel Generators |

## 7. Sensitivity Analysis Parameters
- **One-at-a-time sensitivity:** PV cost, Battery cost, Wind turbine cost, Diesel fuel price varied within ±30%.
- **Scenario-based sensitivity:**
  - Optimistic: +20% renewable availability, 5% discount rate, 0.20 $/L diesel
  - Baseline: nominal values
  - Pessimistic: -20% renewable availability, 11% discount rate, 1.00 $/L diesel

## 8. Key Outputs
| Indicator | Value (Optimal Scenario 3) |
| :--- | :--- |
| Net Present Cost (NPC) | USD 1.26 million |
| Levelized Cost of Energy (LCOE) | USD 0.142/kWh |
| Renewable Fraction (RF) | 97.1% |
| Unmet Load | 0% |
| CO₂ Emissions | 14,557 kg/year |
| Excess Electricity | 17.8% |
| Diesel Consumption | 5,565 L/year |