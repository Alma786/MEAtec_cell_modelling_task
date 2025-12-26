# MEAtec Task

## Cell modelling Project: Electrochemical Parameter & OCV Optimization Framework

---

## Project Overview
This project presents a systematic electrochemical model calibration framework developed using **PyBaMM** for lithium-ion batteries. The primary objective is to accurately match experimental capacity (Ah), voltage response, and overpotentials through sequential optimization of geometric, material, and electrochemical parameters.

A key focus of this work is the selection and optimization of **Half-Cell Open Circuit Voltages (HOCVs)** sourced from the **liiondb database**. The calibrated model is progressively validated, starting from stable (1C) discharge data and extending to dynamic operating conditions using **HPPC** and **WLTP drive cycle data (95k km, cycle-0)**.

---

## Core Objectives
- Match cell capacity (Ah) by optimizing geometric parameters
- Select and optimize HOCVs from liiondb to accurately reproduce:
  - Upper cut-off voltage  
  - Experimental voltage profile
- Perform joint optimization of:
  - Geometry parameters  
  - Selected HOCVs
- Study the sensitivity, bounds, and physical impact of varying:
  - Geometric parameters  
  - Reaction and diffusion-related parameters
- Develop a robust optimization framework using 1C discharge data
- Scale and validate the optimized model using:
  - HPPC data
  - WLTP drive cycle data (95k km, cycle-0)

---

## Modeling Framework
- **Electrochemical Model**: Single Particle Model (SPM / SPM+)
- **Simulation Library**: PyBaMM
- **Data Sources**:
  - Experimental 1C discharge data
  - HPPC pulse data
  - WLTP drive cycle data
  - Half-cell parameter database (liiondb)
- **Optimization Strategy**:
  - Manual and numerical optimization
  - RMSE-based voltage fitting
  - Physics-consistent parameter bounds

---

## Project Structure and File Descriptions

### Main Calibration and Validation
| File | Description |
|------|-------------|
| `Maintestfile.ipynb` | Main validation notebook. Uses optimized parameters to simulate HPPC and WLTP cycles and compares voltage response |
| `Optimization set up.ipynb` | Defines optimization objective functions, parameter bounds, RMSE evaluation, and solver setup |


---

### Geometry Optimization (Capacity Matching)
| File | Description |
|------|-------------|
| `Electrode_Thickness.ipynb` | Optimization of positive and negative electrode thickness to match capacity (Ah) |
| `Particle Radius.ipynb` | Sensitivity analysis and tuning of particle radii |
| `Initial_Conc_Positive.ipynb` | Optimization of initial lithium concentration in the positive electrode |
| `Initial_Conc_Negative.ipynb` | Optimization of initial lithium concentration in the negative electrode |
| `Max_Conc_Positive.ipynb` | Analysis of maximum concentration bounds (positive electrode) |
| `Max_Conc_Negative.ipynb` | Analysis of maximum concentration bounds (negative electrode) |

---

### Diffusion and Kinetics Sensitivity
| File | Description |
|------|-------------|
| `Positive_Particle_difffusivity.ipynb` | Effect of positive particle diffusivity on voltage response and overpotentials |
| `Negative_Particle_difffusivity.ipynb` | Effect of negative particle diffusivity on voltage response and overpotentials |

---

### HOCV Selection and Optimization
| File | Description |
|------|-------------|
| `DATA_Extraction_from_Liiondb.ipynb` | Extraction and preprocessing of HOCV data from the liiondb database |
| `HOCVs_optimization.ipynb` | Initial manual HOCV matching to experimental voltage |
| `HOCVs_optimization_part2.ipynb` | Refined joint optimization of HOCVs together with geometry parameters |

---

### Experimental Data
| File | Description |
|------|-------------|
| `951_Cap_1Cb.csv` | Experimental 1C discharge data used for baseline optimization |
| `951_HPPC.csv` | HPPC pulse data for transient validation |
| `WLTP data (embedded)` | WLTP drive cycle corresponding to 95k km, cycle-0 |

---

## Workflow Summary

⚙️ Workflow Summary

1C Discharge

   ↓
Geometry Optimization → Capacity Matching (Ah)

   ↓
Manual HOCV Selection (liiondb)

   ↓
Joint Geometry + HOCV Optimization

   ↓
Parameter Sensitivity & Bounds Analysis

   ↓
HPPC Validation

   ↓
WLTP (95k km) Drive Cycle Validation


---

## Evaluation Metrics
- Voltage RMSE
- Overpotential decomposition:
  - Kinetic overpotential
  - Diffusion overpotential
  - Ohmic losses

---

## Requirements
- Python >= 3.9
- PyBaMM
- NumPy
- SciPy
- Pandas
- Matplotlib

---

## Important Notes
- Current sign convention is critical (discharge current > 0 in PyBaMM)
- HOCVs are manually curated first before joint optimization
- Parameter bounds are chosen to ensure physical realism
- WLTP validation is performed without re-tuning parameters

---

## Future Extensions
- Full DFN model comparison
- Inclusion of aging and degradation parameters
- Automated HOCV selection
- Global parameter estimation

---

## Author
**Mohd Almasood**  
Materials and Energy Engineering  
Electrochemical Modeling and Battery Diagnostics

