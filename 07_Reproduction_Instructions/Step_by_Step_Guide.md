# Step-by-Step Reproduction Guide

Follow these steps to reconstruct the HOMER Pro model and reproduce the results.

## Step 1: Set Up HOMER Pro Project
1. Open HOMER Pro v3.16.
2. Create a new project.
3. Set **Project Lifetime** to 25 years.
4. Set **Annual Discount Rate** to 6%.
5. Set **Simulation Time Step** to 1 hour (8,760 hours/year).

## Step 2: Import Load Data
1. Create a new **Primary Load**.
2. Import `01_Input_Data/Load_Profile/Annual_Hourly_Load.csv`.
3. Set the load classification:
   - **Critical Loads:** 28% (191,805 kWh/year) – set unmet load constraint to 0%.
   - **Essential Loads:** 55% (376,759 kWh/year) – set unmet load constraint to 0%.
   - **Non-Essential Loads:** 17% (116,452 kWh/year) – model as deferrable load or separate lower-priority load.
4. For seasonal profiles, use `Seasonal_Load_Profiles.csv` to verify summer and winter peaks.

## Step 3: Configure Renewable Resources
1. **Solar:** Import `01_Input_Data/Solar_Resource/Solar_Data.csv`. Ensure annual average is 6.08 kWh/m²/day and clearness index is 0.668.
2. **Wind:** Import `01_Input_Data/Wind_Resource/Wind_Data.csv`. Set hub height to 36 m. HOMER will adjust wind speed using power-law scaling.
3. **Temperature:** Import NASA POWER ambient temperature data (if available) or use HOMER's default.

## Step 4: Configure Components
Use the parameters in `02_HOMER_Models/HOMER_Input_Parameters.csv`. Key values:
- **PV (Canadian Solar):** Capital $1,000/kW, Replacement $800/kW, O&M $10/yr, Lifetime 25 years.
- **Wind Turbine (Eocycle EO20):** Capital $8,665/kW, Replacement $2,599.5/kW, O&M $41/kW/yr, Lifetime 20 years.
- **Battery (EnerSys SBS92F):** Capital $120/kWh, Replacement $100/kWh, O&M $2/kW/yr, Lifetime 10 years, SOC 20-100%.
- **Converter:** Capital $180/kW, Replacement $180/kW, O&M $3/kW/yr, Lifetime 15 years.
- **Diesel Generator:** Capital $200/kW, Replacement $200/kW, O&M $34.1/op.hr, Lifetime 15,000 hours.

## Step 5: Define Scenarios
Create three scenarios as described in `05_Simulation/Scenario_Definitions.md`:
1. **Scenario 1:** PV + Battery
2. **Scenario 2:** PV + Diesel Generator + Battery
3. **Scenario 3:** PV + Wind + Diesel Generator + Battery (Optimal)

Also create a **Diesel-Only** baseline (two 100 kW generators).

## Step 6: Run Simulation
1. For each scenario, run the simulation for 8,760 hours.
2. Apply the priority-based load management strategy (see `04_Priority_Load_Management/Priority_Load_Management_Strategy.md`).
3. Ensure constraints are met: 0% unmet load for critical and essential loads, SOC 20-100%, max annual capacity shortage 0%.

## Step 7: Extract Results
1. After simulation, HOMER Pro will display the optimal configuration for each scenario.
2. Export the results:
   - **Tables:** Use `06_Results/Tables/` CSV files to verify.
   - **Figures:** Use `06_Results/Figures/` for reference. Reproduce plots using the CSV data.
3. The optimal configuration (Scenario 3) should match:
   - PV: 391 kW
   - Wind: 20 kW
   - Battery: 2,134 kWh
   - Diesel Generator: 100 kW
   - NPC: $1.26M
   - LCOE: $0.142/kWh
   - RF: 97.1%
   - CO2: 14,557 kg/year

## Step 8: Sensitivity Analysis
1. Perform one-at-a-time sensitivity: vary PV cost, battery cost, wind turbine cost, and diesel fuel price within ±30%.
2. Use the normalized sensitivity index formula in `03_Optimization/optimization_parameters/Optimization_Parameters.md`.
3. For scenario-based sensitivity, set up Optimistic, Baseline, and Pessimistic cases as per Table 10 in the paper.
4. Compare results with `06_Results/Tables/Scenario_Analysis.csv`.

## Step 9: Validate Results
1. Compare your results with the tables and figures in the paper.
2. If discrepancies exist, check input data, constraints, and component costs.
3. Refer to `Results_Mapping.md` for direct mapping between paper outputs and data files.