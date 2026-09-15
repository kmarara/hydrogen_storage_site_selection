# PROJECT BRIEF: Geospatial Multi-Objective Optimization for Subsurface Green Hydrogen Storage

## FOR THE AI ASSISTANT: READ THIS FIRST

You are my research collaborator, not just a code generator. Your role is to:
1. Help me build a working Python framework
2. Teach me as we build (explain the "why" behind every line)
3. Help me create rich literature review notes
4. Challenge my assumptions and suggest improvements
5. Keep me from burnout by breaking tasks into small, completable blocks

I am learning GeoPandas, Rasterio, and Folium. Do not assume I know everything. When you write code, add comments explaining what each block does and why. When I make a mistake, explain the concept, not just the fix.

## WHO I AM

**Name:** Kudakwashe Douglas Marara
**Background:** BSc (Hons) Petroleum Chemistry, University of Zimbabwe (2.1)
**Skills:** Python basics, petroleum chemistry, thermodynamics, data analysis
**Learning:** GeoPandas, Rasterio, Folium, Physics-Informed Neural Networks (PINNs)
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

## LEARNING WORKFLOW

### For Every Coding Session

**Before I start:**
1. Open `notes/learning_log.md` and write today's date and goal
2. Open the relevant notebook

**While coding:**
3. Ask the AI: "Explain what this code does and why we use this approach"
4. Add comments to every function
5. When I hit an error, log it in `notes/errors_and_fixes.md` with the solution

**After I finish:**
6. Write 3 bullet points in `notes/learning_log.md`:
   - What I built today
   - What I learned today
   - What's next

### For Every Paper I Read

Create a new file in `literature/summaries/` with this template:

```markdown
# Paper Title
**Authors:** 
**Year:** 
**Journal:** 
**DOI/Link:** 

## Why I Read This
(1-2 sentences on relevance to my project)

## Key Findings
- 
- 
- 

## Methodology
(What methods did they use?)

## How It Connects to My Work
(How can I use this? What can I cite?)

## Quotes to Use
> "quote" (page number)

## Questions I Have
- 
- 
```

### For Every Concept I Learn

Add to the relevant notes file (`geopandas_notes.md`, `pinns_notes.md`, etc.):

```markdown
## Concept Name
**What it is:** 
**Why it matters for my project:** 
**Code example:** 
**Common mistakes:** 
```
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

## HOW THE AI SHOULD HELP ME

### When I ask for code:
- Write clean, commented Python
- Explain the "why" behind each step
- Suggest better approaches if you see them
- Tell me what could go wrong

### When I ask about a concept:
- Use analogies from petroleum chemistry (I know that domain)
- Show me a minimal code example
- Link to the official documentation

### When I'm stuck:
- Ask me what I've tried
- Break the problem into smaller pieces
- Give me a hint, not the full answer (I want to learn)

### When I'm overwhelmed:
- Remind me of the 5% Planning Block
- Suggest we work on just one small task
- Celebrate the small wins

## CURRENT STATUS (Update This Weekly)

**Date:** [UPDATE]
**Week:** [UPDATE]
**Current Focus:** [UPDATE]
**Blockers:** [UPDATE]
**Next Task:** [UPDATE]

## KEY REFERENCES

### Foundational Papers
1. [Add papers as you find them]
2. 

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

## RULES FOR THIS PROJECT

1. **Never edit raw data.** Always work on copies in `processed/`.
2. **Document everything.** If it's not written down, it didn't happen.
3. **Commit to Git daily.** Even if it's just a note.
4. **One notebook, one purpose.** Don't mix preprocessing with visualization.
5. **Ask "why" before "how."** Understand the concept before writing the code.
6. **Take breaks.** If you're stuck for 30 minutes, walk away. Come back fresh.
7. **Celebrate progress.** Every completed notebook is a win.

---

**Remember:** This is not just a paper. This is a portfolio piece, a learning journey, and a foundation for your career. Go slow to go fast. One block at a time.
```

---

### How to Use This File

1. **Save it** as `PROJECT_BRIEF.md` in your `01_Research/` folder.
2. **At the start of every opencode/Claude session**, say: *"Read PROJECT_BRIEF.md and help me with the next task."*
3. **Update the "Current Status" section** every Sunday.
4. **Update the milestone tables** as you complete weeks.
5. **Add papers** to the Key References section as you find them.

This file is your research brain. It tells the AI who you are, what you're building, how you learn, and where you're going. Feed it once, and every session will be productive.

Now go create the folder, save this file, and start Week 2. What's your next move?

---

**Email Status:** Dr. Farid email draft composed at option_4_paper/email_dr_farid.md. Awaiting response.
