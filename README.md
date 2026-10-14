# Liga ACB: Advanced Play-by-Play Analytics & Spatial Shot Charts

## Project Overview

This repository contains a Data Engineering and Sports Analytics pipeline designed to process and analyze Play-by-Play match data from the Spanish basketball league (Liga ACB). 

By extracting and consolidating data from 325 individual match files, this project builds a robust in-memory Data Lake. The analytical focus is set on spatial tracking and offensive efficiency, utilizing X/Y coordinate normalization to project shot locations onto a standard FIBA court mapping, and calculating advanced modern basketball metrics such as Points Per Shot (PPS).

## Data Confidentiality & Size Notice

The raw Play-by-Play event datasets used in this project are not included in this repository. Due to data privacy constraints and the heavy file size of 325 individual match logs, the `/partidos` directory and the generated `acb_master_playbyplay.csv` file have been strictly excluded via `.gitignore`. 
Note: To execute the pipeline locally, users must provide their own raw CSV event files and place them inside a local `/partidos` directory.

## Tech Stack & Libraries

* Language: Python 3.10+
* Data Engineering: Pandas, NumPy, OS
* Spatial Visualization: Matplotlib, Seaborn (KDE Density Mapping)
* Metrics: Advanced Sports Analytics (PPS, True Shooting principles)

## Methodology & Technical Pipeline

### 1. Data Consolidation & Engineering (01_acb_data_consolidation.ipynb)
* Extracted and concatenated 325 individual CSV match files into a unified master DataFrame containing hundreds of thousands of registered events.
* Performed data cleaning, type conversion, and feature engineering to classify events into specific shot types (3PT, 2PT, FT) and evaluate shot outcomes.

### 2. Spatial Analysis & Shot Charts (02_shot_charts_eda.ipynb)
* Cleaned and normalized raw X/Y coordinates, projecting bilateral court data onto a single half-court symmetry by inverting the tracking axes.
* Built a custom FIBA half-court geometrical mapping using `matplotlib.patches`.
* Generated 2D topographic density maps (Heatmaps) using Kernel Density Estimation (KDE) to visually identify the league's primary shooting zones and the natural density of the 3-point line.

### 3. Advanced Efficiency Metrics (03_advanced_efficiency_metrics.ipynb)
* Evaluated offensive decision-making by calculating the Points Per Shot (PPS) metric across the league.
* Generated efficiency rankings for both ACB Teams and the Top 15 Individual Players (applying a strict minimum threshold of 100 shots to prevent statistical noise).
* Visualized performance disparities using Seaborn barplots.

## How to Run the Project

1. Clone the repository:
   git clone https://github.com/ekaingutierrez/acb-advanced-analytics.git

2. Install dependencies:
   pip install -r requirements.txt

3. Place your raw match CSV files inside a folder named `/partidos` in the root directory.

4. Run the analytical notebooks sequentially from 01 to 03.
