# FAST TRACK RESEARCH PROTOCOL
# Applied to: A Decision-Support Framework for Subsurface Green Hydrogen Storage


## WHO I AM

**Name:** Kudakwashe Douglas Marara
**Background:** BSc (Hons) Petroleum Chemistry, University of Zimbabwe (2.1)
**Skills:** Python basics, petroleum chemistry, thermodynamics, data analysis
**Learning Objectives:**

### Technical Skills
- Advanced multi-objective optimization using Python (Pandas, NumPy)
- Sensitivity analysis and robustness mapping
- PINN implementation using PyTorch or TensorFlow
- Integration of thermodynamic constraints (Peng-Robinson EOS, LGT) into neural networks
- Geospatial analysis with GeoPandas and Rasterio
- Decision-ready data visualization and export

### Decision Science Concepts
- Multi-criteria decision analysis (MCDA) frameworks
- Uncertainty quantification and propagation
- Robust decision-making under deep uncertainty
- Decision theory applications for energy infrastructure
- Go/no-go criteria development and justification

### Python Implementation Skills
- Building and training PINNs with PyTorch/TensorFlow
- Geospatial data processing with GeoPandas and Rasterio
- Creating decision-ready visualizations and exports
- Uncertainty quantification and propagation
- Exporting results in formats suitable for decision-makers
**Goal:** Build an open-source framework for hydrogen storage site selection, publish a paper, and use it for Master's applications (UCL, Aalto, LUT)

## THE RESEARCH PROJECT

### Title
Geospatial Multi-Objective Optimization for Subsurface Green Hydrogen Storage Site Selection: A Physics-Informed Approach

### Problem Statement
The global energy transition requires large-scale hydrogen storage. Subsurface geological formations (depleted oil/gas fields, saline aquifers) are the safest and cheapest option for long-term, large-volume storage. However, finding the OPTIMAL location requires balancing multiple competing factors:
- Renewable energy potential (solar irradiance)
- Water availability (water stress)
- Geological suitability (basin type, caprock integrity)
- Socio-economic factors (proximity to end-users, safety buffers)
- Physics-based constraints (H2-brine interfacial tension, capillary trapping)

No open-source tool currently integrates all these factors into a single, physics-informed geospatial framework. This project fills that gap.

### Research Questions
1. How can multi-objective optimization be used to rank subsurface hydrogen storage sites?
2. How can Physics-Informed Neural Networks (PINNs) be integrated into a geospatial model to incorporate thermodynamic constraints?
3. What are the optimal sites for hydrogen storage in Africa and Europe based on the integrated model?

### Data Layers

| Layer | Source | Format | Purpose |
|-------|--------|--------|---------|
| Solar Irradiance | Global Solar Atlas | GeoTIFF | Renewable energy potential |
| Water Stress | WRI Aqueduct | Raster/Shapefile | Water availability constraint |
| Subsurface Geology | USGS Basins / Depleted Fields | Shapefile | Geological suitability |
| End-User Proximity | Industrial clusters, ports | Shapefile | Economic viability |
| Population Density | SEDAC / WorldPop | Raster | Safety buffer constraint |

### The Physics Connection (PINNs)
I attended a lecture by Dr. Ahmed Farid on Physics-Informed Neural Networks (PINNs) for predicting H2-brine Interfacial Tension (IFT). I want to integrate this into the geospatial model.

**The Concept:** IFT is not constant. It changes with pressure, temperature, and brine salinity. High IFT means higher capillary trapping risk, which means lower storage safety. I want to train a simple PINN that predicts IFT at various reservoir conditions and use that as a "Storage Safety Penalty" layer in the heatmap.

**The Equation (Young-Laplace):** The PINN will enforce the Young-Laplace equation as a physics constraint during training.

## TECHNICAL STACK

### Core Libraries
- **GeoPandas**: Vector data handling (basins, depleted fields, end-users)
- **Rasterio**: Raster data handling (solar, water stress, population)
- **Folium**: Interactive heatmap visualization
- **NumPy/Pandas**: Data manipulation
- **Matplotlib**: Static plots for the paper

### PINN Libraries (Later Phase)
- **PyTorch** or **TensorFlow**: Building and training the PINN
- **SciPy**: Physics equations and optimization

### Development Environment
- Python 3.10+
- Jupyter Notebooks for exploration
- VS Code for scripts
- Git for version control

## PROJECT STRUCTURE

