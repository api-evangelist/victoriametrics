# VictoriaMetrics (victoriametrics)

VictoriaMetrics is a fast open-source time-series database and monitoring solution, fully compatible with Prometheus protocols. Available as Community (Apache 2.0) and Enterprise (commercial). Also offered as VictoriaMetrics Cloud (managed).

**APIs.json:** [apis.yml](apis.yml)

## APIs
- **Prometheus-Compatible Query** — `http://<host>:8428` — `/api/v1/query`, `/api/v1/query_range`, `/api/v1/labels`, `/api/v1/series`, `/api/v1/status/tsdb`, `/api/v1/metadata` (cluster: vmselect on 8481).
- **Ingestion** — Prometheus remote-write (`/api/v1/write`), InfluxDB line protocol (`/write`), DataDog v1/v2 (`/datadog/api/v1/series`, `/v2/series`), Graphite (TCP 2003), OpenTSDB (TCP 4242 or `/api/put`), CSV/JSON/native imports.
- **Admin / Federation** — `/api/v1/admin/tsdb/delete_series`, `/api/v1/export*`, `/api/v1/import*`, `/federate`.
- **vmanomaly** — Enterprise ML anomaly detection; reads via Prom query API, writes back via remote-write.

## OpenAPI
VictoriaMetrics does not currently publish a single OpenAPI document for its many ingestion / query / admin surfaces; pipeline did not retrieve a spec into `openapi/`.

## Default Ports
- 8428 — single-node HTTP (REST + ingest)
- 8480 — vminsert (cluster)
- 8481 — vmselect (cluster)
- 8482 — vmstorage (cluster)
- 2003 — Graphite TCP
- 4242 — OpenTSDB TCP
- 8490 — vmanomaly (Enterprise)

## Tags
Database, Time-Series, Monitoring, Open Source, Prometheus, PromQL, MetricsQL, Observability

## Common Properties
- [Website](https://victoriametrics.com/)
- [Documentation](https://docs.victoriametrics.com/)
- [Enterprise](https://victoriametrics.com/products/enterprise/) · [Trial](https://victoriametrics.com/products/enterprise/trial/)
- [GitHub](https://github.com/VictoriaMetrics/VictoriaMetrics)
- [Plans](plans/victoriametrics-plans-pricing.yml) — partially reconciled (editions; Enterprise/Cloud numeric prices private)
- [Rate Limits](rate-limits/victoriametrics-rate-limits.yml) — operational flags documented; numeric defaults version-specific
- [FinOps](finops/victoriametrics-finops.yml) — reconciled, FOCUS-aligned

## Editions (reconciled)
- **Community** — Apache 2.0; free.
- **Enterprise Trial** — free trial license.
- **Enterprise** — vmanomaly, downsampling, multi-tenancy quotas, audit logs, SLA. Custom pricing.
- **VictoriaMetrics Cloud** — managed, tiered by ingestion rate / active series.

## Timestamps
- **Created:** 2026-05-08
- **Modified:** 2026-05-08

## Maintainers
- **Kin Lane** — kin@apievangelist.com
