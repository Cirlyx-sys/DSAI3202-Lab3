# DSAI3202 – Lab 3: Data Preprocessing on Azure

##  Overview
This lab demonstrates how to preprocess large-scale data using the Azure ecosystem — combining **Azure Data Lake**, **Azure Data Factory**, **Microsoft Fabric**, and **Databricks**.

---

## ⚙️Steps Completed

###  Azure Data Lake (Bronze)
- Created storage account `goodreadsreviews60104310` with hierarchical namespace.
- Created container **lakehouse** with subfolders: `raw/`, `processed/`, `gold/`.
- Uploaded Goodreads JSON datasets for books, authors, and reviews.

### 2️Azure Data Factory (Silver)
- Built pipelines to copy raw JSON → Parquet.
- Created linked services, datasets, and tested data ingestion.

### 3️ Microsoft Fabric (Silver → Gold attempt)
- Connected Fabric workspace to ADLS Gen2 using access key.
- Performed cleaning and transformations using Power Query (Dataflow Gen2).
- Due to region limitations (Qatar), publishing to Warehouse failed.
- Exported M code and screenshots for verification.

### 4️ Databricks (Gold)
4. Databricks (Gold Layer)

Set up a Databricks workspace and configured a compute cluster (Runtime 16.4 LTS).

Connected securely to Azure Data Lake Gen2 using a SAS token for authentication.

Loaded the Silver-layer Parquet datasets (books, authors, and reviews) and performed a complete cleaning and transformation pipeline:

Removed null and invalid records.

Filtered out short reviews (<10 characters).

Enforced valid rating values (1–5).

Trimmed text and standardized review content.

Aggregated per-book average ratings and total review counts.

Added “Amaze” feature engineering to enrich the dataset beyond the requirements:

Calculated word and character counts for each review.

Counted exclamation (!) and question (?) marks as emotional indicators.

Applied text normalization (lowercasing and whitespace cleaning).

Computed a capitalization ratio to measure emphasis in text.

Added a link flag to identify reviews containing URLs.

Performed quick data visualization (rating distribution bar chart).

Saved and versioned the curated data into two Gold-layer Delta tables:

gold/features_v1 → standard cleaned dataset.

gold/features_v2_amaze → enriched version with advanced text and statistical features.
---

## 🧩 Results
- Successfully generated clean, enriched, analytics-ready dataset.
- All transformations verified through Spark schema and sample rows.
- Gold dataset stored as Delta for future ML/BI analysis.

---

## 🧾 Files in This Repo
| File | Description |
|------|--------------|
| `Lab3_SectionVI_Gold.ipynb` | Databricks notebook (Gold layer + features) |
| `curated_reviews_Mcode.txt` | Power Query M code from Fabric |
| `fabric_cleaning_steps.png` | Fabric Dataflow steps screenshot |
| `databricks_output.png` | Databricks successful output screenshot |
| `README.md` | This file — full documentation |
| `DSAI3202_Lab3_Report.docx` | Formal lab report document |

---

## 📸 Acknowledgment
All steps were performed by **Abdelrahman Abousaadya (60104310)** as part of **DSAI3202 – Data Preprocessing Lab 3** under the guidance of **University of Doha for Science and Technology (UDST)**.
