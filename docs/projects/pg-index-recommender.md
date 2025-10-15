# PostgreSQL Query Log Analyzer & Index Recommender

- Repo: https://github.com/nanduare/pg-index-recommender
- Role: Systems/DB Engineer
- Status: In progress
- Dates: 2025

## Problem
Find slow queries and recommend indexes to reduce p95 latency without regressions.

## Approach
- Collect from `pg_stat_statements`
- Normalize SQL (sqlglot), extract predicates/joins
- Suggest index candidates, validate with `EXPLAIN ANALYZE`

## Run
- `docker compose up -d` (starts Postgres with pg_stat_statements)
- `python cli.py --dsn postgresql://pguser:pgpass@localhost:5433/pgdb`
