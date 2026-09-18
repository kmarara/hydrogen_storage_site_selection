# PAPER OUTLINE: A Decision-Support Framework for Subsurface Hydrogen Storage Site Selection

## 1. INTRODUCTION
### 1.1 Decision Problem Framing
- The global hydrogen economy requires large-scale subsurface storage in geological formations
- Uncertainty in Interfacial Tension (IFT) between H2 and brine affects capillary trapping, injectivity, and containment security
- Decision-makers need tools to balance cost, safety, and sustainability under deep uncertainty
- Current gap: No existing decision-support frameworks integrate multi-objective optimization with physics-informed neural networks (PINNs) for H2-brine IFT prediction in a geospatial context

### 1.2 Novel Contribution
- A two-layer decision-support framework integrating geospatial multi-objective optimization with PINNs
- Strategic screening layer for regional go/no-go decisions
- Tactical planning layer for site-specific analysis with physics-based safety penalties
- Decision-ready output: go/no-go recommendations with risk ranges

## 2. LITERATURE REVIEW: FORENSIC SEARCH FOCUS
### 2.1 Multi-Objective Decision Analysis for Energy Infrastructure
- Existing studies on multi-criteria decision analysis (MCDA) for energy infrastructure siting
- Limited applications specifically for hydrogen storage site selection
- Decision theory approaches to handling uncertainty in energy infrastructure planning

### 2.2 Geospatial Site Selection for Energy Infrastructure
- Existing geospatial models for renewable energy siting (solar, wind)
- Limited applications for subsurface hydrogen storage
- Use of GIS-based weighted overlay and analytic hierarchy processes (AHP)

### 2.3 Physics-Informed Neural Networks in Geoscience
- PINNs for predicting H2-brine Interfacial Tension (IFT) - reference Farid's work
- Previous applications of PINNs in geoscience and subsurface modeling
- Limitations of purely data-driven models for extrapolation beyond training ranges
- Advantages of embedding thermodynamic constraints (Peng-Robinson EOS, Linear Gradient Theory)

### 2.4 Decision Analysis for Energy Infrastructure under Uncertainty
- Robust decision-making (RDM) approaches for energy infrastructure
- Real options analysis for energy investment decisions
- Uncertainty quantification techniques for subsurface properties

## 3. METHODOLOGY: TWO-LAYER DECISION-SUPPORT FRAMEWORK

### 3.1 Strategic Screening Layer (Regional-Level)
#### 3.1.1 Data Layers
- Solar Irradiance (Global Solar Atlas)
- Water Stress (WRI Aqueduct)
- Subsurface Geology (USGS Basins / Depleted Fields)
- Population Density (SEDAC)
- Economic Proximity (industrial clusters, ports)

#### 3.1.2 Normalization and Weighting
- Min-max normalization to [0, 1] scale
- Weight sensitivity analysis (testing 100 random weight configurations)
- Identification of robustly suitable vs. volatile sites

#### 3.1.3 Output
- Regional heatmap showing go/no-go areas
- Decision criteria: areas meeting minimum thresholds across all objectives
- Uncertainty indicators: pixels with high weight sensitivity

### 3.2 Tactical Planning Layer (Site-Specific Analysis)
#### 3.2.1 PINN Integration for H2-brine IFT Prediction
- Architecture: 4 hidden layers with Tanh activation
- Input variables: Pressure, Temperature, Salinity
- Physics loss: Peng-Robinson EOS + Linear Gradient Theory (LGT)
- Learnable parameters: EOS/LGT constants adapted during training
- Training data: 400 experimental H2-brine IFT data points

#### 3.2.2 Safety Penalty Layer
- IFT prediction used as "storage safety penalty"
- High IFT → higher capillary trapping risk → lower safety score
- Integrated with geospatial weighted overlay

#### 3.2.3 Site-Specific Analysis
- Grid-based analysis at 1km resolution
- Uncertainty ranges from PINN prediction intervals
- Output: site suitability score with confidence intervals

### 3.3 Coupling the Two Layers
- Strategic layer identifies candidate regions
- Tactical layer analyzes individual sites within candidates
- Iterative refinement: strategic layer informs tactical analysis boundaries

## 4. CASE STUDY: SOUTHERN AFRICA
### 4.1 Study Area Description
- Southern Africa region (Namibia, Botswana, South Africa west coast)
- Rationale: significant hydrogen potential, underexplored storage options
- Data availability: open access from Global Solar Atlas, WRI Aqueduct, USGS

### 4.2 Strategic Screening Results
- Regional heatmap with go/no-go areas
- Identification of 3-5 candidate regions for further analysis
- Decision criteria thresholds and rationale

### 4.3 Tactical Planning Results
- Site-specific analysis of 3-5 candidate sites
- IFT predictions with uncertainty ranges
- Safety penalty integration and impact on suitability scores
- Go/no-go recommendations with risk ranges

### 4.4 Decision Impact
- How the framework reduces investment risk
- Policy implications for Southern Africa
- Comparison with existing approaches

## 5. DISCUSSION
### 5.1 Decision Framework Evaluation
- Effectiveness in reducing investment risk
- Balance between specificity and generality
- User-friendliness for decision-makers
- Comparison with existing decision-support tools

