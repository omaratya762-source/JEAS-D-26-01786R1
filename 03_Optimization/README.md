# Optimization Framework

This folder contains the optimization parameters, system constraints, and algorithm workflow for the HOMER Pro model.

## Structure
- `optimization_parameters/`
  - `Optimization_Parameters.md` – Objective function, economic model, component costs, scenarios, and sensitivity analysis.
  - `System_Constraints.md` – Power balance, critical load, SOC, renewable fraction, and unmet load constraints.
- `algorithms/`
  - `Optimization_Algorithm.md` – HOMER Pro optimization workflow (5 phases), pseudo-code, and priority-based load management.
  - `Figure4_Optimization_Workflow.png` – Flowchart of the optimization process.

## Software
- HOMER Pro v3.16
- Method: Exhaustive search over all feasible component size combinations
- Simulation: Hourly (8,760 hours/year)

## Key Parameters
- Project lifetime: 25 years
- Discount rate: 6%
- Objective: Minimize NPC while ensuring 0% unmet load for critical and essential loads.

## Source
All data extracted from the paper: "Reliability-Oriented Design and Optimization of Renewable Electrification Systems with Priority Load Management for Public Institutions in Remote Urban Regions".
