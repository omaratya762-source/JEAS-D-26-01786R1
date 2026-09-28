# Priority-Based Load Management Strategy

## 1. Load Classification
The electrical demand is classified into three tiers based on operational priority and reliability requirements:

| Load Type | Annual Energy (kWh) | Share | Operating Schedule | Power Source |
| :--- | :--- | :--- | :--- | :--- |
| Critical | 191,805 | 28% | 24/7 (Continuous) | Batteries / Backup Generator |
| Essential | 376,759 | 55% | 06:00–22:00 (16 h) | Main Hybrid System / Batteries |
| Non-Essential | 116,452 | 17% | Intermittent (8–12 h) | Hybrid (Sheddable) |

## 2. Management Strategy
- **Critical Loads:** Must be supplied at all times. The system design ensures zero unmet load for critical loads through battery storage and backup diesel generator.
- **Essential Loads:** Supplied by the hybrid system with priority. If renewable generation is insufficient, batteries and then the diesel generator supply these loads.
- **Non-Essential Loads:** Treated as flexible, sheddable demand. They are deferred or curtailed during periods of generation shortfall or low battery state-of-charge.

## 3. Implementation in HOMER Pro
The priority-based load management is implemented by:
1. Defining the critical and essential loads as primary loads with a **0% unmet load constraint**.
2. Defining the non-essential loads as a **deferrable load** or as a separate load with lower priority.
3. Using HOMER Pro's dispatch strategy to prioritize the primary loads and supply the deferrable load only when surplus energy is available.
4. The system sizing is driven by the requirement to meet critical and essential loads reliably.

## 4. Supporting Standards
- NHS HTM 06-01 (Electrical safety and life-critical medical loads)
- NFPA 110 (Emergency and standby power systems)
- IEEE Std 446 (Recommended practice for emergency and standby power)
- IEC 60364-8-1 (Energy efficiency)
- Rosales-Asensio et al. (2024) – Resilience-oriented load classification framework

## 5. Data Files
- `Load_Classification_Summary.csv`
- `Winter_Hourly_Load_Profile.csv`
- `Summer_Hourly_Load_Profile.csv`

These files provide the hourly demand profiles for each load category, which are used as input to the HOMER Pro optimization.