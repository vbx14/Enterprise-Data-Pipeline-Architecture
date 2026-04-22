# Enterprise Data Pipeline Architecture (NETVIBES / 3DEXPERIENCE)

## Overview
This project is about a real-world enterprise data pipeline handling multi-source ingestion, ETL processing, and dashboard delivery.

## Architecture Diagram

```mermaid
flowchart TD

%% =====================
%% DATA SOURCES
%% =====================
subgraph S1[Data Sources]
    A1[SQL Databases]
    A2[SharePoint CSV Files]
end

%% =====================
%% INGESTION LAYER
%% =====================
subgraph S2[Ingestion Layer]
    B[Java Integration Layer<br/>Validation | Parsing | Transformation]
end

%% =====================
%% 3DEXPERIENCE PLATFORM
%% =====================
subgraph S3[3DEXPERIENCE (NETVIBES)]

    %% DATA FACTORY
    subgraph S3A[Data Factory Studio]
        C1[Raw SGIs<br/>(Semantic Graph Index)]
        C2["ETL Pipelines<br/>Transformation and Enrichment"]
        C3[Transformed SGIs<br/>(Business Ready Data)]
    end

    %% DATA PERSPECTIVE
    subgraph S3B[Data Perspective Studio]
        D[UI Logic Layer<br/>Custom Transformations & Aggregations]
    end

    %% PRESENTATION
    subgraph S3C[Presentation Layer]
        E[Dashboards<br/>(Data Perspectives)]
    end

end

%% =====================
%% FLOW
%% =====================
A1 --> B
A2 --> B

B --> C1
C1 --> C2
C2 --> C3

C3 --> D
D --> E
