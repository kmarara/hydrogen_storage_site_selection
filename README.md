# Subsurface Green Hydrogen Storage Site Selection

## Project Overview
I am building an open-source Python framework to identify optimal locations for subsurface green hydrogen storage. The goal is to create a "Site Suitability Heatmap" that helps developers and governments (especially in Africa and Europe) find where it is cheapest AND safest to store hydrogen.

## Research Problem
The global energy transition requires large-scale hydrogen storage. Subsurface geological formations (depleted oil/gas fields, saline aquifers) are the safest and cheapest option for long-term, large-volume storage. However, finding the optimal location requires balancing multiple competing factors:
- Renewable energy potential (solar irradiance)
- Water availability (water stress)
- Geological suitability (basin type, caprock integrity)
- Socio-economic factors (proximity to end-users, safety buffers)
- Physics-based constraints (H2-brine interfacial tension, capillary trapping)

No open-source tool currently integrates all these factors into a single, physics-informed geospatial framework.

## Technical Stack
- **Python:** Pandas, GeoPandas, Rasterio, Folium, NumPy
- **Learning:** Physics-Informed Neural Networks (PINNs) for thermodynamic constraints
- **Data Layers:** Solar Irradiance, Water Stress, Subsurface Geology, End-User Proximity

## Current Capabilities
### Phase 1: Data Foundation ✅
- Loaded and preprocessed 5 data layers for Southern Africa ROI
- Clipped rasters to study area (lon 12-22°E, lat -20 to -10°N)
- Created baseline weighted overlay maps with equal weights
- Generated Folium interactive heatmaps

### Phase 2: Multi-Objective Optimization 🟡
- Normalized all raster layers to [0, 1] scale
- Tested 100 random weight configurations
- Generated robustness map showing 34% of pixels are consistently suitable
- Identified best/worst weight configurations for sensitivity analysis

### Phase 3: PINN Integration 📅 (Planned)
- Integrating Physics-Informed Neural Networks (PINNs) for H2-brine IFT prediction
- Based on Dr. Ahmed Farid's work: R² = 0.91 extrapolation performance

## Repository Structure
```
hydrogen_storage_site_selection/
├── README.md          ← This file (project overview)
├── PROJECT_BRIEF.md   ← Full project brief & milestones
├── notebooks/
│   ├── 01_data_exploration.ipynb    ← Data loading workflow
│   ├── 02_raster_preprocessing.ipynb ← Clipping/reprojection
│   ├── 03_vector_overlay.ipynb     ← GeoPandas spatial joins
│   └── 04_folium_heatmap.ipynb     ← Interactive heatmap
├── data/
│   ├── processed/      ← Normalized clipped rasters
│   └── raw/            ← Reference data sources (see below)
├── outputs/            ← Generated maps & figures
│   ├── robustness_map.png
│   ├── best_worst_overlays.png
│   └── folium_heatmap.html
└── .gitignore          ← Excludes notes, test files, large data
```

## Data Sources (Reference, Not Included)
| Dataset | Source | Notes |
|---------|--------|-------|
| Solar Irradiance | Global Solar Atlas: https://globalsolaratlas.info | Freely available |
| Water Stress | WRI Aqueduct: https://www.wri.org/aqueduct | Freely available |
| Subsurface Geology | USGS World Petroleum Assessment | Reference only |
| End-User Proximity | Industrial data, port locations | Reference only |

## Getting Started
1. Clone the repo to explore the code
2. Open `notebooks/01_data_exploration.ipynb` to see data loading
3. Run `notebooks/02_raster_preprocessing.ipynb` to clip/reproject your own data
4. View `outputs/folium_heatmap.html` for an interactive example
5. Read `PROJECT_BRIEF.md` for the full 12-week roadmap

## Learning Path
This project follows a 12-week fast-track timeline designed to:
- Build a complete geospatial framework
- Publish a paper on subsurface hydrogen storage site selection
- Use the work as a centerpiece for Master's scholarship applications (UCL, Aalto, LUT)

**Created by:** Kudakwashe Douglas Marara  
**Institution:** University of Zimbabwe (BSc Hons Petroleum Chemistry, 2025)  
**Target:** September 2027 Master's Intake  
**Email:** kudakwashe.d.marara@gmail.com

## Acknowledgments
- Dr. Ahmed Farid (PINNs for H2-brine IFT)
- Pio Petro Online Internship (Hydrogen Track)
- University of Zimbabwe Supervisors
- Open data providers (Global Solar Atlas, WRI Aqueduct, USGS)
``