# Operational Monitor

Sanitized public overview of an internal operational analytics and monitoring application.

This repository is intentionally documentation-only. The original project contains sensitive operational logic, internal configuration, production integrations and non-public data, so the source code is not included. The screenshots below are redacted and use generic labels.

## What the project demonstrates

- Operational monitoring dashboard for component and system health
- Feature-level warning scores, thresholds and alert history
- Interactive map view for operational status overview
- Assistant-style workflow for generating report/export packages
- Report-oriented UI with downloadable artifacts
- Full-stack application design using a frontend, backend reporting service, monitoring layer and deployment workflow

## Screenshots

### Component health dashboard

![Component health dashboard](docs/screenshots/system-monitor-dashboard.png)

### Feature heat and threshold controls

![Feature heat and threshold controls](docs/screenshots/system-monitor-feature-heat.png)

### Interactive map dashboard

![Interactive map dashboard](docs/screenshots/interactive-map-dashboard.png)

### Assistant workflow

![Assistant workflow](docs/screenshots/assistant-workflow.png)

## High-level architecture

```text
Frontend UI
  |-- statistics workspace
  |-- monitoring dashboards
  |-- assistant workflow
  |-- reports and jobs interface

Backend services
  |-- report generation API
  |-- monitoring and warning logic
  |-- artifact packaging
  |-- configuration and scheduling layer

Data and outputs
  |-- operational event data source
  |-- generated reports
  |-- charts
  |-- metadata
  |-- export bundles
```

## Why the code is not public

The production project is connected to sensitive internal workflows. Public release of the source code could expose implementation details, operational assumptions, configuration patterns, data fields, alert logic, internal terminology or deployment information.

For that reason, this repository only contains a sanitized overview and redacted screenshots. No production data, credentials, endpoints, queries, internal identifiers, real logs or real exports are included.

## Technologies used in the original project

- Python
- FastAPI-style backend services
- React and TypeScript frontend
- Docker-based deployment
- Elasticsearch-style operational data access
- Automated report generation
- Excel, chart, metadata and ZIP export workflows
- Monitoring and warning dashboards
- Local LLM assistant workflow for structured report generation
