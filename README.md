# AI-Powered Carbon Additionality, Plantation Monitoring and Forest Change Detection System

## Overview

This project is an end-to-end geospatial AI and carbon-monitoring platform designed to help forestry professionals, carbon-project developers, auditors, verification teams, investors, and sustainability stakeholders determine whether reported carbon gains are genuinely attributable to a project intervention.

The system combines:

- remote sensing,
- satellite time-series analysis,
- geospatial data engineering,
- computer vision,
- anomaly detection,
- biomass estimation,
- statistical reference-area comparison,
- carbon accounting,
- Generative AI reporting,
- and human expert verification.

Its purpose is not merely to detect vegetation change. It is designed to distinguish:

- pre-existing trees from new plantation,
- natural growth from project-attributable growth,
- seasonal variation from real canopy change,
- temporary clearing from long-term forest recovery,
- and total carbon stock from potentially claimable carbon.

---

## Business Problem

Forestry and plantation-based carbon projects cannot claim every tonne of carbon visible after implementation.

A valid carbon claim must demonstrate that the reported benefit is:

- additional to the pre-project baseline,
- attributable to project implementation,
- not the result of natural regional growth,
- not based on trees already present before the project,
- not hiding temporary cutting, degradation, or reversal events,
- and supported by transparent, reproducible evidence.

### Example

Suppose the project area contains:

```text
Pre-project carbon stock: 500 tonnes
Post-project carbon stock: 720 tonnes
```

The project cannot claim all 720 tonnes.

The first gross change is:

```text
Gross increase = 720 - 500
Gross increase = 220 tonnes
```

Further adjustments may be required for:

- reference-area change,
- natural regeneration,
- leakage,
- uncertainty,
- reversal risk,
- methodology-specific deductions,
- and permanence requirements.

The system therefore focuses on measuring **eligible incremental change**, not merely total forest cover.

---

## Core Project Objective

The main objective is to build a decision-support platform that:

1. establishes a pre-project vegetation and carbon baseline,
2. identifies pre-existing tree cover,
3. detects post-project plantation and canopy growth,
4. compares the project area with a similar reference area,
5. detects canopy loss, cutting, fire, degradation, and regrowth,
6. estimates biomass and carbon-stock change,
7. quantifies potentially attributable carbon,
8. generates maps, alerts, evidence, and reports,
9. and supports human verification before any carbon claim is accepted.

---

## Key Use Cases

### 1. Pre-Project Baseline Mapping

The system identifies:

- existing tree cover,
- existing plantation,
- natural forest,
- degraded land,
- scrub and sparse vegetation,
- bare land,
- water,
- and built-up areas.

The baseline is stored as a versioned, auditable reference.

---

### 2. Pre-Existing Tree Identification

The system separates:

- trees already present before project implementation,
- trees planted after the project start date,
- natural regeneration,
- and growth in old trees.

This prevents old trees from being incorrectly counted as new project-generated carbon.

---

### 3. Plantation Monitoring

The platform monitors:

- plantation establishment,
- canopy development,
- survival indicators,
- vegetation density,
- moisture stress,
- plantation failure,
- gaps in planting,
- and spatial differences in growth.

---

### 4. Forest Change Detection

The system detects:

- canopy loss,
- abrupt vegetation decline,
- possible harvesting,
- fire,
- degradation,
- clearing,
- soil exposure,
- regrowth,
- and suspicious loss-and-recovery patterns.

---

### 5. Cutting and Regrowth Monitoring

A major challenge occurs when monitoring happens only once every few years.

Example:

```text
Year 1: Forest present
Year 2: Trees cut
Year 3: Vegetation regrows
Year 4: Monitoring image captured
```

A simple Year 1 versus Year 4 comparison may miss the temporary loss.

The system therefore uses multi-date time-series analysis rather than only two snapshots.

---

### 6. Reference-Area Comparison

The project area is compared with a similar non-project region.

Reference matching may use:

- historical vegetation,
- rainfall,
- soil,
- elevation,
- slope,
- temperature,
- distance from roads,
- distance from settlements,
- historical deforestation,
- forest-management conditions,
- and land-use history.

