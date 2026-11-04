# Deep-Sea Hydrothermal Vent & Chemosynthetic Extremophile Biomass Tracker

This repository contains the Python generation script and database schema for the **Abyssal Hydrothermal & Extremophile Specimen Database** (`abyssal_hydrothermal_lab.db`), developed for the SQL & Data Science Database Assessment by **Sai Jayanth Keerthipati** (Student ID: `25023235`).

## Repository Contents

* `generate_database.py` (or Jupyter Notebook): The end-to-end Python script utilizing `sqlite3`, `random`, and `numpy` to programmatically build the database, enforce relational constraints, inject realistic missing values/duplicates, and populate 1,200+ records.

* `abyssal_hydrothermal_lab.db`: The compiled SQLite database file outputted by the execution script.

## Schema Architecture & Normalization

The database is fully normalized in Third Normal Form (3NF) across three related tables to eliminate redundancy and update anomalies:

1. **`submersible_dives`** (Parent table tracking abyssal trench sectors and surface salinity).

2. **`vent_chimneys`** (Child table connected via `dive_id` Foreign Key logging mineral facies and plume heights).

3. **`extremophile_specimen_logs`** (Fact table featuring a **Compound Primary Key** `(chimney_id, specimen_id)`, foreign key cascading rules, and rigorous `CHECK` constraints).

## Data Types Representation

The database satisfies all rubric requirements across its 12 total columns:

* **Nominal:** `trench_sector_code`, `mineral_facies_type`, `organism_classification`

* **Ordinal:** `metabolic_activity_tier` (*Dormant* $\rightarrow$ *Stressed* $\rightarrow$ *Active* $\rightarrow$ *Hyper_Proliferating*)

* **Interval:** `plume_temperature_celsius` (Arbitrary zero reference scale in Celsius)

* **Ratio:** `surface_salinity_ppt`, `buoyant_plume_height_m`, `biomass_dry_weight_mg` (Meaningful absolute true zero)

## How to Run the Script

1. Ensure you have Python installed along with the required libraries (`numpy`).

2. Run the Python script or open your Jupyter Notebook:

   ```bash
   python generate_database.py
   ```

3. The script will safely create and populate `abyssal_hydrothermal_lab.db` with over 1,200 rows, complete with deliberate sensor dropouts (`NULL` values) and duplicate records to ensure high database realism.
