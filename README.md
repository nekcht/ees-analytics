# Operational Monitor

Sanitized public overview of an internal operational analytics, monitoring and reporting application.

This repository is intentionally documentation-only. The original project contains sensitive operational logic, internal configuration, production integrations and non-public data, so the source code is not included. The screenshots below are redacted and use generic labels.

The project was developed as a full-stack monitoring and analytics platform for a national-scale operational information system. It combines frontend dashboards, backend report generation, Elastic Stack based operational data access, feature engineering, anomaly detection, alerting workflows and an assistant-style interface for structured report creation.

## What the project demonstrates

- Full-stack operational monitoring application with dashboard, reporting and assistant workflows
- Python backend services for report generation, data processing and artifact packaging
- React and TypeScript frontend for dashboards, report forms, assistant interaction and monitoring views
- Elastic Stack based operational data access and log-driven analytics
- Monitoring of a large operational system serving more than 3,000 concurrent users
- Feature engineering over high-volume operational logs and user activity events
- ECOD-based anomaly detection using engineered feature vectors from operational telemetry
- Rolling time-window analysis for component health, latency, throughput, stale activity and alert trends
- Feature-level warning scores, thresholds, history tracking and alert lifecycle management
- Interactive map view for nationwide operational status overview
- Assistant-style workflow for converting natural-language report requests into structured report/export jobs
- Automated generation of Excel files, charts, metadata files and ZIP export bundles
- Docker-based deployment design with separated frontend, backend, monitoring and supporting services
- Privacy-aware engineering, with sensitive data, internal endpoints, operational rules and credentials excluded from the public version

## Screenshots

### Component health dashboard

![Component health dashboard](docs/screenshots/system-monitor-dashboard.png)

### Feature heat and threshold controls

![Feature heat and threshold controls](docs/screenshots/system-monitor-feature-heat.png)

### Interactive map dashboard

![Interactive map dashboard](docs/screenshots/interactive-map-dashboard.png)

### Assistant workflow

![Assistant workflow](docs/screenshots/assistant-workflow.png)

## Technical highlights

### Monitoring and anomaly detection

The monitoring layer uses operational telemetry collected from Elastic Stack indexes. Raw logs and user activity events are transformed into handcrafted monitoring features over rolling time buckets. These features are used to detect abnormal system behavior and support operational triage.

The internal monitoring dataset is derived from operational logs produced by a large distributed user base, with more than 3,000 concurrent users at peak usage. The system aggregates these events into time-windowed feature vectors suitable for unsupervised anomaly detection and dashboard visualization.

Examples of engineered feature families include:

- request and operation throughput
- component activity counts
- stale or inactive component indicators
- latency and processing duration metrics
- success, failure and rejection ratios
- rolling bucket statistics
- normalized warning indicators
- feature-level contribution scores for alert explanation

An ECOD anomaly detection approach was used on the engineered feature dataset to identify abnormal feature vectors without requiring manually labelled incidents. The monitoring UI exposes both a unified warning score and per-feature warning signals, so an operator can see not only that the system is abnormal, but also which features contributed to the warning.

### Operational dashboards

The dashboard layer provides real-time and historical views for system health. It includes:

- component health overview
- unified warning score
- feature-level alert cards
- threshold controls
- alert timeline and recovery states
- rolling history charts
- active, stale and alerting operational points
- geographic overview of operational activity

The purpose is to reduce manual inspection effort by turning raw operational logs into interpretable monitoring signals.

### Reporting and export workflows

The reporting workflow supports structured generation of operational reports and export packages. The internal version can generate multiple artifact types from selected time windows, filters and report definitions.

The public screenshots show the workflow concept only. Sensitive report logic, real filters, field names, operational terminology and production integrations are not included.

Supported artifact concepts include:

- Excel reports
- charts and plots
- metadata files
- ZIP export bundles
- scheduled or repeatable report jobs

### Assistant-driven report generation

The assistant workflow acts as a natural-language front end for report generation. It converts user requests into structured report parameters, validates the request, asks for clarification when required and returns downloadable artifacts when execution is possible.

The internal implementation combines deterministic planning with optional local LLM assistance. The design goal was not open-ended chat, but controlled report planning with safe execution boundaries.

The assistant workflow demonstrates:

- intent classification for report requests
- date-range extraction
- output type selection
- clarification handling
- structured execution planning
- downloadable artifact response
- separation between casual conversation and executable report requests

## High-level architecture

```text
Frontend UI
  |-- statistics workspace
  |-- monitoring dashboards
  |-- assistant workflow
  |-- reports and jobs interface
  |-- interactive operational map

Backend services
  |-- FastAPI-style reporting API
  |-- report execution layer
  |-- monitoring and warning service
  |-- feature engineering pipeline
  |-- ECOD-based anomaly detection workflow
  |-- artifact packaging service
  |-- configuration and scheduling layer

Data and analytics layer
  |-- Elastic Stack operational logs
  |-- rolling time-window aggregation
  |-- handcrafted monitoring features
  |-- warning score calculation
  |-- alert history and recovery tracking

Outputs
  |-- Excel reports
  |-- charts
  |-- metadata files
  |-- ZIP export bundles
  |-- dashboard-ready status summaries

Deployment
  |-- Docker-based service deployment
  |-- separated frontend and backend services
  |-- internal service-to-service communication
  |-- runtime configuration through environment variables
```

## Original technology stack

The original internal project used:

- Python for backend analytics, reporting and monitoring logic
- FastAPI-style backend services
- Pandas-based data transformation and report preparation
- ECOD anomaly detection on engineered monitoring features
- Elastic Stack as the operational log and event data source
- React and TypeScript frontend
- Dashboard components for statistics, monitoring, reports, jobs and assistant workflows
- Docker-based deployment
- Excel, chart, metadata and ZIP export workflows
- Local LLM assisted planning for structured report generation
- Map-based operational overview using local tile services
- Automated monitoring, alert history and notification-oriented workflows

## Why the code is not public

The production project is connected to sensitive internal workflows and operational systems. Public release of the source code could expose implementation details, operational assumptions, configuration patterns, data fields, alert logic, internal terminology, deployment information or security-relevant behavior.

For that reason, this repository only contains a sanitized overview and redacted screenshots. No production data, credentials, endpoints, queries, internal identifiers, real logs, trained artifacts, configuration files or real exports are included.
