# HOMER Pro Model Configuration

This folder contains the reproducible input parameters for the HOMER Pro model. Due to software license restrictions, the proprietary HOMER Pro project file (.hmr) cannot be redistributed.

## Files
- `HOMER_Input_Parameters.csv` – Complete list of all input parameters required to reconstruct the HOMER Pro model.
- `README.md` – This file.

## How to Use
1. Open `HOMER_Input_Parameters.csv` in Microsoft Excel or any CSV viewer.
2. Follow the `Step_by_Step_Guide.md` in `07_Reproduction_Instructions/` to enter these parameters into a new HOMER Pro project.
3. The file is organized by category: Project Settings, Load Parameters, Solar Resource, Wind Resource, PV, Wind Turbine, Battery, Converter, Diesel Generator, System Constraints, Scenarios, Baseline, and Sensitivity.

## Categories Overview
| Category | Description |
| :--- | :--- |
| Project Settings | Lifetime, discount rate, simulation time step |
| Load Parameters | Annual demand, peak load, load classification |
| Solar Resource | Irradiance, clearness index, NASA POWER data |
| Wind Resource | Wind speed, hub height, power-law scaling |
| PV | Component costs and technical specifications |
| Wind Turbine | Component costs and technical specifications |
| Battery | Component costs, SOC limits, self-discharge |
| Converter | Component costs and efficiency |
| Diesel Generator | Component costs, fuel curve, fuel price |
| System Constraints | 0% unmet load, SOC limits, capacity shortage |
| Scenarios | Scenario 1, 2, 3 definitions and key results |
| Baseline | Diesel-only system results |
| Sensitivity | One-at-a-time and scenario-based sensitivity |

## Important Note on HOMER Pro Files
Due to software license restrictions, the proprietary HOMER Pro project file (.hmr) cannot be redistributed. All necessary configuration parameters are provided in `HOMER_Input_Parameters.csv` to allow full reconstruction of the model.

## Assumptions
Any value marked as "Assumed" is based on HOMER Pro defaults or manufacturer datasheets, as the paper did not specify a numerical value. These assumptions are stated transparently to ensure reproducibility.

## Source
- Paper: "Reliability-Oriented Design and Optimization of Renewable Electrification Systems with Priority Load Management for Public Institutions in Remote Urban Regions".
- HOMER Pro v3.16 User Manual.
- Manufacturer datasheets (Canadian Solar, Eocycle, EnerSys).
- NASA POWER database.