```
📁 option_4_paper/
│
├── 📄 PROJECT_BRIEF.md (this file)
├── 📄 README.md (public-facing project description)
├── 📄 TIMELINE.md (milestones and deadlines)
│
├── 📁 data/
│   ├── 📁 raw/ (original downloads, never edit)
│   │   ├── solar_irradiance.tif
│   │   ├── water_stress.tif
│   │   ├── usgs_basins.shp
│   │   └── population_density.tif
│   ├── 📁 processed/ (cleaned, clipped, reprojected)
│   └── 📁 outputs/ (heatmaps, final maps)
│
├── 📁 notebooks/
│   ├── 📄 01_data_exploration.ipynb
│   ├── 📄 02_raster_preprocessing.ipynb
│   ├── 📄 03_vector_overlay.ipynb
│   ├── 📄 04_multi_objective_optimization.ipynb
│   ├── 📄 05_pinn_ift_model.ipynb
│   └── 📄 06_final_heatmap.ipynb
│
├── 📁 src/
│   ├── 📄 data_loader.py
│   ├── 📄 preprocessor.py
│   ├── 📄 optimizer.py
│   ├── 📄 pinn_model.py
│   └── 📄 visualizer.py
│
├── 📁 notes/
│   ├── 📄 learning_log.md
│   ├── 📄 geopandas_notes.md
│   ├── 📄 rasterio_notes.md
│   ├── 📄 folium_notes.md
│   ├── 📄 pinns_notes.md
│   └── 📄 errors_and_fixes.md
│
├── 📁 literature/
│   ├── 📄 lit_review_master.md
│   ├── 📄 papers/ (PDFs)
│   └── 📄 summaries/
│       ├── 📄 paper_001_summary.md
│       └── 📄 ...
│
├── 📁 paper/
│   ├── 📄 outline.md
│   ├── 📄 abstract_draft.md
│   ├── 📄 methodology.md
│   └── 📄 figures/
│
└── 📁 admin/
    ├── 📄 weekly_progress.md
    └── 📄 supervisor_meetings.md
```


## MILESTONES (12-Week Plan)

### Phase 1: Foundation (Weeks 1-4)
**Goal:** Load, preprocess, and visualize all data layers

| Week | Milestone | Deliverable | Status |
|------|-----------|-------------|--------|
| 1 | Setup environment, load data | Notebook 01 complete | ✅ Done |
| 2 | Rasterio: Clip, reproject, resample rasters | Notebook 02 complete | ✅ Done |
| 3 | GeoPandas: Load basins, overlay vectors | Notebook 03 complete | ✅ Done |
| 4 | Folium: First interactive heatmap | Notebook 04 complete | ✅ Done |

### Phase 2: Optimization (Weeks 5-8)
**Goal:** Implement multi-objective optimization and weight sensitivity analysis

| Week | Milestone | Deliverable | Status |
|------|-----------|-------------|--------|
| 5 | Define weights, normalize layers | Optimizer script | ✅ Done |
| 6 | Weighted overlay, sensitivity analysis | Results table | ✅ Done |
| 7 | Multi-objective optimization (Pareto) | Pareto front plot | 🟡 In Progress |
| 8 | Case study: Southern Africa | Regional heatmap | ⏳ Pending |

### Phase 3: PINN Integration (Weeks 9-12)
**Goal:** Build PINN for IFT prediction and integrate as a layer

| Week | Milestone | Deliverable | Status |
|------|-----------|-------------|--------|
| 9 | Learn PINN basics (tutorials) | PINN notes | ⏳ Pending |
| 10 | Build PINN for H2-brine IFT | Working model | ⏳ Pending |
| 11 | Integrate PINN output as GIS layer | Updated heatmap | ⏳ Pending |
| 12 | Write paper draft | Full draft | ⏳ Pending |


## CURRENT STATUS 

**Date:** [UPDATE]
**Week:** [UPDATE]
**Current Focus:** [UPDATE]
**Blockers:** [UPDATE]
**Next Task:** [UPDATE]

## KEY REFERENCES

### Data Sources
1. Global Solar Atlas: https://globalsolaratlas.info
2. WRI Aqueduct: https://www.wri.org/aqueduct
3. USGS World Petroleum Assessment: https://pubs.usgs.gov
4. SEDAC Population Density: https://sedac.ciesin.columbia.edu

### Key Concepts
- Multi-Objective Optimization
- Physics-Informed Neural Networks (PINNs)
- Interfacial Tension (IFT)
- Capillary Trapping
- Site Suitability Analysis

---
```
