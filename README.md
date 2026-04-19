flowchart TD

%% Data Sources
A[SQL Databases] --> B[Java Ingestion Layer]
A2[PIM System (Excel → CSV)] --> B

%% Ingestion Layer
B -->|Validation & Parsing| C[NETVIBES Platform]

%% Storage Layer
C --> D[DFS Storage Layer\n(Raw & Processed Data Buckets)]

%% Processing Layer
D --> E[Pipeline Mesh (ETL Engine)]
E --> F[SGI Modules\n(Data Processing Units)]

%% Serving Layer
F --> G[DPS Layer\n(UI Logic & Custom Operations)]
G --> H[DP Layer\nDashboards & Visualization]

%% Alerting
E --> I[ITEROP Alerting System]
I -->|JSON Triggers & Workflows| H
