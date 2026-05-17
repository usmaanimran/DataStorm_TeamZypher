# Team Zypher — Data Storm v7.0 (OCTAVE)

End-to-end lakehouse pipeline for **Potential-Based Allocation**: estimating uncapped latent monthly demand at each outlet for January 2026.

## Architecture Overview

| Layer   | Artifact / Script | Status |
|---------|-------------------|--------|
| Bronze  | `DataStorm_TeamZypher_Bronze.ipynb` | Locked (Ingestion & Checksums) |
| Silver  | `DataStorm_TeamZypher_Silver.ipynb` | Locked (Cleaning & Quarantine) |
| Gold    | `DataStorm_TeamZypher_Gold (1).ipynb` | Locked (Feature Engineering) |
| **ML** | `DataStorm_TeamZypher_Modeling.ipynb` | **Run after Gold** |

The Gold layer produces `lakehouse/gold/<timestamp>/master_feature_store.parquet` (SKU × outlet × month features, targeting the engineered `Latent_Demand_Proxy`).

## Prerequisites

- Python 3.10+
- Completed Gold run yielding `master_feature_store.parquet`

Install modeling dependencies:

```bash
pip install -r requirements-ml.txt
