# ROMA FLOW AI — Pilot-Ready v1.2

ROMA FLOW AI is an urban-tourism intelligence platform that forecasts tourism demand, combines capacity and mobility context, and recommends demand redistribution away from overloaded hotspots toward compatible underused destinations.

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
python scripts/generate_dataset.py
python scripts/train_v1.py
uvicorn app.main:app --reload
```

Open `http://127.0.0.1:8000/` for the responsive dashboard or `/docs` for Swagger.

## Docker

```bash
docker compose up --build
```

## Key endpoints

- `GET /api/v1/city-status?date=2026-09-18&hour=17`
- `GET /api/v1/forecast?asset_id=TRV_TREVI&date=2026-09-18&hour=17`
- `GET /api/v1/recommendations?asset_id=TRV_TREVI&date=2026-09-18&hour=17`
- `GET /api/v1/capacity`
- `GET /api/v1/kpis`
- `GET /api/v1/model/report`
- `GET /api/v1/model/calibration`
- `GET /api/v1/data/sources`
- `GET /api/v1/production/readiness`

## Architecture

Data ingestion → quality/provenance → tourism knowledge model → capacity + mobility features → demand forecast → flow optimisation → recommendations → city/operator interfaces → feedback/KPIs.

## Live sources

See `docs/REAL_DATA_RUNBOOK.md`. Verified public source endpoints are configurable via environment variables. Live network access is intentionally executed at deployment time rather than silently mocked during build.

## Important

Synthetic data is used for deterministic development and testing. It must be replaced by governed real data before making operational or funding claims about actual city impact.
