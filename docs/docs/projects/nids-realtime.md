# Real-Time Network Intrusion Detection (Kafka, Python, Postgres, Redis)

- Repo: https://github.com/nanduare/nids-realtime
- Role: ML Engineer (end-to-end)
- Status: In progress
- Dates: 2025

## Problem
Detect and classify malicious network activity in real time with low latency and high precision.

## Architecture
Kafka → Python consumer (sklearn model) → Redis (alerts buffer) + Postgres (persistent alerts)

## Approach
- Synthetic NetFlow-like generator → feature engineering → RandomForest
- Streaming inference with checkpointed consumer
- Write predictions to Postgres for BI; Redis for fast dashboards

## Results
- ROC-AUC ~0.95 on holdout synthetic data
- p95 end-to-end latency < 250 ms at ~100+ EPS locally

## How to Run
- Repo README includes docker-compose
- Start: `docker compose up --build`
- Query: `SELECT pred_label, COUNT(*) FROM alerts GROUP BY 1 ORDER BY 2 DESC;`

## Next
- Replace synthetic with CIC-IDS2017/UNSW-NB15
- Add Prometheus/Grafana monitoring and drift detection
