# VictoriaMetrics (victoriametrics)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