The objective is to estimate what might have happened without the project.

---

### 7. Carbon Additionality Assessment

A simplified analytical structure is:

```text
Potentially attributable carbon
=
Post-project project-area carbon
- Pre-project project-area carbon
- Change in reference area
- Applicable deductions
```

This is a simplified framework. Final calculations must follow the selected carbon methodology.

---

### 8. Biomass and Carbon Estimation

The system estimates:

1. above-ground biomass,
2. below-ground biomass where applicable,
3. total biomass,
4. carbon fraction,
5. carbon stock,
6. carbon-dioxide equivalent.

A simplified sequence is:

```text
Satellite and field variables
          |
          v
Biomass estimate
          |
          v
Carbon stock
          |
          v
CO2 equivalent
```

---

### 9. Audit and Evidence Generation

The platform generates:

- before-and-after maps,
- project-versus-reference trends,
- canopy-loss alerts,
- regrowth alerts,
- biomass estimates,
- carbon estimates,
- uncertainty ranges,
- confidence scores,
- field-verification tasks,
- methodology-based explanations,
- and an auditable review history.

---

## High-Level Architecture

```text
Historical Satellite Imagery
Current Satellite Imagery
Sentinel-1 Radar
Project Boundary
Reference-Area Boundary
Plantation Records
Field Inventory
Environmental Data
Carbon Methodology
          |
          v
Data Ingestion and Quality Control
          |
          v
Cloud, Shadow and Seasonal Correction
          |
          v
Image Alignment and Spatial Harmonisation
          |
          v
Pre-Project Baseline Model
          |
          v
Land-Cover and Canopy Segmentation
          |
          v
Time-Series Forest Change Detection
          |
          v
Project vs Reference-Area Comparison
          |
          v
Biomass and Carbon Estimation
          |
          v
Additionality and Uncertainty Analysis
          |
          v
Anomaly and Risk Detection
          |
          v
Generative AI Evidence and Reporting
          |
          v
Human Expert Verification
          |
          v
Dashboard, Alerts and Audit Pack
```

---

## Recommended Dataset Stack

### Core Free Datasets

| Project module | Recommended datasets |
|---|---|
| Optical monitoring | Sentinel-2 Surface Reflectance |
| All-weather disturbance monitoring | Sentinel-1 SAR |
| Historical baseline | Landsat Collection 2 Level-2 |
| Land-cover support | Dynamic World |
| Fixed land-cover reference | ESA WorldCover |
| Historical forest loss | Hansen Global Forest Change |
| Biomass calibration | GEDI L4A and canopy products |
| Canopy-height support | ICESat-2 |
| Terrain | NASADEM or SRTM |
| Rainfall | CHIRPS |
| Climate | ERA5-Land |
| Soil | SoilGrids |
| India-specific support | Bhuvan and VEDAS |
| Ground truth | Project and field forest inventory |

### High-Resolution Validation

Use selectively:

- Planet tropical forest mosaics,
- commercial high-resolution optical imagery,
- drone orthomosaics,
- airborne lidar,
- commercial SAR.

The recommended strategy is:

```text
Free satellite screening
          |
          v
Risk-area identification
          |
          v
High-resolution imagery only for uncertain zones
          |
          v
Field or drone verification
```

---

## Technology Stack

### Programming and Analysis

- Python
- SQL
- pandas
- NumPy
- SciPy
- Statsmodels
- Jupyter Notebook
- Google Colab

### Geospatial Processing

- Google Earth Engine
- GeoPandas
- Rasterio
- GDAL
- Shapely
- PyProj
- Xarray
- rioxarray
- QGIS
- SNAP

### Remote Sensing

- Sentinel-2
- Sentinel-1
- Landsat
- GEDI
- ICESat-2
- Hansen Global Forest Change
- Dynamic World
- ESA WorldCover
- CHIRPS
- ERA5-Land
- SoilGrids
- NASADEM

### Machine Learning

- scikit-learn
- XGBoost
- LightGBM
- PyTorch
- TensorFlow
- OpenCV
- U-Net
- DeepLab
- Mask R-CNN
- Siamese change-detection networks
- Isolation Forest
- Autoencoders

