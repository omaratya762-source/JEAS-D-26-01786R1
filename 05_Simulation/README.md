# Simulation Setup and Results

This folder contains the simulation configuration and exported results for the HOMER Pro model used in the study.

## Overview
The simulation was performed using HOMER Pro v3.16 with an hourly time step (8,760 hours/year). Three scenarios were simulated and compared:
1. PV + Battery
2. PV + Diesel Generator + Battery
3. PV + Wind + Diesel Generator + Battery (Optimal)

A diesel-only baseline was also simulated for comparison.

## Files
- `Simulation_Setup.md` – Detailed HOMER Pro simulation settings.
- `Scenario_Definitions.md` – Description of each simulated scenario.
- `HOMER_Configuration_Summary.csv` – Summary of key HOMER configuration parameters.
- `Exported_Results/` – Exported results from HOMER Pro.
  - `Optimal_System_Annual_Performance.csv` – Annual performance of the optimal system (Scenario 3).
  - `Scenario_Comparison_Summary.csv` – Comparison of all scenarios (economic, technical, environmental).

## Important Note on HOMER Pro Files
Due to software license restrictions, the proprietary HOMER Pro project file (.hmr) cannot be redistributed. All necessary configuration parameters and exported results are provided in this folder to allow full reconstruction of the simulation.

## Source
All data is extracted from the paper: "Reliability-Oriented Design and Optimization of Renewable Electrification Systems with Priority Load Management for Public Institutions in Remote Urban Regions".
