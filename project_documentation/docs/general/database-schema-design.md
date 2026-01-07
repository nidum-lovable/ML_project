---
title: Database Schema Design
type: database
created: 2026-01-07 04:07:38.230000
updated: 2026-01-07 04:07:38.230000
synced_from: VibeProject
---

# Database Design Document

## 1. Overview
We utilize a hybrid storage approach: `MongoDB` for persistent logs and `Redis` for ephemeral state.

## 2. MongoDB Collections
### 2.1 `alerts` Collection
Stores details of every detected anomaly.
```json
{
  "_id": ObjectId,
  "flow_id": String,
  "timestamp": Date,
  "src_ip": String,
  "dst_ip": String,
  "anomaly_score": Double,
  "model_version": String,
  "features": { "duration": 1.2, "bytes": 5000 },
  "explanation": Array<FeatureContribution>
}
```

### 2.2 `traffic_stats` Collection
Aggregated metrics for dashboard graphing (e.g., packets per minute).
```json
{
  "timestamp_window": Date,
  "total_packets": Int,
  "total_bytes": Long,
  "unique_ips": Int
}
```

## 3. Redis Keys
- `flow:{flow_tuple}`: HASH containing current packet counts for active flows. TTL = 60s.