### Generative AI

- Large language model API or self-hosted model
- LangChain
- LlamaIndex
- Retrieval-Augmented Generation
- Vector database
- Structured-output generation
- Citation and evidence linking
- Prompt and response evaluation
- Guardrails

### Backend and APIs

- FastAPI
- Django or Flask
- REST APIs
- Celery
- Background task queues
- WebSockets

### Front End

- React
- Next.js
- TypeScript
- Leaflet
- Mapbox-compatible map viewers
- Plotly
- Responsive dashboard components

### Storage and Databases

- PostgreSQL
- PostGIS
- Object storage
- Vector database
- Model registry
- Data versioning

### Cloud and MLOps

- AWS, Azure, or Google Cloud
- Docker
- Kubernetes
- GitHub Actions
- MLflow
- DVC
- Airflow or Prefect
- Centralised logging
- Model monitoring
- Drift monitoring

---

## Functional Modules

### 1. Project Registration

Capture:

- project name,
- project ID,
- owner,
- country and region,
- project type,
- project start date,
- crediting period,
- monitoring schedule,
- project boundary,
- reference-area boundary,
- plantation date,
- species,
- density,
- land-use history,
- methodology,
- field-data availability.

---

### 2. Data Ingestion

The platform should ingest:

- satellite imagery,
- radar imagery,
- project polygons,
- reference polygons,
- elevation,
- rainfall,
- temperature,
- soil,
- roads and settlements,
- plantation records,
- field plots,
- fire records,
- harvesting records,
- and methodology documents.

---

### 3. Image Preprocessing

Required operations include:

- reprojection,
- clipping,
- cloud masking,
- shadow masking,
- noise filtering,
- atmospheric correction where needed,
- image co-registration,
- temporal compositing,
- band harmonisation,
- resolution harmonisation,
- seasonal normalisation.

---

### 4. Baseline Generation

The baseline module should:

- identify pre-project vegetation,
- classify land cover,
- map canopy,
- estimate baseline biomass,
- estimate baseline carbon,
- calculate uncertainty,
- and store a versioned baseline.

---

### 5. Land-Cover and Canopy Analysis

The system should classify:

- forest,
- plantation,
- scrub,
- grassland,
- bare land,
- agriculture,
- water,
- and built-up area.

It should also identify canopy density and changes.

---

### 6. Change Detection

The system should classify:

- no material change,
- new vegetation,
- canopy growth,
- canopy loss,
- fire,
- harvesting,
- degradation,
- soil exposure,
- temporary clearing,
- and regrowth.

---

### 7. Reference-Area Matching

Reference areas should be matched using:

- historical vegetation,
- climate,
- rainfall,
- soil,
- elevation,
- slope,
- land-use history,
- road access,
- settlement pressure,
- and deforestation history.

---

### 8. Additionality Analysis

The system should compare:

- pre-project trend,
- post-project trend,
- project-area change,
- reference-area change,
- and project-attributable difference.

Potential statistical methods include:

- difference-in-differences,
- matched controls,
- synthetic controls,
- change-point analysis,
- regression with environmental controls.

---

### 9. Biomass Estimation

Potential modelling inputs include:

- Sentinel-2 bands and indices,
- Sentinel-1 backscatter,
- GEDI biomass labels,
- canopy height,
- terrain,
- rainfall,
- soil,
- field inventory,
- species,
- diameter at breast height,
- and tree height.

---

### 10. Carbon Accounting

The system should support configurable equations for:

- biomass,
- carbon fraction,
- CO2 equivalent,
- baseline,
- leakage,
- uncertainty,
- reversals,
- permanence,
- and methodology-specific deductions.

---

### 11. Risk and Anomaly Detection

The system should flag:

- suspicious clearing,
- sudden canopy loss,
- fire,
- harvesting,
- rapid regrowth,
- repeated disturbance,
- low-confidence areas,
- missing imagery,
- and inconsistent project records.

---

### 12. Generative AI Reporting

Generative AI should be used to:

- summarise findings,
- explain maps and alerts,
- answer methodology questions,
- produce audit-ready narratives,
- create field-inspection summaries,
- and cite supporting evidence.

