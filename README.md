---
title: Mars Mission Power
emoji: 🚀
colorFrom: blue
colorTo: green
sdk: docker
app_file: src/streamlit_app.py
app_port: 8501
tags:
- streamlit
pinned: false
short_description: Martian landing focusing on power budgeting.

license: mit
---

# Mars Mission Planning
demo@ [streamlit communities](https://mars-mission-power.streamlit.app/)

## Overview
A research toolkit for optimizing Martian mission planning, focused on solar power generation, dust deposition, and landing site selection. This project integrates Radiative Transfer Models (RTM) with machine learning to support robust power planning and dust mitigation strategies.
## Objectives

### Power Management 
- Estimate power availability at Martian landing sites to meet subsystem demands.

- Use RTMs to simulate variability in solar irradiance across sites and seasons.

- Ingest atmospheric and solar data from the Mars Climate Database (MCD) and relevant literature.

### Dust Deposition Impact Analysis
- Quantify the impact of dust accumulation on solar array performance.

- Leverage daily mean dust deposition data from MCD.

- Model performance degradation using a linear rate (e.g., 0.2% per sol, based on NASA InSight).

### Optimal Site Selection
- Identify optimal sites for each launch window based on solar resource availability and dust impact.

- Combine RTM outputs (direct, diffuse, effective irradiance) with degradation models.

- Estimate operational payload support hours per site/window to maximize mission duration.


### Dust Deposition Prediction
- Use machine learning to predict the rate of dust deposition based on RTM outputs.
 
- Incorporate features such as top-of-atmosphere irradiance, direct component, and diffuse component.
 
- Address underprediction issues, especially at higher dust deposition rates.

## Models and Data
- **Radiative Transfer Model (RTM)**: Based on COMIMART, adapted for surface-level solar flux calculations on Mars.
- **Data Sources**: Mars Climate Database (MCD) for atmospheric & dust parameters. Literature-sourced constants and assumptions for model calibration.
- **Machine Learning Models**: Ensemble tree regressors and SVMs for dust prediction.

## Repository Structure

```plaintext
mars_mission_power/
├── streamlit_app.py                        # Main Streamlit app entry point
│
├── data/
│   ├── site_tau.csv              # Optical depth (tau) data
│   └── site_dd_mean.csv          # Daily mean dust deposition rates
│
├── # Source code and modules
│   ├── RTM_implementation.py              # RTM for solar irradiance
│   ├── mars_environment.py                # Mars atmospheric ingestion
│   ├── complete_year_irr.py               # Year-round irradiance modeling
│   ├── complete_year_analysis.py          # Visualization of irradiance outputs
│   ├── dust_deposition_analysis.py        # Degradation model for solar arrays
│   ├── load_support.py                    # Payload power support estimation
│   ├── ML_data_creation.py                # ML dataset generation
│   ├── ML_for_dust_deposition_rate_prediction.py
│   ├── ensembled_tree_models.py           # Random Forest, XGBoost, etc.
│   ├── svm.py                             # SVM and kNN regression
│   └── model_evaluation_and_plotting.py   # Metrics + performance visualization
│
├── outputs/                    # Generated plots, model predictions, etc.
│
└── README.md                  # This document

Collaborator: [Prajjwal Yash](https://github.com/PrajjwalYash)
