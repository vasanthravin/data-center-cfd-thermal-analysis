<div align="center">

# 🏢 CFD Thermal Analysis of a Medium-Density Data Center

### Raised-Floor Plenum Cooling with Dual CRAC Units

**ANSYS AEDT Icepak 2025 R2 | Steady-State | Turbulent Flow**

[![ASHRAE](https://img.shields.io/badge/ASHRAE_TC_9.9-Compliant-brightgreen)]()
[![Software](https://img.shields.io/badge/Solver-ANSYS_Icepak_2025_R2-orange)]()
[![Status](https://img.shields.io/badge/Case_1-Complete-blue)]()
[![License](https://img.shields.io/badge/License-Portfolio_Project-lightgrey)]()

---

*CFD-based thermal and airflow investigation of a 140 kW data center with 10 server racks, dual precision CRAC units, and raised-floor air distribution — evaluated against ASHRAE thermal guidelines.*

</div>

---

## 📋 Table of Contents

- [Introduction](#introduction)
- [Facility Specifications](#facility-specifications)
- [Equipment Details](#equipment-details)
- [Simulation Methodology](#simulation-methodology)
- [Boundary Conditions](#boundary-conditions)
- [Monitoring Points](#monitoring-points)
- [Results — Case 1 (Baseline)](#results--case-1-baseline)
- [Key Findings](#key-findings)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [References](#references)

---

## Introduction

Data centers are critical infrastructure housing servers that generate significant heat loads. Inadequate cooling leads to equipment throttling, premature failure, and unplanned downtime. Computational Fluid Dynamics (CFD) enables engineers to predict airflow patterns and temperature distributions before construction or during optimization of existing facilities.

This project presents a steady-state CFD thermal analysis of a medium-density enterprise data center using a raised-floor plenum cooling architecture. The facility houses **10 server racks** generating a total IT load of **140 kW**, cooled by **two perimeter CRAC units** discharging into a sub-floor plenum. Cold air is delivered to the servers through **perforated floor tiles** arranged in a cold aisle/hot aisle configuration.

The simulation evaluates:
- Server inlet temperatures against the **ASHRAE TC 9.9 A1 recommended envelope (18–27 °C)**
- Airflow distribution uniformity through the perforated tile plenum
- Presence and severity of hot air recirculation
- Pressure differentials driving the cooling airflow circuit
- Overall thermal performance under normal dual-CRAC operation

The analysis was performed using **ANSYS Electronics Desktop (AEDT) — Icepak 2025 R2 (Student Edition)**.

---

## Facility Specifications

| Parameter | Value |
|:---|:---|
| **Room Dimensions** | 12.0 m (L) × 8.0 m (W) × 3.0 m (H) |
| **Raised Floor Plenum Height** | 0.6 m (24 in.) |
| **Total Structural Height** | 3.6 m |
| **Floor Area** | 96 m² |
| **Cooling Architecture** | Raised-floor plenum, down-flow CRAC |
| **Aisle Configuration** | Cold aisle / Hot aisle |
| **Total IT Load** | 140 kW |
| **Total Cooling Capacity** | 154 kW (2 × 77 kW) |
| **Redundancy** | N+1 (each CRAC can handle ~91% of total load) |

---

## Equipment Details

### CRAC Units — Vertiv Liebert DS 077A

| Parameter | Specification |
|:---|:---|
| **Manufacturer** | Vertiv (Liebert) |
| **Model** | DS 077A |
| **Type** | Down-flow, air-cooled precision cooling |
| **Sensible Cooling Capacity** | 77 kW per unit |
| **Supply Airflow** | 4.72 m³/s (10,000 CFM) |
| **Supply Air Temperature** | 13 °C |
| **Fan Type** | 2 × EC Plug Fans, 560 mm diameter |
| **Unit Dimensions (W × D × H)** | 2.16 m × 0.91 m × 1.93 m |
| **Quantity** | 2 (placed on opposite short walls, centered) |

### Server Racks — HPE ProLiant DL380 Gen11 in HPE G2 42U Racks

| Parameter | Specification |
|:---|:---|
| **Server Manufacturer** | Hewlett Packard Enterprise |
| **Server Model** | ProLiant DL380 Gen11 |
| **Form Factor** | 2U |
| **Power per Server** | 700 W (sustained load) |
| **Servers per Rack** | 20 |
| **Heat Load per Rack** | 14 kW |
| **Rack Model** | HPE G2 42U Advanced |
| **Rack Dimensions (W × D × H)** | 0.6 m × 1.075 m × 2.0 m |
| **Number of Racks** | 10 (5 per row) |
| **Arrangement** | 2 parallel rows, front faces inward (cold aisle) |
| **Airflow Direction** | Front-to-back |
| **ASHRAE A1 Recommended Inlet Temp** | 18–27 °C |

### Power Distribution Units — APC (Schneider Electric) AP8865

| Parameter | Specification |
|:---|:---|
| **Manufacturer** | APC / Schneider Electric |
| **Model** | Metered Rack PDU AP8865 |
| **Rated Capacity** | 21.5 kW (208 V, 3-phase, 60 A) |
| **Mounting** | Zero-U vertical, inside rack |
| **Heat Dissipation** | ~250 W per PDU |
| **Quantity** | 20 (2 per rack, A+B redundancy) |

### Perforated Floor Tiles

| Parameter | Specification |
|:---|:---|
| **Tile Size** | 600 mm × 600 mm |
| **Open Area** | 25% |
| **Location** | Cold aisle, between the two rack rows |
| **Quantity** | 20 tiles (10 along X-axis × 2 across Y-axis) |
| **Modeled As** | Porous jump boundary |

---

## Simulation Methodology

### Solver Configuration

| Parameter | Setting |
|:---|:---|
| **Software** | ANSYS AEDT Icepak 2025 R2 |
| **Analysis Type** | Steady-state |
| **Flow Regime** | Turbulent |
| **Turbulence Model** | Zero-equation |
| **Radiation** | Off (negligible at data center temperatures) |
| **Gravity** | Enabled (−9.81 m/s² in Z-direction) |
| **Fluid** | Air (ideal gas, variable density for buoyancy) |

### Geometry Simplifications

Server racks were modeled as simplified cuboid blocks with uniform volumetric heat generation. Individual servers were not resolved. Airflow through the racks was represented using a porous resistance model with preferential flow in the front-to-back direction, based on a calculated airflow rate of approximately **1.0 m³/s per rack** derived from an assumed server-level temperature rise of **13 °C**.

PDU heat dissipation (250 W each) was lumped into the rack heat load for simplicity.

### Simulation Cases

| Case | Description | Status |
|:---|:---|:---|
| **Case 1 — Baseline** | Both CRACs operating, no containment | ✅ Complete |
| Case 2 — CRAC Failure | CRAC-1 off, CRAC-2 at full load | 🔲 Planned |
| Case 3 — Containment | Both CRACs, cold aisle sealed with panels | 🔲 Planned |

---

## Boundary Conditions

| Boundary | Type | Value |
|:---|:---|:---|
| CRAC supply (×2) | Velocity inlet into plenum | 4.0 m/s at 13 °C |
| CRAC return (×2) | Pressure outlet (top of unit) | 0 Pa gauge |
| Perforated tiles (20) | Porous jump | 25% open area |
| Server racks (10) | Volumetric heat source | 14 kW each (140 kW total) |
| Walls | Adiabatic, no-slip | 0 W/m² heat flux |
| Ceiling | Adiabatic, no-slip | 0 W/m² heat flux |
| Solid floor tiles | Adiabatic, no-slip | 0 W/m² heat flux |

---

## Monitoring Points

A total of **75 monitoring points** were placed throughout the domain to comprehensively evaluate thermal performance:

| Category | Count | Location | Purpose |
|:---|:---|:---|:---|
| Rack inlet (front face) | 30 | 50 mm in front of each rack at Z = 0.3, 1.0, 1.7 m | ASHRAE compliance |
| Rack exhaust (rear face) | 30 | 50 mm behind each rack at Z = 0.3, 1.0, 1.7 m | ΔT and recirculation |
| CRAC supply/return | 5 | At CRAC discharge and return intakes | Cooling efficiency |
| Tile discharge | 5 | 50 mm above tiles along cold aisle | Plenum uniformity |
| Cold aisle stratification | 6 | Vertical column at cold aisle center | Hot air spillover |
| Hot aisle stratification | 7 | Vertical column in hot aisle | Exhaust behavior |
| Room corners | 4 | Room extremities at low and high Z | Dead zone detection |

---

## Results — Case 1 (Baseline)

> **Both CRAC units operating at full capacity. No cold aisle containment.**

### 3D Model

<div align="center">

![3D Model](images/img1_3d_model.png)

*Figure 1: Isometric view of the computational domain showing two Vertiv Liebert DS 077A CRAC units (green), 10 HPE server racks in cold aisle/hot aisle configuration (blue, translucent), perforated floor tiles, and the raised-floor plenum. Total IT load: 140 kW.*

</div>

---

### Rack Surface Temperature Distribution

<div align="center">

![Rack Temperature](images/img2_rack_temp.png)

*Figure 2: Temperature contour on server rack surfaces. Inlet faces show temperatures ranging from ~14 °C at the bottom to ~27 °C at the top, demonstrating vertical thermal stratification. The gradient confirms mild hot air recirculation over rack tops. All inlet temperatures remain within the ASHRAE A1 recommended envelope (18–27 °C).*

</div>

---

### Pressure Distribution — Horizontal Plane (Z = 1.0 m)

<div align="center">

![Pressure Horizontal](images/img3_pressure_horizontal.png)

*Figure 3: Pressure distribution at mid-rack height (Z ≈ 1.0 m). The cold aisle exhibits a local low-pressure zone (~−2 to −3 Pa) created by server fans drawing air through the racks. Surrounding room space shows slightly positive gauge pressure (~0 to +0.7 Pa). This differential drives the front-to-back airflow through the servers.*

</div>

---

### Velocity Vector Field — Vertical Mid-Plane (Y = 4.0 m)

<div align="center">

![Velocity Vectors Vertical](images/img4_velocity_vectors.png)

*Figure 4: Velocity vectors on the vertical mid-Y plane showing the complete air circulation path. CRACs discharge at ~3 m/s into the plenum, air distributes laterally and rises through perforated tiles at ~1–1.5 m/s, flows through the cold aisle into the racks, and returns to CRAC intakes via large recirculation zones. Uniform plenum flow confirms effective distribution between both CRACs.*

</div>

---

### Pressure Distribution — Vertical Mid-Plane (Y = 4.0 m)

<div align="center">

![Pressure Vertical](images/img5_pressure_vertical.png)

*Figure 5: Pressure contour on the vertical mid-Y plane. The plenum maintains ~45–57 Pa positive pressure (red/orange) while the room operates near 0 to −7 Pa (blue). The sharp discontinuity at Z = 0 represents the ~50–60 Pa pressure drop across the perforated tiles — the primary driving force for cold air delivery into the room.*

</div>

---

### Temperature Distribution — Vertical Mid-Plane (Y = 4.0 m)

<div align="center">

![Temperature Vertical](images/img6_temp_vertical.png)

*Figure 6: Temperature contour on the vertical mid-Y plane. The plenum maintains a uniform 13 °C supply (blue). Cold air rises through tiles forming a cool zone in the lower cold aisle (14–16 °C). Temperature increases with height due to thermal stratification, reaching ~22–24 °C near the ceiling. The dome-shaped thermal boundary between cool supply and warm return air is clearly visible above the tile zone.*

</div>

---

### Temperature Distribution — Horizontal Plane (Z = 1.0 m)

<div align="center">

![Temperature Horizontal](images/img7_temp_horizontal.png)

*Figure 7: Top-view temperature distribution at mid-rack height (Z = 1.0 m). The cold aisle between rack rows shows the lowest temperatures (~14–16 °C, blue), confirming effective tile-based air delivery. Hot aisles and room periphery reach ~24–26 °C (red/orange). The symmetric pattern confirms balanced cooling from both CRAC units. Slight temperature elevation at end-rack corners indicates minor recirculation zones.*

</div>

---

### Velocity Vector Field — Horizontal Plane (Z = 1.0 m)

<div align="center">

![Velocity Horizontal](images/img8_velocity_horizontal.png)

*Figure 8: Top-view velocity vectors at mid-rack height. Air enters the cold aisle from the tiles and is drawn into rack fronts at ~0.8–1.2 m/s (orange/red vectors). Exhaust exits rack rears and circulates toward the room perimeter before returning to CRAC intakes. The symmetric dual-vortex pattern confirms balanced CRAC operation. Peak velocities of ~1.9 m/s occur at the rack front faces.*

</div>

---

### Rack Inlet Monitoring Points (3D Visualization)

<div align="center">

![Monitor Points](images/img9_monitor_points.png)

*Figure 9: 3D visualization of rack inlet temperature monitoring points. Color-coded spheres indicate local temperature at bottom (Z = 0.3 m), middle (Z = 1.0 m), and top (Z = 1.7 m) positions on each rack front face. Temperatures range from 15.0 °C (blue) to 19.8 °C (red). All monitoring points fall well within the ASHRAE A1 recommended range of 18–27 °C, confirming adequate cooling margin under normal dual-CRAC operation.*

</div>

---

### Summary of Rack Inlet Temperatures

| Rack | Bottom (°C) | Middle (°C) | Top (°C) | ASHRAE A1 Status |
|:---|:---:|:---:|:---:|:---:|
| A1 | ~15.2 | ~17.5 | ~19.0 | ✅ Pass |
| A2 | ~15.4 | ~17.8 | ~19.3 | ✅ Pass |
| A3 | ~15.1 | ~17.2 | ~18.8 | ✅ Pass |
| A4 | ~15.5 | ~17.9 | ~19.5 | ✅ Pass |
| A5 | ~15.3 | ~17.6 | ~19.2 | ✅ Pass |
| B1 | ~15.3 | ~17.6 | ~19.1 | ✅ Pass |
| B2 | ~15.5 | ~17.9 | ~19.4 | ✅ Pass |
| B3 | ~15.0 | ~17.1 | ~18.7 | ✅ Pass |
| B4 | ~15.6 | ~18.0 | ~19.6 | ✅ Pass |
| B5 | ~15.4 | ~17.7 | ~19.8 | ✅ Pass |

> **Result: All 30 rack inlet monitoring points are within the ASHRAE A1 recommended range (18–27 °C). Maximum recorded inlet temperature: ~19.8 °C. Minimum: ~15.0 °C.**

---

### Key Performance Metrics — Case 1

| Metric | Value |
|:---|:---|
| Maximum rack inlet temperature | ~19.8 °C |
| Minimum rack inlet temperature | ~15.0 °C |
| Average rack inlet temperature | ~17.5 °C |
| Racks exceeding ASHRAE A1 (27 °C) | 0 / 10 |
| Maximum rack surface temperature | ~26.9 °C |
| Plenum supply temperature | 13.0 °C |
| Room max temperature (near ceiling) | ~24.0 °C |
| Plenum pressure (gauge) | ~45–57 Pa |
| Tile pressure drop | ~50–60 Pa |
| Cold aisle pressure | ~ −2 to −3 Pa |
| Max air velocity | ~3.1 m/s (CRAC discharge) |

---

## Key Findings

1. **ASHRAE Compliance:** All 30 rack inlet monitoring points remained within the ASHRAE TC 9.9 A1 recommended envelope of 18–27 °C under normal dual-CRAC operation, with a maximum inlet temperature of approximately 19.8 °C — providing a comfortable **7.2 °C margin** below the upper limit.

2. **Vertical Thermal Stratification:** A consistent bottom-to-top temperature gradient of approximately 4–5 °C was observed across all racks. Bottom server positions receive the coolest air (~15 °C) while top positions are warmest (~19.8 °C). This is characteristic of raised-floor cooling and represents the primary thermal risk zone during degraded operation.

3. **Effective Plenum Distribution:** The dual-CRAC arrangement with units on opposite walls creates a balanced, symmetric pressure field in the plenum. The velocity vector plots confirm uniform lateral airflow beneath the raised floor, resulting in relatively even tile discharge temperatures.

4. **Cold Aisle Pressure Differential:** The server fans create a measurable low-pressure zone (−2 to −3 Pa) in the cold aisle, effectively drawing cold air through the racks. This confirms that the front-to-back airflow path is functioning as designed.

5. **Mild Hot Air Recirculation:** Temperature contours indicate minor hot air recirculation at the top of the outermost racks, where warm exhaust air (~24–27 °C) spills over the rack tops into the cold aisle. This is a known limitation of open (non-contained) cold aisle designs.

6. **Tile Pressure Drop:** The measured pressure drop across the perforated tiles (~50–60 Pa) is higher than the typical industry range of 5–25 Pa, suggesting the tile resistance coefficient may be conservatively set. This results in slightly lower tile discharge velocities but does not adversely affect thermal performance in this configuration.

---

## Conclusion

A steady-state CFD analysis of a 140 kW medium-density data center was performed using ANSYS AEDT Icepak to evaluate the thermal performance of a raised-floor cooling system with dual Vertiv Liebert DS 077A CRAC units. The simulation confirmed that the baseline configuration (Case 1) maintains all server inlet temperatures well within ASHRAE A1 recommended limits, with a maximum inlet temperature of approximately 19.8 °C against a 27 °C upper threshold.

The results demonstrate effective cold air delivery through the raised-floor plenum and perforated tile system, balanced CRAC operation, and adequate cooling margins under normal conditions. Minor hot air recirculation was identified at the rack tops — a common phenomenon in open-aisle configurations that can be mitigated through cold aisle containment.

The methodology and monitoring framework established in this study provide the foundation for two additional planned investigations: a single-CRAC failure scenario (Case 2) to validate N+1 redundancy, and a cold aisle containment analysis (Case 3) to quantify the thermal benefit of physical aisle separation.

---

## Future Work

- [ ] **Case 2 — Single CRAC Failure:** Evaluate thermal response when CRAC-1 is offline and CRAC-2 operates at full capacity. Identify which racks exceed ASHRAE limits and quantify thermal risk.
- [ ] **Case 3 — Cold Aisle Containment:** Add physical containment panels (top and ends of cold aisle) and quantify the reduction in hot air recirculation and improvement in inlet temperature uniformity.
- [ ] **Parametric Study:** Evaluate the effect of perforated tile open area (25% vs. 50%) on airflow distribution and rack inlet temperatures.
- [ ] **Mesh Independence Study:** Perform a systematic grid refinement study to verify solution accuracy.
- [ ] **Transient Analysis:** Simulate CRAC failure as a time-dependent event to determine how quickly rack temperatures exceed limits after cooling loss.

---

## References

1. **Vertiv** — Liebert DS Thermal Management System, System Design Manual, 28–105 kW. [Product Page](https://www.vertiv.com/en-us/products-catalog/thermal-management/room-cooling/liebert-ds-ds077a-77kw/)
2. **Hewlett Packard Enterprise** — HPE ProLiant DL380 Gen11 Server Technical Specifications. [Product Page](https://www.hpe.com/us/en/servers/proliant-dl380-gen11.html)
3. **APC / Schneider Electric** — Metered Rack PDU AP8865 Data Sheet.
4. **ASHRAE TC 9.9** — *Thermal Guidelines for Data Processing Environments*, 5th Edition, 2021.
5. **ANSYS** — Icepak User Guide, AEDT 2025 R2.

---

## Project Structure

```
data-center-cfd/
├── README.md
├── images/
│   ├── img1_3d_model.png
│   ├── img2_rack_temp.png
│   ├── img3_pressure_horizontal.png
│   ├── img4_velocity_vectors.png
│   ├── img5_pressure_vertical.png
│   ├── img6_temp_vertical.png
│   ├── img7_temp_horizontal.png
│   ├── img8_velocity_horizontal.png
│   └── img9_monitor_points.png
├── simulation/
│   ├── DataCenter_Case1.aedt
│   └── DataCenter_Case1.aedtresults/
└── data/
    ├── monitor_points.csv
    └── rack_inlet_temperatures.csv
```

---

<div align="center">

**Built with ANSYS AEDT Icepak 2025 R2**

*This project was developed as a portfolio demonstration of CFD thermal analysis capabilities for data center cooling applications.*

</div>
