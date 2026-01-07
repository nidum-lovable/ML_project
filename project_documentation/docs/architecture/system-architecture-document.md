---
title: System Architecture Document
type: architecture
created: 2026-01-07 04:07:38.230000
updated: 2026-01-07 04:07:38.230000
synced_from: VibeProject
---

# System Architecture Document

## 1. High-Level Architecture
The system follows a microservices-based, event-driven architecture to ensure scalability and decoupling of components. This designs allows individual scaling of the ingestion and inference layers.

### 1.1 Components
1.  **Ingestion Service**: Uses `Scapy` or `GoPacket` to capture packets from the NIC. Filtering (BPF) is applied here to discard noise.
2.  **Message Broker**: `Apache Kafka` acts as the buffer between high-speed ingestion and processing. Topics: `raw-packets`, `processed-features`, `alerts`.
3.  **Preprocessing & Feature Engine**: A Python service that consumes raw packets, performs stateful feature extraction (e.g., Flow aggregation over 5s windows), and pushes vectors to Kafka.
4.  **Inference Engine**: Holds the trained PyTorch/Sklearn models. Consumes feature vectors, predicts anomaly scores, and pushes results.
5.  **Persistence Layer**: `MongoDB` stores flow metadata, anomaly scores, and alert logs. `Redis` is used for caching active flow states.
6.  **Visualization Service**: A specific frontend (React/Streamlit) that queries MongoDB to display real-time insights.

## 2. Technology Stack Choice
- **Capture**: Scapy/Libpcap (Industry standard for packet manipulation)
- **Queue**: Apache Kafka (For high-throughput, fault-tolerant messaging)
- **ML Framework**: PyTorch & Scikit-learn (Flexibility for Deep Learning & Classic ML)
- **Database**: MongoDB (Schema-less nature fits varying flow data), Redis (Speed for state management)
