# Mammalian home-range analysis: code and data

This repository provides the code and data for *Thermal constraints rather than resource limitations shrink mammalian home ranges under climate change*.

The analysis code, analysis-ready data, source inputs and results are distributed together in this GitHub repository.

## Download and extract

Download the three ZIP files and extract them into the same parent directory. Each archive contains its own top-level directory; preserve those directory names.

| Archive | Contents | Extracted directory |
|---|---|---|
| [Analysis_Code.zip](Analysis_Code.zip) | R scripts, package installer, workflow instructions, validation scripts and the official lavaan 0.6-20 source archive | `code/` |
| [Analysis_Data_and_Results.zip](Analysis_Data_and_Results.zip) | Analysis-ready inputs, fitted models, coefficients, projections, supplementary tables and verification reports | `analysis_data/` |
| [Source_Data_and_Environmental_Inputs.zip](Source_Data_and_Environmental_Inputs.zip) | Original HomeRange, trait, phylogeny and annual NPP inputs; derived current and future environmental point tables; source and checksum records | `raw_data/` |

The extracted layout is:

```
repository/
  code/
  analysis_data/
  raw_data/
```

Each extracted package contains `manifest_sha256.csv`, listing its individual files, sizes and SHA256 checksums.

## Run the analyses

R 4.4.2 was used for validation. After extracting the archives, open R in the `code` directory and follow the instructions in `code/README.md`. Its package installer uses a project-local library, and the official lavaan 0.6-20 source archive is supplied under `code/vendor/`.

Three workflows are documented in that README:

1. **Published-results workflow:** use saved models and results to regenerate figures and inspect the numerical outputs.
2. **Refit from analysis-ready data:** re-estimate PGLS, LMM and multilevel SEM models and recompute projections and summaries.
3. **Reconstruct from source tables and environmental points:** repeat record filtering, trait integration, phylogeny preparation and NPP aggregation, join the supplied environmental point inputs, and refit the analyses.

The source-data workflow defaults to the supplied point tables. Global environmental TIFFs are obtained separately for optional spatial re-extraction. After extraction, `raw_data/README.md` explains retrieval and placement, and `raw_data/external_raster_sources.csv` records official sources, product versions, spatial resolutions, periods and the original raster SHA256 values. These include WorldClim 2.1 baseline climate at 30 arc-seconds, continuous Human Footprint 2009 at 1 km, and BCC-CSM2-MR CMIP6 bioclimatic projections at 2.5 arc-minutes for four SSPs and four periods. The scripts do not automatically download these global rasters.

## Key SEM files

The following files are supplied in `analysis_data/results/tables/`:

- `msem_multilevel_v3_results.csv`
- `SEM_path_coefficients.csv`
- `SEM_fit_measures.csv`

Canonical result filenames, compatibility aliases and the corresponding fitted model objects are described in the code and analysis-data READMEs.

## Verification

A previous independent reconstruction started from a fresh code directory and used only the supplied source-data and environmental point inputs. It passed **111 preparation checks** and **15 core scientific result checks**. Across **31 result tables and 734 compared fields** in that recorded run, the maximum numeric difference from the reference results was **2.240844e-9**, within the **1e-8** result tolerance. Descriptive locality-text decoding differences are recorded separately. After extraction, full details are in `analysis_data/verification/light_validation_summary.txt`.

The current statistical-summary export uses Pearson correlation for species-level body mass and trophic level, and Spearman correlation for grouped warming summaries across latitude zones and biogeographic regions. Climate-class outputs are descriptive summaries. The updated summary was regenerated from archived inputs and independently reconstructed inputs, with **22 result checks** passing in each run. See `analysis_data/verification/trait_correlation_validation.md` after extraction. Earlier comparison reports retain their historical statistical-summary snapshot; the current export and its checks supersede those summary rows. Source inputs, fitted models and projections are unchanged.

Earlier reconstruction using the original local environmental rasters also passed the recorded validation checks; its reports are retained in `analysis_data/verification/RAW_VALIDATION.md`. Downloading those global rasters again from the public sources was outside the current validation run. Figures were not regenerated during the current point-input validation; the plotting code and scientific plotting inputs were unchanged, and earlier figure checks are retained separately.

After extraction, dataset citations and input provenance are in `raw_data/DATA_SOURCES.md`. Preparation rules are in `code/RAW_RECONSTRUCTION_NOTES.md`.
