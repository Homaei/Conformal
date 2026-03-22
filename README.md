# 🌊 Conformal Prediction-Driven Adaptive Sampling for WDN Digital Twins

![Status](https://img.shields.io/badge/Project-Active-brightgreen)
![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![License](https://img.shields.io/badge/License-MIT-black)
![PyTorch](https://img.shields.io/badge/ML-PyTorch-red)
![Hydraulics](https://img.shields.io/badge/Simulation-EPANET%202.2-lightgrey)
![Coverage](https://img.shields.io/badge/CP%20Coverage-90%25-success)

Official implementation for the paper:

> **Conformal Prediction-Driven Adaptive Sampling for Digital Twins of Water Distribution Networks**  
> *Homaei,  Mohammadhossein and Tarif,  Mehran and Rodriguez,  Pablo Garcia and Caro,  Andres and Avila,  Mar*  
> ICT Express, 2026

---

## 🚀 Overview

This project introduces a **Conformal Prediction (CP)-based adaptive sampling strategy** for efficient sensor placement in Water Distribution Network (WDN) Digital Twins.

It dynamically identifies high-uncertainty nodes and prioritizes them for sensing — improving state estimation performance while minimizing sensing infrastructure.

### ✅ Highlights

| Feature | Description |
|--------|-------------|
| Sensor Efficiency | Superior accuracy with fewer sensors |
| Improvement | **33–34% lower RMSE** at 40% sensor coverage |
| Uncertainty Guarantees | Empirical CP coverage: **90.2%** |
| Computation | Only **5–10%** overhead |

---

## 🧠 Framework Architecture

1. Train node-wise LSTM demand forecasters  
2. Calibrate CP intervals per node  
3. Iteratively:
   - Predict demand
   - Compute uncertainty from CP interval width
   - Select top-k uncertain nodes for real measurements  
4. Run **single-step EPANET** for hydraulic consistency

---

## 📦 Installation

### Requirements

- Python ≥ 3.9  
- PyTorch, WNTR, EPANET 2.2
- Parquet datasets for demand & pressure

### Setup

```bash
git clone https://github.com/Homaei/Conformal.git
cd Conformal
pip install -r requirements.txt
```

🚨 Make sure EPANET binary is installed and discoverable by WNTR.


📁 Repository Structure
```bash
/Conformal
├── /data
│   ├── /inp
│   │   ├── Hanoi.inp
│   │   ├── Net3.inp
│   │   └── CTOWN.inp
│   └── /scenarios
│       ├── hanoi_demand_1Y.parquet
│       └── ...
├── Conformal_Adaptive_Sampling_Full_Replication.ipynb
├── requirements.txt
└── README.md
```
### Run

All pipeline components are included in the notebook:

📌 Conformal_Adaptive_Sampling_Full_Replication.ipynb

Key hybrid physics-ML simulation function


def run_single_step_epanet(inp_file_path, demand_vector_t, junction_names):
```bash
    Executes a single EPANET step using hybrid CP-updated demand input.
    Returns updated pressure values sorted by junction_names.
```
📊 Results

| Metric            | Uniform | CP-Adaptive | Gain    |
| ----------------- | ------- | ----------- | ------- |
| Demand RMSE (L/s) | 1.92    | 1.28        | ✅ 33.3% |
| Pressure RMSE (m) | 1.43    | 0.95        | ✅ 33.6% |

| Safety Metric  | Target | Adaptive |
| -------------- | ------ | -------- |
| CP Coverage    | 90%    | ✅ 90.2%  |
| Violation Rate | ↓      | ✅ 0.23%  |


@article{Homaei2026conformal,
  title = {Conformal prediction-driven adaptive sampling for digital water twins},
  ISSN = {2405-9595},
  DOI = {10.1016/j.icte.2026.01.010},
  journal = {ICT Express},
  publisher = {Elsevier BV},
  author = {Homaei,  Mohammadhossein and Tarif,  Mehran and Rodriguez,  Pablo Garcia and Caro,  Andres and Avila,  Mar},
  year = {2026},
  month = jan 
}


## Contact

🧑‍💻 Hubert Homaei — hoamei@ieee.org
