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

When data are added, the README will record the source URL or DOI, version, retrieval date,
units, and processing steps. Raw data will remain unchanged, and processed
data will be written separately.
