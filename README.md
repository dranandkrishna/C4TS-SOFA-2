# C4TS-SOFA-2

**Centre for Trauma Sciences (C4TS) dataset for the analysis of Multiple Organ Dysfunction Syndrome (MODS) in major trauma patients using the SOFA-2 score.**

## Overview

This repository holds a patient-level dataset from major trauma patients. It records daily organ dysfunction scores using both the original **Sequential Organ Failure Assessment (SOFA)** score and the updated **SOFA-2** score, with each patient's injury severity, early resuscitation and outcome.

The dataset is designed to:

- describe how often MODS occurs after major trauma and how it develops over time
- compare the original SOFA with SOFA-2 for detecting and grading organ dysfunction
- look at how injury pattern, coagulopathy and early resuscitation relate to later organ failure and outcome

## Contents

| File | Description |
|---|---|
| `C4TS SOFA-2.xlsx` | The main dataset: one sheet, one row per patient (2,223 patients, 625 variables) |
| `README.md` | This file |

## Cohort at a glance

| Characteristic | Value |
|---|---|
| Patients | 2,223 |
| Injury Severity Score (ISS) | median 25 (range 0–75) |
| Mechanism (where recorded) | 673 blunt, 201 penetrating |
| Traumatic brain injury | 1,023 (46%) |
| Major haemorrhage protocol activated | 789 |
| 28-day mortality | 392 (17.6%) |
| Hospital length of stay | median 21 days |

## Variable groups

Variable names use the suffix `_dN` for study day *N*, from day 0 (day of injury) to day 28.

**Injury characteristics**
- `inj_type`: blunt or penetrating
- `iss`: Injury Severity Score
- `*_ais`: Abbreviated Injury Scale by body region (head/neck, face, thorax, abdomen/pelvis, extremity, external)
- `tbi`: traumatic brain injury (0/1)

**Admission physiology and coagulation**
- `hr`, `sbp`: heart rate and systolic blood pressure
- `gcs`, `gcs_e`, `gcs_v`, `gcs_m`, `gcs_tube`: Glasgow Coma Scale and its components
- `bd`: base deficit
- `inr`, `plt_c`, `fbg`: INR, platelet count, fibrinogen
- `extem_a5`, `fibtem_a5`, `plttem_a5`: ROTEM viscoelastic clot amplitudes at 5 minutes

**Resuscitation**
- `mhp_act`, `mhp_act_loc`: whether the major haemorrhage protocol was activated, and where
- `prbc_24h`, `ffp_24h`: red cells and plasma given in the first 24 hours
- `*_inj_12h` / `*_12h_24h`: volumes given from injury to 12 hours, and from 12 to 24 hours, for each fluid and blood product: crystalloid (`csl`), colloid (`col`), hypertonic saline (`hts`), whole blood (`wb`), PRBC, FFP, Octaplas (`octap`), lyophilised plasma (`lyop`), platelets (`plt`), cryoprecipitate (`cryo`) and other fluids

**Daily organ function and scores (day 0 to day 28)**
- `gcs_dN`, `map_dN`, `pf_dN`, `bili_dN`, `plts_dN`, `cr_dN`: raw values used for scoring (GCS, mean arterial pressure, PaO₂/FiO₂, bilirubin, platelets, creatinine)
- Original SOFA organ sub-scores: `resp_score_dN`, `cvs_score_dN`, `cns_score_dN`, `haem_score_dN`, `hep_score_dN`, `ren_score_dN`
- SOFA-2 organ sub-scores: `resp2_score_dN`, `cvs2_score_dN`, `cns2_score_dN`, `haem2_score_dN`, `hep2_score_dN`, `ren2_score_dN`
- Total scores: `sofa_complete_dN` / `sofa2_complete_dN` (all six organ systems available) and `sofa_any_dN` / `sofa2_any_dN` (calculated from whichever components are available)
- `*_max_dN`: maximum score reached up to day *N*
- `scores_sofa_count`: number of days with SOFA data

**MODS**
- `mods_dN` / `mods2_dN`: MODS present on day *N* (by SOFA and by SOFA-2)
- `mods_yn` / `mods2_yn`: MODS at any point during the stay
- `days_in_mods` / `days_in_mods2`: number of days in MODS

**Outcomes and resource use**
- `death_28d`: death within 28 days
- `cc_death`: death in critical care
- `discharge_loc`: where the patient went on discharge
- `los`, `los_calc`, `los_icu`, `los_hdu`, `los_cc`: length of stay in hospital, ICU, HDU and critical care overall
- `vasop_days`, `vent_days`, `rrt_days`: days on vasopressors, mechanical ventilation and renal replacement therapy

## About SOFA-2

SOFA-2 updates the original 1996 SOFA score to match current critical care practice. It covers six organ systems (brain, respiratory, cardiovascular, liver, kidney, haemostasis), each scored 0–4, for a total of 0–24. Changes from the original include:
- counting advanced respiratory support and ECMO in the respiratory score
- revised vasopressor bands and mechanical circulatory support in the cardiovascular score
- urine output and renal replacement therapy criteria in the kidney score
- updated platelet thresholds

> Moreno R, et al. *Development and Validation of the Sequential Organ Failure Assessment (SOFA)-2 Score.* JAMA. 2025.

## Data notes

- Missing values are left as empty cells. Some fields use `[ND]` to mean "not documented".
- The dataset contains no direct patient identifiers.
- This dataset is for research use only and must not be used to make clinical decisions.

## Citation

If you use this dataset, please cite the Centre for Trauma Sciences (C4TS), Blizard Institute, Queen Mary University of London, and any related publication.

## Contact

Centre for Trauma Sciences (C4TS), Blizard Institute, Queen Mary University of London.
