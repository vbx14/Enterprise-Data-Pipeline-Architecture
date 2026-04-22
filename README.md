# Enterprise Data Pipeline Architecture (NETVIBES / 3DEXPERIENCE)

## Overview
This project is about a real-world enterprise data pipeline handling multi-source ingestion, ETL processing, and dashboard delivery.

## Architecture Diagram

```mermaid
flowchart TB

%% DATA SOURCES
subgraph S1[Data Sources]
    A1[SQL Databases]
    A2[SharePoint CSV Files]
end

%% INGESTION
subgraph S2[Ingestion Layer]
    B["Java Integration Layer - Validation, Parsing, Transformation"]
end

%% 3DEXPERIENCE PLATFORM
subgraph S3[3DEXPERIENCE NETVIBES]

    subgraph S3A[Data Factory Studio]
        C1["Raw SGIs - Semantic Graph Index"]
        C2["ETL Pipelines - Transformation and Enrichment"]
        C3["Transformed SGIs - Business Ready Data"]
    end

    subgraph S3B[Data Perspective Studio]
        D["UI Logic Layer - Custom Transformations and Aggregations"]
    end

    subgraph S3C[Presentation Layer]
        E["Dashboards - Data Perspectives"]
    end

end

%% FLOW
A1 --> B
A2 --> B

B --> C1
C1 --> C2
C2 --> C3

C3 --> D
D --> E
