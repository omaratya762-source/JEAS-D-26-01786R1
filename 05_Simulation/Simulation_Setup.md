# HOMER Pro Simulation Setup

## 1. Software and Simulation Parameters
| Parameter | Value |
| :--- | :--- |
| Software | HOMER Pro v3.16 |
| Simulation Time Step | 1 hour (8,760 hours/year) |
| Project Lifetime | 25 years |
| Annual Discount Rate | 6% |
| Dispatch Strategy | Load Following (HOMER default) |
| Maximum Annual Capacity Shortage | 0% |
| Unmet Load Constraint | 0% for Critical and Essential Loads |

## 2. Load Inputs
- Annual electricity demand: 685,016 kWh
- Peak load: 115 kW
- Load classification:
  - Critical: 28% (191,805 kWh/year)
  - Essential: 55% (376,759 kWh/year)
  - Non-Essential: 17% (116,452 kWh/year)
- Hourly load profiles: Imported from `01_Input_Data/Load_Profile/Annual_Hourly_Load.csv` (and seasonal profiles).

## 3. Renewable Resource Inputs
- Solar: NASA POWER data, annual average 6.08 kWh/m²/day, clearness index 0.668.
- Wind: NASA POWER data, annual mean 6.26 m/s at 50 m height.
- Wind turbine hub height: 36 m (adjusted using HOMER's power-law scaling).
- Temperature: NASA POWER ambient temperature data.

## 4. Component Configuration
Components are configured according to Table 5 in the paper. See `02_HOMER_Models/HOMER_Input_Parameters.csv` for detailed costs and specifications.

## 5. Constraints
- Critical load unmet: 0%
- Maximum annual capacity shortage: 0%
- Battery SOC limits: 20% – 100%
- Self-discharge rate: 1%/day

## 6. Scenarios Simulated
See `Scenario_Definitions.md`.

## 7. Sensitivity Analysis
- One-at-a-time sensitivity: PV cost, battery cost, wind turbine cost, diesel fuel price varied within ±30%.
- Scenario-based sensitivity: Optimistic, Baseline, Pessimistic (see Table 10 in paper).

## 8. Outputs
- Exported results are available in `Exported_Results/`.
- Key performance indicators: NPC, LCOE, RF, unmet load, CO₂ emissions, excess electricity.