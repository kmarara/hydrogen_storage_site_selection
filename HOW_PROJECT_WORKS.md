# How This Project Works

## Overview
This Python framework identifies optimal locations for subsurface hydrogen storage using a **geospatial multi-objective optimization approach** integrated with **Physics-Informed Neural Networks (PINNs)**.

## The Problem
Finding the best subsurface hydrogen storage site requires balancing:
1. **Renewable energy potential** (solar irradiance)
2. **Water availability** (water stress)
3. **Geological suitability** (basin type, porosity, permeability)
4. **Socio-economic factors** (proximity to end-users, population density)
5. **Physics-based constraints** (H2-brine interfacial tension, capillary trapping)

## The Workflow

### Phase 1: Data Foundation (Weeks 1-4)
1. **Load data layers** (solar, water, geology, users, population)
2. **Clip rasters** to your region of interest (ROI)
3. **Reproject all layers** to a common CRS (EPSG:4326 WGS84)
4. **Normalize** each layer to [0, 1] scale

### Phase 2: Multi-Objective Optimization (Weeks 5-8)
1. **Create weighted overlay** maps using configurable weights
2. **Run sensitivity analysis** with random weight configurations
3. **Generate robustness map** showing which pixels are consistently suitable
4. **Identify Pareto-optimal** weight sets based on trade-offs

### Phase 3: PINN Integration (Weeks 9-12)
1. **Integrate PINN** for H2-brine Interfacial Tension (IFT) prediction
2. **Add "Safety Penalty" layer** to the heatmap
3. **Re-run optimization** with physics-informed constraints
4. **Generate final heatmap** with physics-based rankings

## Key Files & Their Purpose

| File | What It Shows |
|------|--------------|
| `PROJECT_BRIEF.md` | Full project brief, problem statement, 12-week milestones, learning workflow |
| `README.md` | Project overview, technical stack, getting started guide |
| `notebooks/01_data_exploration.ipynb` | Load and explore data layers, create synthetic data |
| `notebooks/02_raster_preprocessing.ipynb` | Clip/reproject rasters to ROI, normalize layers |
| `notebooks/03_vector_overlay.ipynb` | GeoPandas spatial joins, basins + end-users analysis |
| `notebooks/04_folium_heatmap.ipynb` | Folium interactive heatmap, markers, layer control |
| `outputs/folium_heatmap.html` | Interactive map (open in browser) |
| `outputs/robustness_map.png` | How often each pixel ranks high across random weights |
| `outputs/best_worst_overlays.png` | Comparison of best vs. worst weight configurations |

## Data Sources (Reference, Not Included)
| Dataset | Source | Notes |
|---------|--------|-------|
| Solar Irradiance | Global Solar Atlas | Freely available |
| Water Stress | WRI Aqueduct | Freely available |
| Subsurface Geology | USGS World Petroleum Assessment | Reference only |
| End-User Proximity | Industrial data, port locations | Reference only |

## Running the Framework
1. **Clone the repo** or download the files
2. **Install requirements:** `pip install geopandas rasterio folium numpy`
3. **Place your data** in `data/raw/` (GeoTIFF and shapefiles)
4. **Run notebooks sequentially:**
   - `01_data_exploration.ipynb` - Load and verify data
   - `02_raster_preprocessing.ipynb` - Clip and normalize
   - `03_vector_overlay.ipynb` - Spatial joins and analysis
   - `04_folium_heatmap.ipynb` - Generate interactive map
5. **View the output** in `outputs/folium_heatmap.html`

## Customizing for Your Region
1. **Update the ROI** in notebook 02 (change the `box()` coordinates)
2. **Replace synthetic data** with your actual datasets in `data/raw/`
3. **Adjust weights** in the multi-objective optimization notebooks
4. **Integrate PINN** using the framework described in `PROJECT_BRIEF.md`

## Contact & Citation
- **Created by:** Kudakwashe Douglas Marara
- **Institution:** University of Zimbabwe (BSc Hons Petroleum Chemistry, 2025)
- **Email:** kudakwashe.d.marara@gmail.com
- **GitHub/LinkedIn:** [add your profile URL]
- **Target Master's:** UCL MSc Energy Systems, Aalto MSc Hydrogen, LUT MSc Power-to-X

## Citation
If you use this framework in your work, please cite:
```
Marara, K.D. (2026). Subsurface Green Hydrogen Storage Site Selection:
A Geospatial Multi-Objective Optimization Framework. 
Unpublished project repository. GitHub.
```

## Licensing
This project is open for learning and adaptation. Please credit the original creator and acknowledge the data sources listed above.
``