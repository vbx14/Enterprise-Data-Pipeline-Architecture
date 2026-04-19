# Enterprise Data Pipeline Architecture (NETVIBES / 3DEXPERIENCE)

## Overview
This project is about a real-world enterprise data pipeline handling multi-source ingestion, ETL processing, and dashboard delivery.

## Architecture Diagram

```mermaid
flowchart TD

A[SQL Databases] --> B[Java Ingestion Layer]
A2[PIM System - Excel to CSV] --> B

B --> C[NETVIBES Platform]

C --> D[DFS Storage Layer - Raw and Processed Data]
D --> E[Pipeline Mesh - ETL Engine]
E --> F[SGI Modules - Data Processing]

F --> G[DPS Layer - UI Logic]
G --> H[DP Layer - Dashboards]

E --> I[ITEROP Alerting System]
I --> H
