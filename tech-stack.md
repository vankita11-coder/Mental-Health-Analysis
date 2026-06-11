# Tech Stack (Excel + Power BI Focus)

Purpose: Recommended toolset and workflow for this project using Excel and Power BI only. Explicitly avoid Python, R, or ML tools — this is a pure data analytics / BI project.

- **Data Ingest & Storage**:
  - **CSV / Excel files**: Primary raw data exchange format for manual imports and archival snapshots.
  - **Azure SQL / SQL Server / Local SQLite** (optional): store cleaned, join-ready tables for scheduled refreshes if dataset size or concurrency grows.

- **Data Preparation (ETL)**:
  - **Power Query (Excel & Power BI)**: Primary ETL engine — joins, transforms, type conversions, incremental loads, parameterized queries.
  - **Power Query Best Practices**: use query folding when connecting to databases, stage raw -> cleaned -> model tables, document steps.
  - **Excel Power Query**: lightweight cleansing for small datasets or ad-hoc exploration.

- **Data Modeling & Calculations**:
  - **Power Pivot (Excel)** and **Data Model (Power BI)**: build star schemas, define relationships and calculated columns.
  - **DAX (Power BI / Power Pivot)**: measures for rates, rolling averages, year-over-year change, standardized indicators (prevalence %, incidence per 100k).
  - **Naming conventions**: clear table/column names, measure prefixes (e.g., M_ for measures).

- **Analysis & Visualization**:
  - **Excel (PivotTables/Charts)**: quick slice-and-dice, initial EDA, small-group sharing, what-if scenarios using slicers.
  - **Power BI Desktop**: interactive dashboards, cross-filtering visuals, bookmarks, drill-throughs, and report pages for stakeholder views.
  - **Power BI Service**: scheduled refreshes, sharing, row-level security for sensitive views, app workspace publishing.
  - **Paginated Reports** (Power BI Report Builder) for printable tables and static exports.

- **Reporting & Delivery**:
  - **Power BI dashboards** published to workspaces; scheduled email subscriptions and PDF exports.
  - **Excel reports** for stakeholders preferring spreadsheets; use connected PivotTables to the data model for refreshable views.

- **Governance & Ops**:
  - **Versioning**: keep raw snapshots (CSV/Excel) in an archival folder with date stamps.
  - **Data dictionary**: maintain a sheet/markdown with variable definitions, source, update frequency, and known biases.
  - **Access & Security**: use Power BI row-level security and service workspaces; follow organizational privacy rules (HIPAA awareness if PHI present).
  - **Refresh schedule**: define frequency (daily/weekly/monthly) depending on upstream data availability.

- **Collaboration & Documentation**:
  - **OneDrive/SharePoint** for shared Excel workbooks and dataset snapshots.
  - **README and Data Dictionary** alongside reports for reproducibility.

- **Skills & Roles**:
  - **Data Analyst (Excel & Power BI)**: builds ETL in Power Query, data model, DAX measures, and visuals.
  - **Data Steward**: maintains data dictionary, manages sources and access.
  - **Product Owner / SME**: validates metric definitions and interpretation.

Notes and constraints:
- No use of Python, R, or ML tools — all transformations and calculations should be implemented via Power Query, DAX, and Excel.
- For large-scale ingestion or complex joins across massive claims/EHR data, use a lightweight SQL store (Azure SQL / SQL Server). Keep downstream analysis in Power BI / Excel.
