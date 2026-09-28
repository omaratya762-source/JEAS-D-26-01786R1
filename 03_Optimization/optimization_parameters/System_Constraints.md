# System Operation Constraints

The following constraints are enforced within the HOMER Pro optimization framework to ensure reliable and secure operation of the proposed HRES.

## 1. Power Balance Constraint
At each time step \(t\), total generation and discharge must satisfy load demand and battery charging requirements:

\[
P_{PV}(t) + P_{WT}(t) + P_{DG}(t) + P_{dis}(t) \geq P_{Load}(t) + P_{ch}(t)
\]

Where:
- \(P_{PV}(t)\): PV output power (kW)
- \(P_{WT}(t)\): Wind turbine output power (kW)
- \(P_{DG}(t)\): Diesel generator output power (kW)
- \(P_{dis}(t)\): Battery discharge power (kW)
- \(P_{Load}(t)\): Total load demand (kW)
- \(P_{ch}(t)\): Battery charging power (kW)

## 2. Critical Load Constraint
Uninterrupted supply to critical loads must be guaranteed under all operating conditions:

\[
P_{PV}(t) + P_{WT}(t) + P_{gen}(t) + P_{dis}(t) \geq P_{critical}(t)
\]

Where \(P_{critical}(t)\) represents the demand of high-priority (critical) loads.

## 3. Battery State-of-Charge (SOC) Constraint
To preserve battery health and ensure sustainable operation:

\[
SOC_{min} \leq SOC \leq SOC_{max}
\]

**Notes:**
- The paper does not explicitly state numerical SOC limits.
- In the HOMER Pro model, SOC limits were set according to the EnerSys PowerSafe SBS92F battery datasheet and HOMER Pro default settings.
- For reproducibility, the following values were used:
  - \(SOC_{min} = 20\%\)
  - \(SOC_{max} = 100\%\)
  - Self-discharge rate = 1%/day (as stated in Section 2.6.2(d))

## 4. Renewable Energy Fraction Constraint
The renewable fraction is defined as:

\[
f_{ren} = 1 - \frac{E_{nonren}}{E_{served}}
\]

Where:
- \(f_{ren}\): Fraction of renewable energy in total supply
- \(E_{nonren}\): Energy generated from non-renewable sources
- \(E_{served}\): Total electrical energy delivered to loads

## 5. Unmet Load Constraint
- **Maximum Annual Capacity Shortage:** 0%
- **Critical Load Unmet:** 0%
- This ensures that critical and essential loads are always served, and no unmet load is allowed for critical infrastructure.

## 6. Additional Design Constraints
| Constraint | Value |
| :--- | :--- |
| Project Lifetime | 25 years |
| Discount Rate | 6% |
| Maximum Annual Capacity Shortage | 0% |
| Minimum Renewable Fraction | Not explicitly constrained; optimized to 97.1% |
| Diesel Generator Operation | Only as backup; 2.24% of annual time |