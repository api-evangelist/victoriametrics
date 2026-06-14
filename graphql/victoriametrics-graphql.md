# VictoriaMetrics GraphQL Schema

This directory contains a conceptual GraphQL schema for the VictoriaMetrics time-series database and monitoring platform. VictoriaMetrics does not natively expose a GraphQL endpoint; this schema is a structured representation of its Prometheus-compatible HTTP API, MetricsQL query engine, cluster component model, and Enterprise features, designed to support code generation, API tooling, and documentation workflows.

## Source API Surface

| Endpoint group | Base path | Notes |
|---|---|---|
| Instant query | `/api/v1/query` | PromQL / MetricsQL expression at a single timestamp |
| Range query | `/api/v1/query_range` | Expression over a time window with a step interval |
| Label names | `/api/v1/labels` | All label names present in the store |
| Label values | `/api/v1/label/<name>/values` | Values for a given label name |
| Series search | `/api/v1/series` | Series matching a selector |
| TSDB status | `/api/v1/status/tsdb` | Cardinality statistics |
| Metric metadata | `/api/v1/metadata` | TYPE / HELP strings per metric |
| Export (JSON) | `/api/v1/export` | Line-delimited JSON export of raw samples |
| Export (native) | `/api/v1/export/native` | Binary native format export |
| Import | `/api/v1/import` | Bulk import of JSON / native / CSV data |
| Delete series | `/api/v1/admin/tsdb/delete_series` | Delete series matching a selector |
| Federation | `/federate` | Prometheus federation endpoint |
| vmagent targets | `/api/v1/targets` | Scrape target health and state |

Reference: https://docs.victoriametrics.com/url-examples/

## Schema File

`victoriametrics-schema.graphql`

## Type Inventory

### Core metric primitives

| Type | Description |
|---|---|
| `Metric` | Named metric with full label set and optional type/help |
| `MetricName` | Wrapper for the `__name__` label value |
| `MetricLabel` | A single key-value label pair |
| `MetricValue` | A (timestamp, value) pair at an instant |
| `MetricType` | Enum: COUNTER, GAUGE, HISTOGRAM, SUMMARY, UNTYPED |

### Samples and time series

| Type | Description |
|---|---|
| `Sample` | A single (timestamp, value) data point |
| `TimeSeries` | Metric identity combined with a list of samples |
| `TimeSeriesData` | Raw export payload: separate value and timestamp arrays |
| `SeriesMeta` | Metric descriptor without sample data |
| `RangeSample` | A (timestamp, value) pair within a range result |

### Query language abstractions

| Type | Description |
|---|---|
| `PromQL` | Parsed PromQL expression with validation state |
| `MetricsQL` | MetricsQL expression (superset of PromQL) with extension hints |

### Query results

| Type | Description |
|---|---|
| `QueryResult` | Instant-query response wrapping `InstantVector` elements |
| `InstantVector` | Single vector element: metric labels + scalar value |
| `RangeResult` | Range-query response wrapping `RangeVector` elements |
| `RangeVector` | Single matrix element: metric labels + value matrix |

### Label discovery

| Type | Description |
|---|---|
| `LabelNames` | Response from `/api/v1/labels` |
| `LabelValues` | Response from `/api/v1/label/<name>/values` |

### Export and series discovery

| Type | Description |
|---|---|
| `ExportResult` | Line from a `/api/v1/export` response |
| `SeriesResult` | Response wrapper from `/api/v1/series` |
| `Series` | Single series label set |

### TSDB statistics and cardinality

| Type | Description |
|---|---|
| `SeriesCount` | Aggregate series count with per-metric and per-label breakdowns |
| `MetricGroupCount` | Count of series under a single grouping key |
| `Cardinality` | Full TSDB status cardinality snapshot |
| `CardinalityStats` | Cardinality with churn counters for a specific date |

### Storage and retention

| Type | Description |
|---|---|
| `RetentionInfo` | Retention period and deduplication configuration |
| `StorageInfo` | Top-level storage statistics (rows, blocks, sizes) |
| `IndexInfo` | Inverted index statistics |
| `HotStorageInfo` | In-memory / recently flushed data statistics |
| `ColdStorageInfo` | On-disk big-parts (cold) statistics |
| `DataPart` | A single data part file on disk |
| `DataPartMeta` | Extended metadata for a data part |
| `Rotation` | A merge or downsampling rotation event |
| `RetentionPolicy` | Label-scoped retention policy (Enterprise) |

### Cluster components

| Type | Description |
|---|---|
| `ClusterNode` | A node in a VictoriaMetrics cluster |
| `ClusterRole` | Enum: VMINSERT, VMSELECT, VMSTORAGE |
| `NodeDetails` | Runtime detail for a cluster node |
| `NodeStatus` | Health and error state of a node |
| `MemStats` | Runtime memory statistics |
| `ComponentFlags` | Raw startup flags for any VM component |
| `Vminsert` | vminsert component with insertion configuration |
| `Vmselect` | vmselect component with query configuration |
| `Vmstorage` | vmstorage component with storage details |
| `ReplicationSet` | A logical shard / replication group |

### vmagent

| Type | Description |
|---|---|
| `Vmagent` | A vmagent instance with its targets and queues |
| `VmagentTarget` | A scrape target with labels and health state |
| `TargetHealth` | Enum: UNKNOWN, UP, DOWN |
| `TargetStatus` | Detailed scrape status including timings |
| `QueueMetrics` | Write-queue depth and throughput counters |
| `BackpressureMetrics` | Flow-control / throttling metrics |
| `RemoteWriteTarget` | A remote-write destination configured in vmagent |

### Anomaly detection (Enterprise vmanomaly)

| Type | Description |
|---|---|
| `Anomaly` | A single detected anomaly event with score and severity |
| `AnomalySeverity` | Enum: LOW, MEDIUM, HIGH, CRITICAL |
| `AnomalyReport` | Aggregated anomaly report for a time window |

### Security / API keys (Enterprise)

| Type | Description |
|---|---|
| `APIKey` | An API key for Enterprise authentication |
| `Token` | A bearer token for API authentication |

### Root types

| Type | Description |
|---|---|
| `Query` | Root query: instant/range queries, label discovery, series search, cardinality, cluster, anomaly, and storage |

## Usage Notes

- `Time` scalars are Unix timestamps in milliseconds (or RFC3339 strings depending on context).
- `Float64` scalars represent 64-bit floating-point metric values, including `NaN`, `+Inf`, and `-Inf`.
- `Duration` scalars follow Prometheus duration syntax, e.g., `15s`, `5m`, `1h`.
- Cluster-mode endpoints prefix paths with `/select/<accountID>/prometheus/` (vmselect) or `/insert/<accountID>/prometheus/` (vminsert).
- Enterprise-only types (`RetentionPolicy`, `Anomaly`, `AnomalyReport`, `APIKey`, `Token`) require an active VictoriaMetrics Enterprise license.

## References

- API URL examples: https://docs.victoriametrics.com/url-examples/
- Key concepts / MetricsQL: https://docs.victoriametrics.com/keyConcepts.html
- Cluster setup: https://docs.victoriametrics.com/cluster-victoriametrics/
- vmagent: https://docs.victoriametrics.com/vmagent/
- Anomaly detection: https://docs.victoriametrics.com/anomaly-detection/
- GitHub: https://github.com/VictoriaMetrics/VictoriaMetrics
