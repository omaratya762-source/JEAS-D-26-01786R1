
---

## 4. Input Data

All input datasets are provided in the `01_Input_Data/` folder:

| Dataset | File | Source |
| :--- | :--- | :--- |
| Annual hourly load profile | `Load_Profile/Annual_Hourly_Load.csv` | Engineering estimates (685,016 kWh/year, peak 136.6 kW) |
| Load classification | `Load_Profile/Load_Classification.csv` | NHS HTM 06-01, ASHRAE, Rosales-Asensio et al. (2024) |
| Seasonal load profiles | `Load_Profile/Seasonal_Load_Profiles.csv` | Summer and winter hourly profiles |
| Solar resource data | `Solar_Resource/Solar_Data.csv` | NASA POWER (6.08 kWh/m²/day, clearness index 0.668) |
| Wind resource data | `Wind_Resource/Wind_Data.csv` | NASA POWER (6.26 m/s at 50 m height) |

---

## 5. Model Assumptions

Key assumptions are documented in `02_HOMER_Models/HOMER_Input_Parameters.csv` and `03_Optimization/optimization_parameters/`:

### 5.1 Project Settings
- Project lifetime: 25 years
- Annual discount rate: 6%
- Simulation time step: 1 hour (8,760 hours/year)

### 5.2 Load Classification
- Critical loads: 28% (191,805 kWh/year) – 24/7 operation, zero unmet load
- Essential loads: 55% (376,759 kWh/year) – 16 hrs/day scheduled
- Non-Essential loads: 17% (116,452 kWh/year) – sheddable/deferrable

### 5.3 Component Costs and Specifications (Table 5 in Paper)
| Component | Capital Cost | Replacement Cost | O&M Cost | Lifetime |
| :--- | :--- | :--- | :--- | :--- |
| PV (Canadian Solar) | 1,000 $/kW | 800 $/kW | 10 $/yr | 25 years |
| Wind Turbine (Eocycle EO20) | 8,665 $/kW | 2,599.5 $/kW | 41 $/kW/yr | 20 years |
| Battery (EnerSys SBS92F) | 120 $/kWh | 100 $/kWh | 2 $/kW/yr | 10 years |
| Converter | 180 $/kW | 180 $/kW | 3 $/kW/yr | 15 years |
| Diesel Generator | 200 $/kW | 200 $/kW | 34.1 $/op.hr | 15,000 hours |

### 5.4 System Constraints
- Maximum annual capacity shortage: 0%
- Unmet load for critical and essential loads: 0%
- Battery SOC limits: 20% – 100%
- Self-discharge rate: 1%/day

---

## 6. How to Run the Simulations

To reproduce the simulations, follow these steps:

1. **Set up HOMER Pro project:**
   - Open HOMER Pro v3.16.
   - Create a new project with 25-year lifetime and 6% discount rate.

2. **Import load data:**
   - Import `01_Input_Data/Load_Profile/Annual_Hourly_Load.csv`.
   - Apply priority-based load classification (see `04_Priority_Load_Management/`).

3. **Configure renewable resources:**
   - Import solar and wind data from `01_Input_Data/`.
   - Set wind turbine hub height to 36 m.

4. **Configure components:**
   - Use parameters in `02_HOMER_Models/HOMER_Input_Parameters.csv`.

5. **Define scenarios:**
   - Scenario 1: PV + Battery
   - Scenario 2: PV + DG + Battery
   - Scenario 3: PV + Wind + DG + Battery (Optimal)

6. **Run optimization:**
   - Run HOMER Pro for 8,760 hours.
   - Apply priority-based load management.

7. **Extract results:**
   - Compare with exported results in `06_Results/Tables/`.

**Detailed step-by-step instructions:** See `07_Reproduction_Instructions/Step_by_Step_Guide.md`.

---

## 7. How to Reproduce Reported Tables and Figures

All tables and figures in the paper are mapped to specific data files in `07_Reproduction_Instructions/Results_Mapping.md`. A summary is provided below:

| Table/Figure | Description | Data File |
| :--- | :--- | :--- |
| Table 2 | Load classification | `01_Input_Data/Load_Profile/Load_Classification.csv` |
| Table 4 | Monthly renewable resource data | `01_Input_Data/Solar_Resource/`, `Wind_Resource/` |
| Table 5 | Component costs | `02_HOMER_Models/HOMER_Input_Parameters.csv` |
| Table 6 | Optimal system annual performance | `06_Results/Tables/Table6_Optimal_System_Annual_Performance.csv` |
| Table 7 | Economic comparison | `06_Results/Tables/Table7_Economic_Comparison.csv` |
| Table 8 | Technical and environmental comparison | `06_Results/Tables/Table8_Technical_Environmental_Comparison.csv` |
| Table 9 | Diesel vs. hybrid comparison | `06_Results/Tables/Table9_Diesel_vs_Hybrid_Comparison.csv` |
| Table 10 | Scenario-based sensitivity | `06_Results/Tables/Scenario_Analysis.csv` |
| Figure 5 | Sankey diagram | `06_Results/Tables/Sankey_Diagram_Data.csv` |
| Figure 6 | NPC distribution | `06_Results/Tables/NPC_Distribution.csv` |
| Figure 7 | Sensitivity analysis | `06_Results/Tables/Sensitivity_Analysis.csv` |
| Figure 8 | Economic performance | `06_Results/Tables/Figure8_Economic_Performance.csv` |
| Figure 9 | Environmental performance | `06_Results/Tables/Figure9_Environmental_Performance.csv` |

---

## 8. Important Note on HOMER Pro Files (License Restriction)

Due to software license restrictions, the proprietary HOMER Pro project file (`.hmr`) **cannot be redistributed** in this repository. Uploading such files without checking the software license terms is strictly prohibited.

**Instead, we provide:**
- All reproducible input parameters (`02_HOMER_Models/HOMER_Input_Parameters.csv`)
- Configuration information (`03_Optimization/`, `05_Simulation/`)
- Exported results (`06_Results/`)
- Detailed step-by-step instructions (`07_Reproduction_Instructions/`)

This limitation is stated transparently in this repository and in the response letter to the editor. Users can fully reconstruct the HOMER Pro model using the provided parameters and instructions without needing the original `.hmr` file.

---

## 9. Key Results (Optimal Scenario 3)

| Indicator | Value |
| :--- | :--- |
| PV Capacity | 391 kW |
| Wind Capacity | 20 kW |
| Battery Storage | 2,134 kWh |
| Diesel Generator | 100 kW |
| Net Present Cost (NPC) | USD 1.26 million |
| Levelized Cost of Energy (LCOE) | USD 0.142/kWh |
| Renewable Fraction (RF) | 97.1% |
| Unmet Load | 0% |
| CO₂ Emissions | 14,557 kg/year |

---

## 10. Citation

If you use this repository, please cite:

> Hamed, O. A., Abdelhameed, E. H., & Mahmoud, A. A. (2026). Reliability-Oriented Design and Optimization of Renewable Electrification Systems with Priority Load Management for Public Institutions in Remote Urban Regions. *Journal of Engineering and Applied Science (JEAS)*.

---

---

## 11. Contact

For questions regarding the data or reproduction, please contact:

- **Omar Attia Hamed** – Sohag University, Egypt
  - Email: omaratya762@gmail.com
- **Esam H. Abdelhameed** (Corresponding Author) – Aswan University, Egypt
  - Email: ehhameed@energy.aswu.edu.eg
