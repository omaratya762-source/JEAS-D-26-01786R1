# Reproduction Instructions

This folder provides detailed instructions to reproduce the results presented in the paper.

## Overview
The proposed framework uses HOMER Pro v3.16 for techno-economic optimization of a hybrid renewable energy system (HRES) for an integrated healthcare and educational complex in New Sohag City, Egypt. The system integrates PV, wind, battery storage, and a diesel generator, with a priority-based load management strategy.

## Software Requirements
- **HOMER Pro v3.16** (or later compatible version)
- **Microsoft Excel** or any CSV viewer for input data
- **NASA POWER Database** (for climatic data)
- **Python or MATLAB** (optional, for post-processing and plotting)

## Input Data
All input data are provided in the `01_Input_Data` folder:
- `Load_Profile/Annual_Hourly_Load.csv` – Annual hourly load profile (685,016 kWh/year, peak 136.6 kW)
- `Load_Profile/Load_Classification.csv` – Load classification (Critical, Essential, Non-Essential)
- `Load_Profile/Seasonal_Load_Profiles.csv` – Seasonal load profiles (winter/summer)
- `Solar_Resource/Solar_Data.csv` – NASA POWER solar irradiance data (6.08 kWh/m²/day)
- `Wind_Resource/Wind_Data.csv` – NASA POWER wind speed data (6.26 m/s at 50 m)

## Model Assumptions
Key assumptions are documented in `02_HOMER_Models/HOMER_Input_Parameters.csv` and `03_Optimization/optimization_parameters/Optimization_Parameters.md`:
- Project lifetime: 25 years
- Discount rate: 6%
- Component costs and specifications (Table 5 in paper)
- Battery SOC limits: 20% – 100%
- Maximum annual capacity shortage: 0%
- Unmet load for critical and essential loads: 0%

## How to Reproduce
1. Follow the step-by-step guide in `Step_by_Step_Guide.md`.
2. Use the mapping in `Results_Mapping.md` to locate each table and figure.
3. For any issues, refer to `License_Note.md` regarding HOMER Pro file restrictions.

## Important Note on HOMER Pro Files
Due to software license restrictions, the proprietary HOMER Pro project file (.hmr) cannot be redistributed. Instead, we provide all reproducible input parameters, configuration information, and exported results necessary to reconstruct the model.