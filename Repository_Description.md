# Title

Code and data for: Thermal constraints rather than resource limitations shrink mammalian home ranges under climate change

# Description

This repository contains the R code, source inputs, analysis-ready datasets and results supporting the study *Thermal constraints rather than resource limitations shrink mammalian home ranges under climate change*. The analyses include phylogenetic generalized least squares, linear mixed-effects models, multilevel structural equation modelling and future home-range projections under four shared socioeconomic pathways.

The code and data are distributed together through this GitHub repository.

The repository is organized into three archives:

- **Analysis_Code.zip:** R analysis and preparation scripts, package installation instructions, validation scripts and the official lavaan 0.6-20 source archive.
- **Analysis_Data_and_Results.zip:** processed model inputs, fitted model objects, coefficient and model-comparison tables, scenario projections, supplementary tables and validation reports. The files `msem_multilevel_v3_results.csv`, `SEM_path_coefficients.csv` and `SEM_fit_measures.csv` are included under `analysis_data/results/tables/`.
- **Source_Data_and_Environmental_Inputs.zip:** original HomeRange, PanTHERIA, EltonTraits, complete mammalian phylogeny and annual NPP inputs, together with derived current and future environmental point inputs and source metadata.

Extract all three archives into the same parent directory, preserving the `code`, `analysis_data` and `raw_data` directory names. The code README documents three workflows: regeneration from saved results, refitting from analysis-ready inputs, and reconstruction from source tables and environmental point inputs. Validation used R 4.4.2 and lavaan 0.6-20.

The default reconstruction uses the supplied environmental point tables. Optional spatial re-extraction is supported after separately obtaining the official global rasters. The source-data package records download locations, versions, resolution, periods and original SHA256 values for WorldClim 2.1 baseline climate at 30 arc-seconds, continuous Human Footprint 2009 at 1 km, and BCC-CSM2-MR CMIP6 bioclimatic projections at 2.5 arc-minutes for four SSPs and four future periods. The global raster files are not bundled in these archives. Dataset citations and preprocessing rules are provided in the package documentation.

A previous independent reconstruction from the supplied source tables and environmental point inputs passed all 111 preparation checks and all 15 core scientific result checks. Comparisons across 31 result tables and 734 fields in that recorded run found a maximum numeric difference of 2.240844e-9, within the 1e-8 result tolerance. Locality-text decoding differences are documented separately. Reports from an earlier successful reconstruction using the original local rasters are also included. Fresh downloads of those global rasters were outside that validation run. Figures were not regenerated during the point-input validation; the plotting code and scientific plotting inputs were unchanged, and earlier figure verification is retained separately.

The current statistical-summary export reports Pearson correlations for species-level body mass and trophic level, and Spearman correlations for warming summaries across latitude zones and biogeographic regions. Climate-class outputs are descriptive summaries. The updated export was regenerated from archived inputs and independently reconstructed inputs; all 22 result checks passed in each run. Its validation report is in `analysis_data/verification/trait_correlation_validation.md`. Historical full-workflow reports retain their earlier statistical-summary snapshot; the current export and its checks supersede those summary rows. Source inputs, fitted models and projections are unchanged.

Each archive includes an individual-file manifest with file sizes and SHA256 checksums. The repository README provides extraction instructions and the paths to the workflow documentation within the extracted packages.

# Keywords

Mammalian home range; climate change; body mass; trophic level; phylogenetic generalized least squares; linear mixed-effects models; multilevel structural equation modelling; shared socioeconomic pathways; reproducible research; R
