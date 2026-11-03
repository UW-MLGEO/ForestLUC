# ForestLUC

Project repository for the Aboveground Carbon Stock Density Prediction Model. 
Global Aboveground Biomass (AGB) Carbon Density Maps is available for the year 2010 completed by NASA. This will be used as the observed variable, and referred to as the "observed data". 
This project aims to identify various remote sensing signals and relevant data that are suitable to develop predictor variables to quantify the AGB Carbon Density globally for the year 2010 and beyond. 
A linear regression prediction model will be created using various predictor variables using remote sensing signals. This model will then be compared to our observed data to evaluate accuracy of the model. This will serve as the within domain application. 
The accuracy of the prediction model as well as the relevance of the predictor variables will be further evaluated by modifying the list of variables that goes into the prediction model. 
The prediction model with the highest accuracy will be used to develop a time-series data covering AGB Carbon Density globally from 2011 to 2021. This will serve as the out-of-domain application. 

To test for replicability, the model will also be fitted on another dataset by WHRC on Pantropical National Level Carbon Stock Dataset for the year 2012. The same workflow will be applied to this dataset as well. 

## How to run

This repository uses Pixi to manage the course environment.

Install the environment:

```bash
pixi install
```

Run the smoke test:

```bash
pixi run smoke
```

A successful test ends with:

```text
smoke test passed
```

## Reproducibility check

From a fresh clone, run:

```bash
git clone https://github.com/UW-MLGEO/ForestLUC.git
cd ForestLUC
pixi install
```

The smoke test checks that the required Python environment works and performs a
small numerical calculation. A successful run ends with:

```text
smoke test passed
```

## Working with notebooks

Start JupyterLab from the repository root:

```bash
pixi run lab
```

Open the forwarded port 8888 in Codespaces. Run notebooks from top to bottom
after restarting the kernel. Save notebooks before committing them.

## Git workflow

Before starting work:

```bash
git pull
```

After making changes:

```bash
git status
git add FILE_NAME
git commit -m "Describe the change"
git push
```

## Data and provenance

license_and_citations:
  - dataset: FAO GAUL Simplified 500m 2025 level1
    license: CC-BY-4.0
    citation: FAO. 2025. Global Administrative Unit Layers (GAUL). https://data.apps.fao.org
  - dataset: NASA ORNL Global Aboveground and Belowground Biomass Carbon Density Maps, v1
    license: Public domain
    citation: Spawn et al. 2020. ORNL DAAC. https://doi.org/10.3334/ORNLDAAC/1763
  - dataset: MODIS/061/MOD13Q1
    license: No restrictions on subsequent use, sale, or redistribution
    citation: NASA LP DAAC. MOD13Q1.061. https://doi.org/10.5067/MODIS/MOD13Q1.061
  - dataset: MODIS/061/MOD15A2H
    license: No restrictions on subsequent use, sale, or redistribution
    citation: NASA LP DAAC. MOD15A2H.061. https://doi.org/10.5067/MODIS/MOD15A2H.061
  - dataset: MODIS/061/MCD12Q1
    license: No restrictions on subsequent use, sale, or redistribution
    citation: NASA LP DAAC. MCD12Q1.061. https://doi.org/10.5067/MODIS/MCD12Q1.061
  - dataset: USGS/GTOPO30
    license: Public domain; no restrictions on use
    citation: USGS EROS Center. 2023. Global Topographic 30 Arc-Second Digital Elevation Model: Released 1996. https://doi.org/10.5066/F7DF6PQS.
  - dataset: WHRC/biomass/tropical
    license: Scientific, conservation, and educational use; see provider terms
    citation: Baccini et al. 2012. Nature Climate Change. https://doi.org/10.1038/NCLIMATE1354
    role: Separate 2012 target dataset; aboveground live woody biomass, not equivalent to ORNL carbon density.

variables:
  agb_carbon_mg_ha: {role: target, source_band: agb, units: Mg C ha-1, dtype: float32}
  agb_uncertainty_mg_ha: {role: target_uncertainty, source_band: agb_uncertainty, units: Mg C ha-1, dtype: float32}
  ndvi: {role: predictor, source_band: NDVI, units: dimensionless, dtype: float32, scale_factor_applied: 0.0001}
  evi: {role: predictor, source_band: EVI, units: dimensionless, dtype: float32, scale_factor_applied: 0.0001}
  fpar_fraction: {role: predictor, source_band: Fpar_500m, units: fraction, dtype: float32, scale_factor_applied: 0.01}
  lai_m2_m2: {role: predictor, source_band: Lai_500m, units: m2 m-2, dtype: float32, scale_factor_applied: 0.1}
  landcover_igbp: {role: predictor, source_band: LC_Type1, units: IGBP class code, dtype: int16}
  elevation_m: {role: predictor, source_band: elevation, units: m, dtype: float32}
  whrc_live_woody_biomass_mg_ha: {role: alternate_label, source_band: Mg, units: Mg dry live woody biomass ha-1, dtype: float32}
  grid_col: {role: spatial_index, units: ORNL reference-grid pixel, dtype: int32}
  grid_row: {role: spatial_index, units: ORNL reference-grid pixel, dtype: int32}
  longitude: {role: coordinate, units: degrees_east, dtype: float64}
  latitude: {role: coordinate, units: degrees_north, dtype: float64}
  label_year: {role: metadata, units: year, dtype: int16}
  predictor_year: {role: metadata, units: year, dtype: int16}
  spatial_block_id: {role: partition_group, units: none, dtype: string}
  split: {role: partition, allowed_values: [train, validation, test], dtype: string}
