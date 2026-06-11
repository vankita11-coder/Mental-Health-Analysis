# Dataset Description & Recommended Sources

Purpose: A concise reference of datasets to collect for the Mental Health Trends Analysis project. This is a raw idea / reference guide for dataset collection and prioritization; it assumes no use of Python/ML and that analysis will be done in Excel / Power BI.

1) Priority public datasets (start here)
  - **BRFSS (Behavioral Risk Factor Surveillance System)** — state-level, adult behavioral health indicators (depression diagnosis, frequent mental distress). Good for state trends and risk-factor stratification. Accessible via CDC APIs / CSV.
  - **YRBSS (Youth Risk Behavior Surveillance System)** — high-school age mental-health behaviors (sadness, suicide attempts) with trend tables and state data.
  - **NHIS (National Health Interview Survey)** — national estimates for diagnosed depression/anxiety and care utilization; useful for age/sex/race stratification.
  - **NSDUH (National Survey on Drug Use and Health)** — estimates of mental illness prevalence and co-occurring substance use at national/state levels.
  - **CDC WONDER / NVSS Vital Statistics (Mortality)** — suicide mortality counts and rates by county/state/age/sex; essential outcome metric.

2) Healthcare utilization & administrative sources
  - **HCUP (AHRQ) / State hospital discharge datasets** — hospitalizations and ED visits with principal mental-health diagnoses; good for measuring acute care burden.
  - **Medicare/Medicaid public use files** — utilization and spending patterns for covered populations (claims-level may require data use agreements).
  - **Syndromic surveillance (NSSP) / ED visit datasets** — near-real-time ED trends for mental-health-related visits where available.

3) International and comparative sources
  - **WHO Global Health Estimates / Mental Health Atlas** — cross-country prevalence, workforce, financing.
  - **GBD (IHME)** — long-term burden (prevalence, DALYs) for cross-country comparisons and historical trends.

4) Social determinants & contextual datasets (must-link by geography/time)
  - **ACS (American Community Survey)** — income, education, housing, unemployment at county/tract levels.
  - **BLS (Local Area Unemployment Statistics)** — unemployment trends by county/state.
  - **School enrollment / NCES indicators** — student demographics and school-level context for youth analyses.
  - **Crime statistics / DOJ / local police data** — violence exposure as a social determinant.

5) Supplemental proxy sources (for triangulation)
  - **Google Trends** — search-volume proxies for mental-health-related queries (regionally aggregated).
  - **Social media aggregates (publicly available)** — high-level signals, but use cautiously due to biases and privacy.

6) Recommended minimal dataset to begin analysis (fast start)
  - BRFSS (state-level prevalence + demographics)
  - YRBSS (youth indicators)
  - CDC WONDER suicide mortality (county/state/year)
  - ACS 5-year estimates (demographics & socioeconomic variables)
  - HCUP or state ED/hospital discharge (if available) for utilization trends

7) Data fields / schema suggestions (survey records)
  - `record_id`, `survey_year`, `geography` (state/county), `age_group`, `sex`, `race_ethnicity`, `indicator` (e.g., depression_diagnosis_yes_no), `measure_value` (percent or count), `sample_weight` (if provided), `source`, `notes`

8) Data fields / schema suggestions (administrative claims / hospital)
  - `encounter_id`, `encounter_date`, `patient_age_group`, `patient_sex`, `patient_race`, `zip_code`, `county`, `primary_dx`, `secondary_dx`, `disposition`, `payer`, `length_of_stay`, `cost` (if available), `source`

9) Collection notes & access
  - Public datasets (CDC, BRFSS, YRBSS, NHIS, ACS, WONDER) are downloadable as CSV or accessible via APIs; annotate licensing and update cadence.
  - HCUP, claims, and detailed EHR data often require DUA or purchase — begin with aggregated public-use tables if procurement is slow.
  - Maintain a data inventory sheet (source, URL, last download date, contact, frequency, access restrictions).

10) Granularity, time span, and quality
  - Aim for annual time series from 2010–present where possible to capture pre/post-COVID trends.
  - Prefer state-level as a baseline; county-level where available for hotspot mapping.
  - Track known biases (self-report vs. claims) in the data dictionary.

References & access portals (quick-start)
  - CDC Data & APIs (Data.CDC.gov)
  - CDC WONDER (wonder.cdc.gov)
  - BRFSS & YRBSS pages on CDC site
  - AHRQ HCUP online data tools
  - ACS / Census APIs

Priority next steps for dataset collection:
- Download BRFSS and ACS tables for target states/counties and load raw CSVs into a `data/raw/` folder.
- Acquire CDC WONDER suicide counts for the same geographies and time span.
- If access available, request HCUP state discharge or ED tables for trending utilization metrics.
