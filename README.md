# ds4320-aqi-prediction

# DS-4320-Project-1: Detecting Credit Card Fraud

### Executive Summary

This README now documents a Credit Card Fraud Project for DS-4320 that includes details on name, NetID, DOI, links, and license. It also contains a defined problem statement, rationale, a terminology table, readings, implicit schema, and data dictionary to provide more context to the project.

<br>

<br>

---

### Name - Mu Patrick Ho
### NetID - bqu3tr
### DOI - 
### Press Release
[**Tomorrow's Air: A Machine Learning Tool That Predicts Whether the Air You Breathe Will Be Safe**](url)
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
[**Tomorrow's Air: A Machine Learning Tool That Predicts Whether the Air You Breathe Will Be Safe**](url)

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

### Code


### Bias Identification


### Bias Mitigation


### Rationale


<br>

<br>

---

### Implicit Schema

### Data

### Data Dictionary

### Quantification of Uncertainty
