---
title: Deployment & User Guide
type: user-manual
created: 2026-01-07 04:07:38.230000
updated: 2026-01-07 04:07:38.230000
synced_from: VibeProject
---

# Deployment & User Guide

## 1. Prerequisites
- Docker & Docker Compose installed
- 8GB RAM minimum
- Python 3.9+

## 2. Installation
1. Clone the repository: `git clone https://github.com/project/ads-ml.git`
2. Navigate to directory: `cd ads-ml`
3. Build images: `docker-compose build`
4. Start services: `docker-compose up -d`

## 3. Accessing the Dashboard
- Open browser to `http://localhost:3000`
- Login with default credentials (admin/admin)

## 4. Configuration
- Edit `config/settings.yaml` to adjust:
    - `INTERFACE`: Network interface to listen on (e.g., eth0)
    - `ANOMALY_THRESHOLD`: Score above which to alert (default 0.85)
