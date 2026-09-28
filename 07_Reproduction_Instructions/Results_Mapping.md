# Results Mapping

This document maps each table and figure in the paper to the corresponding data file and HOMER Pro output.

## Tables
| Table in Paper | Description | Data File in Repository |
| :--- | :--- | :--- |
| Table 1 | Comparative benchmarking of HRES studies | Not provided (literature review) |
| Table 2 | Electrical load classification | `01_Input_Data/Load_Profile/Load_Classification.csv` |
| Table 3 | Priority-based load classification framework | `04_Priority_Load_Management/Priority_Load_Management_Strategy.md` |
| Table 4 | Monthly renewable resource data | `01_Input_Data/Solar_Resource/Solar_Data.csv`, `Wind_Resource/Wind_Data.csv` |
| Table 5 | Component cost assumptions | `02_HOMER_Models/HOMER_Input_Parameters.csv` |
| Table 6 | Technical specifications and annual performance | `06_Results/Tables/Table6_Optimal_System_Annual_Performance.csv` |
| Table 7 | Economic comparison of scenarios | `06_Results/Tables/Table7_Economic_Comparison.csv` |
| Table 8 | Technical and environmental comparison | `06_Results/Tables/Table8_Technical_Environmental_Comparison.csv` |
| Table 9 | Diesel vs. hybrid comparison | `06_Results/Tables/Table9_Diesel_vs_Hybrid_Comparison.csv` |
| Table 10 | Scenario-based sensitivity analysis | `06_Results/Tables/Scenario_Analysis.csv` |

## Figures
| Figure in Paper | Description | Data File / Image File |
| :--- | :--- | :--- |
| Figure 1 | Location map | `01_Input_Data/Figure1_Location_Map.png` |
| Figure 2 | Daily load profiles | `01_Input_Data/Load_Profile/Figure2_Daily_Load_Profiles.png` |
| Figure 3 | System architecture | `02_HOMER_Models/Figure3_System_Architecture.png` |
| Figure 4 | Optimization workflow | `03_Optimization/algorithms/Figure4_Optimization_Workflow.png` |
| Figure 5 | Sankey diagram | `06_Results/Figures/Figure5_Sankey_Diagram.png` (data: `06_Results/Tables/Sankey_Diagram_Data.csv`) |
| Figure 6 | NPC distribution | `06_Results/Figures/Figure6_NPC_Distribution.png` (data: `06_Results/Tables/NPC_Distribution.csv`) |
| Figure 7 | Sensitivity of LCOE and NPC | `06_Results/Figures/Figure7_Sensitivity_LCOE_NPC.png` (data: `06_Results/Tables/Sensitivity_Analysis.csv`) |
| Figure 8 | Economic performance | `06_Results/Figures/Figure8_Economic_Performance.png` (data: `06_Results/Tables/Figure8_Economic_Performance.csv`) |
| Figure 9 | Environmental performance | `06_Results/Figures/Figure9_Environmental_Performance.png` (data: `06_Results/Tables/Figure9_Environmental_Performance.csv`) |

## How to Reproduce Figures
- Use the CSV files in `06_Results/Tables/` to re-plot the figures.
- For Sankey diagram, use `Sankey_Diagram_Data.csv` and any Sankey plotting tool (e.g., Plotly, Power BI).
- For sensitivity tornado charts, use `Sensitivity_Analysis.csv`.
- For bar charts (Figures 8 and 9), use `Figure8_Economic_Performance.csv` and `Figure9_Environmental_Performance.csv`.