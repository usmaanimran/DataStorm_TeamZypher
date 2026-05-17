# Team Zypher — Data Storm v7.0 (OCTAVE)

End-to-end lakehouse pipeline for **Potential-Based Allocation**: estimating uncapped latent monthly demand at each outlet for January 2026.

🔗 **Official Google Drive Workspace:** [Team Zypher Project Folder](https://drive.google.com/drive/folders/1hzJtMfkISC4c1xsLFbLvh1JyuDGG9-7-?usp=sharing)
*(Note: This pipeline was natively engineered in Google Colab. Executing via the Drive link above is the recommended approach.)*

## Architecture Overview

| Layer   | Artifact / Script | Status |
|---------|-------------------|--------|
| Bronze  | `DataStorm_TeamZypher_Bronze.ipynb` | Locked (Ingestion & Checksums) |
| Silver  | `DataStorm_TeamZypher_Silver.ipynb` | Locked (Cleaning & Quarantine) |
| POI     | `DataStorm_TeamZypher_POI_Scraper.ipynb` | Locked (Spatial Density Extraction) |
| Gold    | `DataStorm_TeamZypher_Gold.ipynb` | Locked (Feature Engineering) |
| **ML** | `DataStorm_TeamZypher_Modeling.ipynb` | **Run after Gold** |

The Gold layer produces `lakehouse/gold/<timestamp>/master_feature_store.parquet` (SKU × outlet × month features, targeting the engineered `Latent_Demand_Proxy`).

---

## 🚀 Execution Instructions (Google Colab / Drive)

To replicate the Lakehouse architecture and generate the final predictions using the cloud environment, please follow these steps:

### 1. Environment Setup
1. Open the shared Google Drive folder linked above.
2. Open the notebooks using **Google Colab**.
3. In the first cell of each notebook, ensure Google Drive is mounted:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