### 5.2 Uncertainty and Limitations
- Sources of uncertainty: data, model, parameter
- Uncertainty quantification approaches used
- Limitations of PINN extrapolation beyond training ranges
- Geographic transferability of framework

### 5.3 Policy and Industry Implications
- How the framework supports investment decisions
- Regulatory implications
- Integration with existing pipeline and storage planning processes

## 6. CONCLUSION
### 6.1 Key Contributions
- Two-layer decision-support framework for H2 storage site selection
- Integration of PINNs for physics-based IFT prediction
- Decision-ready output with go/no-go recommendations
- Transferability to other regions and energy storage types

### 6.2 Future Work
- Expansion to multi-component gas systems (H2-CO2-CH4)
- Integration with reservoir simulation models
- Real options analysis for staged investment decisions
- Framework adaptation for carbon capture and storage (CCS) applications

## 7. REFERENCES
- Farid, A. (2026). Physics-informed model for H2-brine interfacial tension prediction outside the development range: Hydrogen storage implications. Results in Engineering.
- Additional references on multi-objective decision analysis, geospatial site selection, and PINNs in geoscience

---

## Learning Objectives

### Technical Skills
- Advanced multi-objective optimization using Python (Pandas, NumPy)
- Sensitivity analysis with random weight configurations
- PINN implementation using PyTorch or TensorFlow
- Integration of thermodynamic constraints (Peng-Robinson EOS, LGT) into neural networks
- Geospatial analysis with GeoPandas and Rasterio

### Decision Science Concepts
- Multi-criteria decision analysis (MCDA) frameworks
- Uncertainty quantification and propagation
- Robust decision-making under deep uncertainty
- Decision theory applications for energy infrastructure
- Go/no-go criteria development and justification

### Python Implementation Skills
- Building and training PINNs with PyTorch/TensorFlow
- Geospatial data processing with GeoPandas and Rasterio
- Creating decision-ready visualizations with Folium/Matplotlib
- Uncertainty quantification and visualization
- Exporting results in formats suitable for decision-makers

---

## PROJECT TIMELINE (12 Weeks)

### Phase 1: Data Foundation (Weeks 1-4)
- Data loading and preprocessing
- Geospatial clipping and normalization
- Baseline weighted overlay maps
- **Milestone:** Complete 4 notebooks

### Phase 2: Multi-Objective Optimization (Weeks 5-8)
- Weight sensitivity analysis
- Robustness mapping
- Identifying Pareto-optimal weight sets
- **Milestone:** Regional heatmap with sensitivity indicators

### Phase 3: PINN Integration (Weeks 9-11)
- PINN architecture design and training
- Safety penalty layer integration
- Site-specific analysis on candidate sites
- **Milestone:** Two-layer framework operational

### Phase 4: Case Study and Write-up (Week 12)
- Southern Africa case study
- Decision-ready map generation
- Paper outline completion
- **Milestone:** Complete paper outline and decision-support framework demonstration

---

## HOW THE AI SHOULD HELP

### When I ask for code:
- Write clean, commented Python
- Explain the "why" behind each step
- Connect methodology to decision-support goals
- Ensure PINN integration serves the decision framework

### When I ask about concepts:
- Use decision-science framing
- Connect to PhD application goals
- Provide both theoretical and implementation perspectives
- Emphasize practical decision-support utility

### When I'm stuck:
- Break the problem into decision-layer components
- Connect to existing framework components
- Provide both theoretical and practical perspectives
- Emphasize the decision-support utility of the solution

---

## STATUS UPDATE: WHERE WE ARE (For Next Session)

### Current Project State
- **Framework:** Two-layer decision-support framework for subsurface hydrogen storage site selection
- **Data:** 5 geospatial layers loaded and normalized for Southern Africa ROI
- **Notebooks:** 4/4 complete (01-data exploration, 02-raster preprocessing, 03-vector overlays, 04-Folium heatmap)
- **Findings:** Weight sensitivities ~0.33 each (solar, water, population); 34% of pixels robustly suitable across weight configurations
- **PINN Status:** Framework documented; ready for integration in Phase 3

### What's Complete
- ✅ Data foundation: 5 raster layers normalized and clipped to Southern Africa
- ✅ Multi-objective optimization: 100 weight configurations tested, robustness map generated
- ✅ Documentation: PROJECT_BRIEF.md, PAPER_OUTLINE.md, HOW_PROJECT_WORKS.md
- ✅ Notebooks: All 4 complete and pushed to GitHub

### What's Next
1. **Phase 3, Week 9:** Begin PINN integration for H2-brine IFT prediction
2. **Connect strategic and tactical layers:** Link regional heatmap to site-specific analysis
3. **Case study:** Southern Africa demonstration with go/no-go recommendations
4. **Paper outline:** Complete all sections per the outlined structure
5. **PhD application material:** Frame project as decision-support framework

### Immediate Next Session Goals
- Begin PINN integration (Phase 3, Week 9)
- Connect strategic screening layer with tactical planning layer
- Start Southern Africa case study demonstration
- Document framework outputs as decision-ready recommendations

---
*This status update provides a clear picture of the project state for the next session, emphasizing the decision-support framework direction and where we are in the 12-week timeline.*