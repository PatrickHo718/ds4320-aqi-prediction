# DS 4320 Project 2: AQI Prediction

### Executive Summary

This README now documents a Air Quality Prediction Project for DS-4320 that includes details on name, NetID, DOI, links, and license. It also contains a defined problem statement, rationale, a terminology table, readings, implicit schema, and data dictionary to provide more context to the project.

<br>

<br>

---

### Name - Mu Patrick Ho
### NetID - bqu3tr
### DOI - [![DOI](https://zenodo.org/badge/1177391857.svg)](https://doi.org/10.5281/zenodo.19337554)
### Press Release
[**Tomorrow's Air: A Machine Learning Tool That Predicts Whether the Air You Breathe Will Be Safe**](https://github.com/PatrickHo718/ds4320-aqi-prediction/blob/main/press-release/press-release.md)
### Pipeline - [analysis code](https://github.com/PatrickHo718/ds4320-aqi-prediction/blob/main/code/pipeline.ipynb)
### License - [MIT](LICENSE)


---
<br>

<br>

## Problem Definition
### General and Specific Problem
* **General Problem:** Predicting air quality.
* **Specific Problem:** Given historical measurements of atmospheric pollutants (PM2.5, PM10, ozone, NO₂, CO, SO₂) and meteorological conditions (temperature, wind speed, humidity) for a set of US cities, can we predict the next-day Air Quality Index (AQI) category being Good, Moderate, Unhealthy for Sensitive Groups, Unhealthy, or Very Unheathy using a multi-class classification model?

### Rationale
The general problem of predicting air quality is intentionally broad as it could apply to any geography, any time horizon, any output format, and any set of input features. Refinement was necessary to make the problem tractable and practically useful. The decision to focus on next-day AQI category rather than a raw AQI score was driven by how forecasts are actually communicated to the public. Framing this as a multi-class classification task aligns the model output directly with the form that end-users receive and act on. The scope was further limited to US cities because the EPA AQS API provides well-documented and publicly accessible data at that level, removing data acquisition barriers and ensuring high data quality for a first project of this type. Restricting to daily granularity reduces noise and aligns with the forecasting horizon that is most actionable for the general public.

### Motivation
Air quality is one of the main environmental determinants of public health. The American Lung Association estimates that nearly half of all Americans live in counties with unhealthy levels of air pollution on at least some days of the year. Poor air quality is associated with increased rates of asthma, cardiovascular disease, and death. The burden that falls disproportionately on low-income communities and communities of color, who are more likely to live near industrial sources of pollution. Despite this, most people have little advance warning of bad air quality days and cannot plan accordingly. A reliable next-day AQI prediction tool could allow vulnerable individuals, such as those with asthma, the elderly, children, to proactively limit outdoor exposure, adjust medication, or seek cleaner indoor environments. This project addresses that gap by building a model trained on real EPA monitoring data.
### Press Release Headline and Link
[**Tomorrow's Air: A Machine Learning Tool That Predicts Whether the Air You Breathe Will Be Safe**](https://github.com/PatrickHo718/ds4320-aqi-prediction/blob/main/press-release/press-release.md)

<br>

<br>

---

## Domain Exposition

### Terminology

| Term | Definition |
|------|------------|
| **AQI (Air Quality Index)** | A standardized 0-500 scale used by the EPA to communicate daily air quality risk to the public. |
| **PM2.5** | Fine particulate matter with aerodynamic diameter ≤ 2.5 micrometers. A primary driver of AQI and a key health-risk pollutant that penetrates deep into the lungs. |
| **PM10** | Coarser particulate matter with aerodynamic diameter ≤ 10 micrometers. Less dangerous than PM2.5 but still regulated under NAAQS. |
| **Ozone (O₃)** | A secondary pollutant formed when NOₓ and volatile organic compounds react in sunlight. A major component of urban smog measured at ground level. |
| **NO₂ (Nitrogen Dioxide)** | A primary pollutant produced by vehicle exhaust and industrial combustion. A key indicator of traffic-related air pollution. |
| **CO (Carbon Monoxide)** | A colorless, odorless gas produced by incomplete combustion of fossil fuels. At high concentrations it reduces blood oxygen levels. |
| **SO₂ (Sulfur Dioxide)** | Produced primarily by burning coal at power plants and industrial facilities. Linked to respiratory illness and acid rain formation. |
| **NAAQS** | National Ambient Air Quality Standards — EPA-set concentration limits for criteria pollutants in outdoor air, established under the Clean Air Act. |
| **AQS (Air Quality System)** | The EPA's central database of ambient air quality data collected from thousands of regulatory monitors across the US, storing over 3 billion measurements dating back to 1957. |
| **AQI Category** | One of five plain-language risk tiers derived from the AQI value: Good (0-50), Moderate (51-100), Unhealthy for Sensitive Groups (101-150), Unhealthy (151-200), Very Unhealthy (201-300). |
| **Multi-class Classification** | A supervised ML task where the model predicts one of more than two discrete output classes — here, the five AQI categories. |
| **Random Forest** | An ensemble ML algorithm that builds multiple decision trees on data subsets and aggregates their predictions, shown to achieve 70-90% accuracy in AQI prediction tasks. |
| **Census Block Group** | The smallest geographic unit used by the US Census Bureau for which demographic data is published. |
| **FRM / FEM** | Federal Reference Method / Federal Equivalent Method — EPA-designated measurement methods whose data is used for regulatory compliance determinations under the Clean Air Act. |

### Domain
This domain of this project is concentrated on environmental science and public health. Air quality monitoring is a scientific field governed by the Environmental Protection Agency, which has operated the Air Quality System (AQS) monitoring network since the 1970s. The AQS network currently includes thousands of monitoring stations across all 50 states, collecting hourly or daily readings of criteria pollutants as defined under the Clean Air Act. The AQI was developed as a public communication tool, which is a single number that distills complex multi-pollutant measurements into an easily understandable health risk indicator.

### Reading
| Title | Description | Link |
|-------|-------------|------|
| "Racial and Ethnic Disparities in Regulatory Air Quality Monitor Locations in the US" | Study of 329M US residents finding that EPA regulatory monitors are inequitably distributed across racial and ethnic groups. | [link](https://myuva-my.sharepoint.com/:b:/g/personal/bqu3tr_virginia_edu/IQAfIrk_1nCdSocvnt1DrBaZAadSYqtFsBGIXai9h5HIE2g?e=Vbr3Xd) |
| "About AQS Data" | Official EPA documentation explaining the structure, contents, temporal scope, and data handling procedures of the AQS database. | [link](https://myuva-my.sharepoint.com/:b:/g/personal/bqu3tr_virginia_edu/IQDRHVfG8BjqR48LLBwFaBxUAUWpCp1BBBza3GyMC6uZ88k?e=uTcD01) |
| "Air Quality Prediction using Machine Learning Algorithms: A Review" | Compares ML algorithms  applied to AQI prediction across multiple studies.  | [link](https://myuva-my.sharepoint.com/:b:/g/personal/bqu3tr_virginia_edu/IQBfCWKTpyZPTpWSVoy0F-rQAe1OR-tsvxhECb5VqHqVhAk?e=ni7Lav) |
| "Air Quality Prediction: Big Data and Machine Learning Approaches" | Covers Genetic Algorithm-ANN, Random Forest, Deep Belief Network, and SVM approaches for air quality. | [link](https://myuva-my.sharepoint.com/:b:/g/personal/bqu3tr_virginia_edu/IQB6H8ayN6PwQLxb16U9vCv0AbOrkp5ekaxCD8gd9EMZQRk?e=3m9etI) |
| "State of the Air 2023" | Annual report documenting air quality trends and health impacts across US cities. | [link](https://myuva-my.sharepoint.com/:b:/g/personal/bqu3tr_virginia_edu/IQBZ0BuAXtqhQpLEg1D498uIAUYxI8N6m4kcTxrUwKh7itk?e=h8CzMR) |

---
<br>

<br>

## Data Creation

### Data Provenance

The dataset from the United States Environmental Protection Agency's Air Quality System (AQS) is accessed programmatically through the AQS REST API, which returns JSON-formatted records for daily summary statistics by county, pollutant, and date range. Each API response record represents one daily observation at one monitoring site and includes the site's geographic coordinates, the daily mean and maximum PM2.5 concentration, the raw AQI value, and associated metadata such as the measurement method, observation count, and observation completeness percentage.

Data is retrieved with a Python script that loops over each county-year combination, shapes each raw API record into a structured MongoDB document with nested subdocuments for pollutant readings, AQI, and location, and inserts all documents into a MongoDB Atlas collection. The AQI category label (Good, Moderate, Unhealthy for Sensitive Groups, Unhealthy, Very Unhealthy, Hazardous) is derived programmatically from the raw AQI integer value using the EPA's standard breakpoint thresholds since the AQS daily summary endpoint does not return a pre-labeled category field. A five-second delay between API calls is enforced to respect the AQS Data Mart rate limit.

### Code

| File | Description | Link |
|------|-------------|------|
| `fetch_insert.ipynb` | Connects to EPA AQS API, fetches daily PM2.5 summary records by county and year, derives AQI category labels, and bulk-inserts documents into MongoDB Atlas | [fetch_insert.ipynb](https://github.com/PatrickHo718/ds4320-aqi-prediction/blob/main/code/fetch_insert.ipynb) |

### Bias Identification

First, spatial coverage bias occurs when the AQS network does not cover all populations. Kelly et al. (2024) found that relative to White non-Hispanic populations, all other racial groups are associated with fewer PM monitors per capita. Because this project draws data only from counties with established monitoring infrastructure, the resulting dataset overrepresents communities that are already well-monitored and cannot capture air quality conditions in undermonitored locations. Second, monitor siting bias is present because individual monitors are placed to meet regulatory siting requirements rather than to be spatially representative of all residents within a county. A single monitor reading is interpolated to represent an entire county, which introduces uncertainty especially in large or geographically heterogeneous counties like Los Angeles. Third, multi-monitor aggregation bias happens when many counties have multiple nearby monitors measuring the same pollutant. The API returns monitor-level records, so counties with denser monitoring infrastructure will contribute more documents to the dataset, potentially over-weighting certain geographic areas in model training.

### Bias Mitigation

To address spatial coverage bias, the project selects cities with dense, well-established monitoring networks (Los Angeles, New York, Houston, Chicago, Phoenix) where monitor coverage is relatively consistent, but this method itself can be a selection bias. To address multi-monitor aggregation bias, a deduplication step in the pipeline groups records by city and date and takes the daily mean AQI across all monitors before modeling, ensuring each city-day combination contributes exactly one observation to the training set. Monitor siting bias is inherently difficult to eliminate without supplementary spatial data, but its effect can be quantified by reporting prediction uncertainty as a function of the number of active monitors per city-day. For example, days with more active monitors should yield more reliable AQI estimates and lower model uncertainty.

### Rationale

**Choice of PM2.5 as the sole pollutant:** PM2.5 is the most monitored criteria pollutant across all five target cities and is the most common driver of elevated AQI values in urban US settings. Using a single pollutant simplifies the data model and reduces the number of API calls required, while still producing a meaningful and actionable prediction target.

**Choice of five specific cities:** Los Angeles, New York, Houston, Chicago, and Phoenix were selected because they represent geographic, climatic, and demographic diversity across the US and all have dense, long-running monitoring networks that reliably produce daily observations. This maximizes data completeness and minimizes missing-value imputation.

**Two-year date range (2022-2023):** Two calendar years provides enough observations to train a classification model with reasonable coverage of seasonal variation, while staying within AQS's one-year-per-API-call limit. Data from 2022-2023 is also sufficiently recent to reflect current monitoring infrastructure and post-pandemic traffic and emissions patterns.

**Deriving AQI category from raw AQI integer:** The AQS daily summary API does not return a pre-labeled category field. The EPA's breakpoint thresholds (0-50 Good, 51-100 Moderate, etc.) are applied deterministically, so the derived label is exact and introduces no additional uncertainty beyond what is already present in the underlying PM2.5 measurement.

<br>

<br>

---

### Implicit Schema

Each document in the daily_aqi collection follows the structure below. All fields are present in every document; no fields are optional. Nested subdocuments are used to logically group related fields.

```
{
  "city": "<string> — city label assigned during data acquisition",
  "date": "<string> — date of observation in YYYY-MM-DD format (local standard time)",
  "location": {
    "lat": "<float> — latitude of the monitoring site in decimal degrees (NAD83)",
    "lon": "<float> — longitude of the monitoring site in decimal degrees (NAD83)",
    "site": "<string> — local name of the monitoring site as recorded in AQS",
    "address": "<string> — street address of the monitoring site"
  },
  "pollutant": {
    "parameter": "<string> — full parameter name as returned by the AQS API",
    "units": "<string> — unit of measure for concentration values",
    "mean": "<float> — arithmetic mean PM2.5 concentration for the 24-hour period",
    "max_value": "<float> — maximum PM2.5 concentration recorded during the day",
    "max_hour": "<int> — hour of day (0-23) at which the daily maximum occurred"
  },
  "aqi": {
    "value": "<int> — raw AQI integer calculated from the daily PM2.5 concentration",
    "category": "<string> — AQI category label derived from value using EPA breakpoints"
  },
  "observation_count": "<int> — number of individual samples contributing to the daily summary",
  "observation_percent": "<float> — percentage of expected observations that were actually recorded",
  "source": "<string> — always 'EPA AQS API'; documents the data origin"
}
```

### Data

| Collection | Description |
|------------|-------------|
| `daily_aqi` | Daily PM2.5 AQI observations at the monitor level for Los Angeles, New York, Houston, Chicago, and Phoenix covering 2022-2023.|

### Data Dictionary

| Feature | Data Type | Description | Example |
|---------|-----------|-------------|---------|
| `city` | string | City label assigned during ingestion corresponding to the target county | `"Los Angeles"` |
| `date` | string | Date of observation in ISO 8601 format (YYYY-MM-DD) | `"2022-06-15"` |
| `location.lat` | float | Latitude of the monitoring site (datum: NAD83) | `34.669739` |
| `location.lon` | float | Longitude of the monitoring site (datum: NAD83) | `-118.130511` |
| `location.site` | string | Local name of the monitoring site as recorded in AQS | `"Lancaster-Division Street"` |
| `location.address` | string | Street address of the monitoring site | `"43301 DIVISION ST., LANCASTER, CA"` |
| `pollutant.parameter` | string | Full parameter name as returned by the AQS API | `"PM2.5 - Local Conditions"` |
| `pollutant.units` | string | Unit of measure for all concentration values in this document | `"Micrograms/cubic meter (LC)"` |
| `pollutant.mean` | float | Arithmetic mean PM2.5 concentration across all samples in the 24-hour period | `8.5` |
| `pollutant.max_value` | float | Maximum PM2.5 concentration recorded at any hour during the day | `12.3` |
| `pollutant.max_hour` | integer | Hour of day (0-23, local standard time) at which the daily maximum occurred | `14` |
| `aqi.value` | integer | Raw AQI integer calculated by the EPA from the daily PM2.5 mean concentration | `47` |
| `aqi.category` | string | AQI risk category derived from `aqi.value` using EPA standard breakpoints | `"Good"` |
| `observation_count` | integer | Number of individual sub-daily samples that contributed to the daily summary | `1` |
| `observation_percent` | float | Percentage of expected observations that were actually recorded (completeness indicator) | `100.0` |
| `source` | string | Origin of the data record; always `"EPA AQS API"` for all documents in this collection | `"EPA AQS API"` |

**Note:** The data dictionary above describes fields as stored in MongoDB. The analysis pipeline derives additional features at query time (yesterday's PM2.5 mean and max, AQI lag, 3-day and 7-day rolling averages) that do not appear in the raw documents. 

### Quantification of Uncertainty

| Feature | Count | Mean | Median | Std | Min | Max | Q1 | Q3 | IQR | Missing | Missing % |
|---|---|---|---|---|---|---|---|---|---|---|---|
| `aqi.value` | 447,236 | 45.499 | 47.0 | 17.554 | 0.0 | 223.0 | 32.0 | 56.0 | 24.0 | 46,380 | 9.4% |
| `observation_count` | 493,616 | 3.130 | 1.0 | 6.633 | 1.0 | 24.0 | 1.0 | 1.0 | 0.0 | 0 | 0.0% |
| `observation_percent` | 493,616 | 99.873 | 100.0 | 2.057 | 4.0 | 100.0 | 100.0 | 100.0 | 0.0 | 0 | 0.0% |
