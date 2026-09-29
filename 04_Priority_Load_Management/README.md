# Priority-Based Load Management

This folder contains the data and documentation for the priority-based load management strategy implemented in the proposed HRES.

## Overview
The electrical load of the integrated healthcare and educational complex is classified into three priority tiers:
1. **Critical Loads (28%)** – Uninterruptible, 24/7 operation (life-support equipment, emergency lighting, medical refrigerators, oxygen systems).
2. **Essential Loads (55%)** – Scheduled daily operation (classroom lighting, computers, ventilation, water pumps, administration).
3. **Non-Essential Loads (17%)** – Flexible, sheddable loads (air conditioning, elevators, recreational facilities, decorative lighting).

The strategy ensures that critical loads are always supplied, essential loads are prioritized, and non-essential loads are shed during periods of generation shortfall.

## Files
- `Load_Classification_Summary.csv` – Annual energy and percentage share for each load category.
- `Winter_Hourly_Load_Profile.csv` – Hourly load profile for winter season (Jan/Feb/Dec).
- `Summer_Hourly_Load_Profile.csv` – Hourly load profile for summer season (Jun/Jul/Aug).
- `Priority_Load_Management_Strategy.md` – Detailed description of the management strategy and its implementation in HOMER Pro.

## Source
All data is extracted from the paper: "Reliability-Oriented Design and Optimization of Renewable Electrification Systems with Priority Load Management for Public Institutions in Remote Urban Regions".