Generative AI should not independently approve carbon credits.

---

## User Roles

| User role | Main responsibility |
|---|---|
| Project Administrator | Create projects, manage boundaries, users, and configuration |
| Forestry Expert | Validate species, plantation design, and field assumptions |
| Remote-Sensing Analyst | Review imagery, preprocessing, and change maps |
| Carbon Specialist | Configure methodology and carbon rules |
| AI Engineer | Build, test, deploy, and monitor models |
| Geospatial Engineer | Manage raster, vector, projection, and map workflows |
| Data Engineer | Build data pipelines and storage |
| Field Surveyor | Upload tree measurements and evidence |
| Auditor or Verifier | Review evidence, uncertainty, and approval history |
| Business Stakeholder | Review project performance and risks |
| System Administrator | Manage access, security, infrastructure, and reliability |

---

## Repository Structure

```text
.
├── README.md
├── notebooks/
│   ├── 01_sentinel2_eda.ipynb
│   ├── 02_pre_project_baseline.ipynb
│   ├── 03_reference_area_matching.ipynb
│   ├── 04_change_detection.ipynb
│   ├── 05_biomass_estimation.ipynb
│   └── 06_additionality_analysis.ipynb
├── src/
│   ├── data_ingestion/
│   ├── preprocessing/
│   ├── baseline/
│   ├── land_cover/
│   ├── change_detection/
│   ├── reference_matching/
│   ├── biomass/
│   ├── carbon_accounting/
│   ├── anomaly_detection/
│   ├── genai_reporting/
│   └── api/
├── app/
│   ├── frontend/
│   └── backend/
├── configs/
│   ├── project_config.yaml
│   ├── methodology_rules.yaml
│   └── model_config.yaml
├── data/
│   ├── raw/
│   ├── interim/
│   ├── processed/
│   └── field_inventory/
├── models/
├── reports/
├── tests/
├── docker/
├── requirements.txt
├── environment.yml
├── .env.example
├── .gitignore
└── LICENSE
```

---

## Current Implemented Component

The currently implemented notebook performs exploratory data analysis on Sentinel-2 Surface Reflectance.

It includes:

- Earth Engine authentication,
- configurable area of interest,
- date filtering,
- scene-level cloud filtering,
- Cloud Score+ integration,
- Scene Classification Layer masking,
- reflectance scaling,
- median-composite generation,
- NDVI, EVI, NDMI, NBR, NDWI, SAVI, and BSI,
- scene metadata analysis,
- pixel-level descriptive statistics,
- missing-value analysis,
- outlier analysis,
- correlation analysis,
- monthly time-series analysis,
- vegetation-condition segmentation,
- area calculation,
- CSV export,
- GeoTIFF export.

---

## Installation

### Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/ai-carbon-additionality-monitoring.git
cd ai-carbon-additionality-monitoring
```

### Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it:

```bash
# Windows
.venv\Scripts\activate

# macOS/Linux
source .venv/bin/activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

Example minimum requirements:

```text
earthengine-api
geemap
pandas
numpy
matplotlib
geopandas
rasterio
shapely
pyproj
scikit-learn
xgboost
fastapi
uvicorn
pydantic
```

---

## Google Earth Engine Setup

1. Create or select a Google Cloud project.
2. Enable Earth Engine access.
3. Register the project for commercial or non-commercial use as appropriate.
4. Authenticate with the same Google account.
5. Replace the placeholder project ID.

Example:

```python
import ee

EE_PROJECT_ID = "YOUR_GOOGLE_CLOUD_PROJECT_ID"

ee.Authenticate()
ee.Initialize(project=EE_PROJECT_ID)
```

Do not commit access tokens, service-account keys, or secrets.

---

## Configuration

Example project configuration:

```yaml
project:
  name: "Carbon Monitoring Pilot"
  start_date: "2025-01-01"
  end_date: "2025-12-31"
  methodology: "CONFIGURE_SELECTED_METHODOLOGY"

remote_sensing:
  max_scene_cloud_percent: 80
  cloud_score_threshold: 0.60
  analysis_scale_m: 20
  sample_pixels: 5000

monitoring:
  monthly_composites: true
  detect_canopy_loss: true
  detect_regrowth: true
  use_reference_area: true

carbon:
  include_above_ground_biomass: true
  include_below_ground_biomass: false
  uncertainty_deduction: true
```

