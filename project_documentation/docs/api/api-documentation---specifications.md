---
title: API Documentation & Specifications
type: api
created: 2026-01-07 04:07:38.230000
updated: 2026-01-07 04:07:38.230000
synced_from: VibeProject
---

# API Documentation

## 1. Overview
The Anomaly Detection System exposes a REST API for the Dashboard to consume real-time alerts and historical data.

## 2. Endpoints
### 2.1 Get System Status
- **GET** `/api/status`
- **Response**: `{ "status": "healthy", "kafka_lag": 0, "active_nodes": 3 }`

### 2.2 Get Recent Alerts
- **GET** `/api/alerts?limit=10&severity=high`
- **Response**:
```json
[
  {
    "id": "alert_123",
    "timestamp": "2023-10-27T10:00:00Z",
    "source_ip": "192.168.1.5",
    "anomaly_score": 0.98,
    "severity": "critical",
    "explanation": { "feature": "packet_size_var", "value": 0.85 }
  }
]
```

### 2.3 Get Flow Details
- **GET** `/api/flows/{flow_id}`
- **Description**: Returns full feature vector and metadata for a specific network flow.
