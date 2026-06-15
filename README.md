# VictoriaMetrics (victoriametrics)

VictoriaMetrics is a fast open-source time-series database and monitoring solution. It exposes a Prometheus-compatible HTTP query API, a wide range of ingestion endpoints (Prometheus remote-write, InfluxDB Line Protocol, DataDog v1/v2, Graphite, OpenTSDB, CSV, JSON, native), a federation endpoint and admin endpoints. The commercial Enterprise edition adds anomaly detection (vmanomaly), downsampling, multi-tenancy and other features.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/victoriametrics/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/victoriametrics/refs/heads/main/apis.yml)

## Tags

- Database
- Time-Series
- Monitoring
- Open Source
- Prometheus
- PromQL
- MetricsQL
- Observability

## Timestamps

- **Created:** 2026-05-08
- **Modified:** 2026-05-08

## APIs

### VictoriaMetrics Prometheus-Compatible Query API

Prometheus-compatible HTTP API for instant and range queries (PromQL / MetricsQL), label discovery, series search, metadata and TSDB status. Single-node default port 8428; in cluster mode served by vmselect on port 8481 under /select/<accountID>/prometheus/.

- **Human URL:** [https://docs.victoriametrics.com/url-examples/](https://docs.victoriametrics.com/url-examples/)
- **Base URL:** `http://<host>:8428`

#### Tags

- REST
- Prometheus
- PromQL
- MetricsQL
- Query

#### Properties

- [Documentation](https://docs.victoriametrics.com/)
- [API Reference](https://docs.victoriametrics.com/url-examples/)
- [Prom Q L Compat](https://docs.victoriametrics.com/keyConcepts.html#metricsql)
- [Postman Collection](collections/victoriametrics.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/victoriametrics.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### VictoriaMetrics Ingestion APIs

Multi-protocol ingestion — Prometheus remote-write (/api/v1/write), InfluxDB line protocol (/write or /insert/0/influx/write), DataDog v1 (/datadog/api/v1/series) and v2 (/datadog/api/v2/series), Graphite (TCP 2003 or /graphite endpoints), OpenTSDB (TCP 4242 or /api/put), CSV/JSON/ native /api/v1/import.

- **Human URL:** [https://docs.victoriametrics.com/#how-to-import-time-series-data](https://docs.victoriametrics.com/#how-to-import-time-series-data)
- **Base URL:** `http://<host>:8428`

#### Tags

- REST
- Ingestion
- Remote Write
- InfluxDB
- DataDog
- Graphite
- OpenTSDB

#### Properties

- [Documentation](https://docs.victoriametrics.com/#how-to-import-time-series-data)
- [Postman Collection](collections/victoriametrics.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/victoriametrics.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### VictoriaMetrics Admin / Federation API

Administrative endpoints for time-series deletion (/api/v1/admin/tsdb/ delete_series), data export/import (/api/v1/export, /api/v1/import in various formats), Prometheus federation (/federate), TSDB stats and metadata.

- **Human URL:** [https://docs.victoriametrics.com/#how-to-delete-time-series](https://docs.victoriametrics.com/#how-to-delete-time-series)
- **Base URL:** `http://<host>:8428`

#### Tags

- REST
- Admin
- Federation
- Export

#### Properties

- [Postman Collection](collections/victoriametrics.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/victoriametrics.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### VictoriaMetrics Anomaly Detection (vmanomaly)

Enterprise-only ML-driven anomaly detection. Reads via Prometheus query API, writes anomaly scores back via Prometheus remote-write. Multivariate models, confidence intervals and HA deployment supported.

- **Human URL:** [https://docs.victoriametrics.com/anomaly-detection/](https://docs.victoriametrics.com/anomaly-detection/)
- **Base URL:** `http://<host>:8490`

#### Tags

- Enterprise
- Anomaly Detection
- ML
- Prometheus

#### Properties

- [Documentation](https://docs.victoriametrics.com/anomaly-detection/)
- [Postman Collection](collections/victoriametrics.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/victoriametrics.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/victoriametrics)
- [Website](https://victoriametrics.com/)
- [Documentation](https://docs.victoriametrics.com/)
- [Pricing](https://victoriametrics.com/products/enterprise/)
- [Git Hub](https://github.com/VictoriaMetrics/VictoriaMetrics)
- [Enterprise Trial](https://victoriametrics.com/products/enterprise/trial/)
- [Plans](plans/victoriametrics-plans-pricing.yml)
- [Rate Limits](rate-limits/victoriametrics-rate-limits.yml)
- [Fin Ops](finops/victoriametrics-finops.yml)
- [Integrations](https://victoriametrics.com/partners/index.html)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