---

## How to Run

### Notebook Workflow

```text
notebooks/01_sentinel2_eda.ipynb
```

Run the notebook from top to bottom in Google Colab or Jupyter.

### API Workflow

A future FastAPI service may be started using:

```bash
uvicorn src.api.main:app --reload
```

### Front-End Workflow

A future React or Next.js interface may be started using:

```bash
npm install
npm run dev
```

---

## Expected Outputs

### Baseline Outputs

- pre-project land-cover map,
- pre-existing canopy map,
- baseline biomass,
- baseline carbon stock,
- baseline uncertainty,
- approved baseline version.

### Monitoring Outputs

- current vegetation map,
- canopy-growth map,
- canopy-loss map,
- regrowth map,
- disturbance alerts,
- plantation-performance indicators.

### Comparative Outputs

- project-area trend,
- reference-area trend,
- project-versus-reference difference,
- additionality estimate,
- reference-area similarity score.

### Carbon Outputs

- gross biomass change,
- gross carbon-stock change,
- reference-adjusted change,
- uncertainty deduction,
- methodology deductions,
- indicative attributable carbon.

### Risk Outputs

- possible cutting,
- possible fire,
- degradation,
- suspicious regrowth,
- missing observations,
- low-confidence zones,
- areas requiring field verification.

### Reports

- technical monitoring report,
- project summary,
- audit evidence pack,
- downloadable maps,
- downloadable tables,
- field-verification task list,
- Generative AI explanation,
- approval history.

---

## Success Metrics

### Data Quality Metrics

- cloud-free observation percentage,
- temporal coverage,
- field-data completeness,
- spatial alignment error,
- valid monitoring dates.

### Model Metrics

For classification and segmentation:

- precision,
- recall,
- F1 score,
- intersection over union,
- overall accuracy,
- class-wise accuracy.

For biomass regression:

- mean absolute error,
- root mean squared error,
- R-squared,
- percentage estimation error.

For event detection:

- true disturbance events detected,
- false-alert rate,
- missed-event rate,
- detection delay.

### Business Metrics

- reduction in manual review time,
- reduction in field visits,
- monitoring cost per hectare,
- number of high-risk zones detected,
- report-generation time,
- expert-confirmed alert rate,
- reduction in unsupported carbon claims.

---

## Constraints and Limitations

### Spatial Resolution

Sentinel-2 cannot reliably identify every individual tree in mixed or dense landscapes.

### Cloud Cover

Optical imagery may be unavailable for long periods.

### Mixed Pixels

One pixel may include trees, grass, soil, water, and buildings.

### Seasonal Variation

Rainfall and vegetation cycles may resemble project-driven change.

### Field-Data Dependency

Certification-grade biomass requires field calibration.

### Reference-Area Bias

A poor control region can invalidate additionality estimates.

### Causal Attribution

Change detection is not the same as proving project causality.

### Methodology Variation

Different carbon standards have different rules.

### Regulatory Acceptance

AI outputs may not be accepted without transparent evidence and expert validation.

### Model Generalisation

A model trained in one forest type may not generalise to another.

### Explainability

Auditors require maps, evidence, assumptions, and reproducible calculations.

---

## Responsible AI and Carbon Integrity

The system must follow these principles:

- no automatic carbon-credit issuance,
- no unsupported claims,
- evidence-linked conclusions,
- explicit uncertainty,
- human approval,
- versioned models,
- traceable source data,
- clear methodology mapping,
- field verification for high-risk cases,
- independent auditability.

The correct positioning is:

```text
Geospatial AI detects change.
Statistical analysis estimates additionality.
Biomass models estimate carbon.
Generative AI explains the evidence.
Qualified experts make the final decision.
```

---

## Development Roadmap

### Phase 1: Discovery and Requirements

- select methodology,
- define users,
- confirm data,
- finalise project and reference boundaries,
- define success criteria,
- create risk register.

### Phase 2: Baseline

