# Optimization Algorithm and Workflow

## 1. Optimization Platform
- **Software:** HOMER Pro v3.16
- **Method:** Exhaustive search over all feasible component size combinations
- **Simulation:** Hourly (8,760 hours/year) for each candidate configuration

## 2. Optimization Workflow (Figure 4 in Paper)
The optimization process follows five phases:

### Phase 1: Problem Definition and Data Collection
- Define technical, economic, and environmental inputs.
- Inputs include:
  - Annual load: 685,016 kWh
  - Peak demand: 136.6 kW
  - Renewable resource profiles (NASA POWER)
  - Component costs and sensitivity ranges
  - Critical design requirement: uninterrupted supply to critical loads

### Phase 2: Proposed Design Scenarios
Three scenarios are developed:
1. PV + Battery
2. PV + Diesel Generator + Battery
3. PV + Wind + Diesel Generator + Battery

### Phase 3: Selection Criteria
For each configuration:
1. Simulate 8,760 hours
2. Apply priority-based load management (Critical > Essential > Non-Essential)
3. Calculate NPC and LCOE
4. Check all operational constraints

### Phase 4: Keep Solution and Select Optimal Configuration
- All feasible configurations meeting constraints are retained.
- Configurations are ranked in ascending NPC order.
- The least-cost solution is identified as the optimal configuration.

### Phase 5: Optimal System Validation
- Sensitivity analysis on key parameters
- Comparison with diesel-only system
- Environmental assessment

## 3. Pseudo-Code for HOMER Pro Optimization
```pseudo
FOR each scenario IN [Scenario 1, Scenario 2, Scenario 3]:
    FOR each combination of component sizes:
        Simulate 8760 hours
        Apply priority-based load management
        IF constraints are satisfied:
            Calculate NPC, LCOE, RF, Unmet Load, CO2
            Store configuration and results
    END FOR
END FOR

Select configuration with minimum NPC among all feasible solutions
```

## 4. Priority-Based Load Management Strategy
- **Critical Loads (28%):** Uninterruptible, 24/7 operation. Supplied by batteries and backup generator.
- **Essential Loads (55%):** Scheduled daily operation (16 hrs). Supplied by hybrid system with priority.
- **Non-Essential Loads (17%):** Flexible, sheddable load based on resource availability.

## 5. Sensitivity Analysis Methodology
- **One-at-a-time parametric sensitivity:** Vary PV, battery, wind turbine costs, and diesel fuel price within ±30%.
- **Normalized sensitivity index:**
  \[
  SI_x = \frac{\partial LCOE}{\partial x} \cdot \frac{x_0}{LCOE_0}
  \]
- **Scenario-based sensitivity:**
  - Optimistic, Baseline, Pessimistic scenarios (see Section 3.8 and Table 10 in paper).

## 6. Key Results from Optimization
| Parameter | Value |
| :--- | :--- |
| Optimal Configuration | Scenario 3 (PV/Wind/DG/Battery) |
| PV Capacity | 391 kW |
| Wind Capacity | 20 kW |
| Battery Storage | 2,134 kWh |
| Diesel Generator | 100 kW |
| NPC | USD 1.26 million |
| LCOE | USD 0.142/kWh |
| RF | 97.1% |
| CO₂ Emissions | 14,557 kg/year |