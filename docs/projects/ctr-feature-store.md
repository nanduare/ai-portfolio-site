# CTR Feature Store + Low-Latency Serving (Redis, FastAPI, sklearn)

- Repo: https://github.com/nanduare/ctr-feature-store
- Role: ML Engineer (solo)
- Status: In progress
- Dates: 2025

## Problem
Serve CTR predictions with millisecond latency and offline/online feature consistency.

## Architecture
Parquet (offline) → batch aggregates → Redis (online features) → FastAPI model serving

## Approach
- Build user/ad CTR aggregates offline and load into Redis hashes
- Train logistic regression with time-aware split and proper encodings
- Serve predictions via FastAPI using online features

## Results
- P99 online feature reads ~3–10 ms (Redis)
- AUC ~0.78 on synthetic clickstream

## How to Run
- `docker compose up --build`
- `POST /predict` with user_id, ad_id, device_type, country (see README)