- collect historical imagery,
- generate land-cover baseline,
- map pre-existing vegetation,
- estimate baseline biomass,
- create baseline report.

### Phase 3: Change Detection

- generate post-project composites,
- detect vegetation gain and loss,
- detect cutting and regrowth,
- create alerts.

### Phase 4: Reference-Area Analysis

- identify comparable control regions,
- compare historical trends,
- calculate project-versus-reference difference.

### Phase 5: Biomass and Carbon

- integrate field inventory,
- add GEDI,
- train biomass models,
- estimate carbon and uncertainty.

### Phase 6: Generative AI Reporting

- ingest methodology documents,
- build a retrieval system,
- generate evidence-linked reports,
- add guardrails.

### Phase 7: Production Deployment

- deploy APIs,
- deploy dashboard,
- schedule monitoring,
- add role-based access,
- implement MLOps,
- enable audit logging.

---

## Interview-Ready Project Explanation

> This project is an AI-powered geospatial monitoring system for carbon additionality, plantation performance, and forest-change detection. It combines Sentinel-2 optical imagery, Sentinel-1 radar, Landsat historical data, GEDI biomass observations, field inventory, environmental variables, and project records. The system establishes a pre-project baseline, identifies existing vegetation, detects new canopy growth, monitors cutting and regrowth, compares the project area with a matched reference region, estimates biomass and carbon change, and generates auditable evidence. Computer vision and time-series models detect what changed, statistical analysis estimates what may be attributable to the project, biomass models estimate carbon, Generative AI explains the evidence, and domain experts make the final decision.

---

## Current Project Status

```text
Completed:
- Project discovery
- Business context
- Functional scope
- Dataset research
- Sentinel-2 exploratory data analysis
- Descriptive analytics
- Spectral-index analysis
- Documentation

In progress:
- Pre-project baseline
- Reference-area matching
- Time-series change detection
- Additionality analysis
- Biomass modelling
- Production architecture
```

---

## Future Enhancements

- automated reference-area recommendation,
- Sentinel-1 and Sentinel-2 fusion,
- deep-learning canopy segmentation,
- field mobile application,
- drone-data ingestion,
- carbon-methodology rule engine,
- uncertainty propagation,
- fraud-risk scoring,
- alert prioritisation,
- digital audit trail,
- project portfolio dashboard,
- multilingual Generative AI reporting.

---

## Contributing

Contributions are welcome in:

- geospatial preprocessing,
- remote sensing,
- change detection,
- biomass estimation,
- causal analysis,
- carbon accounting,
- Generative AI,
- dashboards,
- testing,
- documentation.

Recommended contribution process:

```bash
git checkout -b feature/your-feature
git add .
git commit -m "Add your feature"
git push origin feature/your-feature
```

Then open a pull request with:

- problem solved,
- data used,
- methodology,
- validation,
- limitations,
- screenshots or outputs,
- expected business impact.

---

## Security

Do not commit:

- `.env` files,
- Earth Engine tokens,
- service-account keys,
- cloud credentials,
- private project boundaries,
- confidential field data,
- customer or landowner information.

Use:

- environment variables,
- secret managers,
- role-based access,
- encrypted storage,
- audit logs.

---

## License

Add the appropriate licence before public or commercial release.

For open educational use, consider:

- MIT,
- Apache 2.0,
- BSD 3-Clause.

Dataset usage remains subject to the terms of the original providers.

---

## Acknowledgements

- European Space Agency
- Copernicus Programme
- Google Earth Engine
- NASA
- USGS
- GEDI mission
- ISRO
- Open-source Python and geospatial communities
- Forestry, carbon-accounting, remote-sensing, and AI domain experts

---

## Disclaimer

This project is a research, learning, monitoring, and decision-support system.

It does not independently:

- issue carbon credits,
- certify carbon removals,
- replace accredited validation or verification,
- provide legal approval,
- guarantee carbon-market eligibility.

Final claims require:

- an approved methodology,
- field inventory,
- uncertainty assessment,
- expert review,
- independent verification,
- registry acceptance.

---

## Project Title

**AI-Powered Carbon Additionality, Plantation Monitoring and Forest Change Detection System**
