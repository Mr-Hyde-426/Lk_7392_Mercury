# Lk_7392 // Mercury Platform
### Earth Observation Analytics & Land Viability Assessment Engine

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![NASA Open Science](https://img.shields.io/badge/Data-NASA%20Open%20Data-orange.svg)](https://earthdata.nasa.gov/)
[![C++ Core](https://img.shields.io/badge/C%2B%2B-20%20Core-00599C?logo=cplusplus)](https://isocpp.org/)
[![Python Service](https://img.shields.io/badge/Python-3.11%2B-3776AB?logo=python)](https://python.org/)
[![Database](https://img.shields.io/badge/PostgreSQL-PostGIS-336791?logo=postgresql)](https://postgis.net/)

**Democratizing orbital remote sensing for land-use decision-making and property protection.**

---

## 1. Mission Statement & Executive Summary

Project **Lk_7392** (commercially branded as **Mercury**) is a territorial intelligence and environmental assessment platform powered by open Earth observation datasets from orbital missions in GEO and LEO constellations.

Its core purpose is to **eliminate information asymmetry in land acquisition and occupancy**, transforming complex biophysical and meteorological satellite streams into intuitive, scientifically grounded, and accessible insights for everyday citizens, real estate appraisers, and environmental surveyors.

### Guiding Principles
1. **Knowledge Democratization:** Unrestricted, cost-free access to rapid parcel diagnostics for individual buyers and civil society.
2. **Scientific Rigor & Transparency:** Fully auditable formulas, data provenance, and processing pipelines compliant with **NASA Open Science** standards.
3. **Territorial Integrity:** Empirical technical support designed to prevent property and human loss caused by latent environmental hazards.

---

## 2. The Problem: Information Asymmetry in Real Estate

Space agencies such as **NASA**, **ESA**, and partner organizations distribute terabytes of Earth observation data daily with exceptional radiometric and temporal resolution. However:
* **Accessibility Barrier:** Raw feeds are distributed in dense matrix formats (GeoTIFF, NetCDF, HDF5) requiring advanced domain knowledge in Remote Sensing and Geographic Information Systems (GIS).
* **Hidden Vulnerabilities:** Homebuyers, agricultural producers, and land developers frequently acquire properties without insight into multi-year environmental behavior: chronic hydric stress, recurring surface heat anomalies, deforestation patterns, or nearby wildfire history.

---

## 3. System Mechanics & Analytical Metrics

### 3.1 Input Interfaces & Spatial Scale
* **Input Mechanisms:** GPS coordinates (Latitude/Longitude), interactive pinpointing on dynamic web maps, or GeoJSON parcel polygon ingestion.
* **Microenvironment & Influence Radius:** Due to spatial resolutions across public satellite sensors (ranging from 10 m to several kilometers), the engine performs decoupled assessments evaluating both the **target parcel** and its **surrounding influence radius** (calibrated between 1 and 5 km).

### 3.2 Land Viability Score (10-Level Indicator)
Mercury discards raw numerical matrices in favor of an integrated, weighted score scaled from **1 to 10**, supported by natural language diagnostic cards:
* **Wildfire Risk & Thermal Anomalies:** Historical and current proximity to active thermal anomalies and burn scars.
* **Land Surface Temperature (LST) Stress:** Extreme ground temperature deviations and seasonal microclimate heat islands.
* **Hydrologic Vulnerability & Drainage:** Multi-year drought patterns versus historical water accumulation and flood recurrence.
* **Atmospheric Quality & Aerosols:** Frequency of persistent particulate matter, smoke plumes, and tropospheric pollutants.
* **Vegetative Vigor & Canopy Dynamics:** Long-term soil degradation and desertification trends versus healthy, stable vegetative cover.

---

## 4. Operational Modes

* **Quick View Mode (Public Citizen Diagnostic):**
  * Instant, cost-free public lookup.
  * 1-to-10 Viability Indicator and concise diagnostic summaries (e.g., *"Parcel displays stable vegetative canopy and no recent thermal anomalies; local drainage review recommended due to historical runoff accumulation"* ).
* **Active Monitoring Mode (Real-Time Alerts):**
  * Spatial surveillance for registered parcel coordinates.
  * Automated early warnings for active thermal detections (last 24–48 hours via FIRMS), severe atmospheric plumes, or critical EONET events within the influence radius.
* **Historical Audit Mode (Mercury Audit):**
  * Comprehensive 5-to-10-year time-series reconstruction.
  * Interannual auditing of progressive canopy loss, chronic soil moisture depletion, and climate cyclicity.
  * Engineered as technical due-diligence documentation for appraisals, collateral risk assessments, and legal land validation.

---

## 5. Satellite Data Sources & NASA Open Science Compliance

The system operates strictly within **FAIR** (*Findable, Accessible, Interoperable, Reusable*) data principles, integrating public sensor pipelines:

| Environmental Vector | Sensor / Mission | Provider / Ingestion API |
| :--- | :--- | :--- |
| **Active fire detections & historical scars** | MODIS (Terra/Aqua), VIIRS (Suomi NPP) | **NASA FIRMS** |
| **Severe natural events & tracking** | Multi-mission orbital constellation | **NASA EONET** |
| **Land Surface Temperature (LST)** | Landsat 8/9 (TIRS), ECOSTRESS | **NASA Earthdata / AppEEARS** |
| **Soil moisture & agricultural drought** | SMAP (Soil Moisture Active Passive) | **NASA NSIDC / Earthdata** |
| **Precipitation & surface water dynamics** | GPM (IMERG), Landsat (NDWI), MODIS | **NASA DAACs** |
| **Atmospheric aerosols & smoke drift** | Sentinel-5P (Copernicus/NASA), TEMPO | **NASA GES DISC / Earthdata** |

---

## 6. Engineering & Software Architecture

The platform implements a decoupled, high-performance hybrid architecture:

* **Frontend Layer (Mercury UI):** Interactive cartographic interface for parcel bounding, diagnostic card rendering, and technical report exports.
* **Service & Data Layer (`lk-7392-service` - Python & PostGIS):**
  * Ingestion, schema validation, and caching of NASA REST APIs (JSON / GeoJSON).
  * Spatial-relational modeling of core domain entities (`Parcels`, `EnvironmentalReadings`, `HistoricalEvents`, `AuditReports`).
  * Optimized spatial indexing (R-Tree / GiST) running on PostgreSQL + PostGIS.
* **Compute Core (`lk-7392-core` - C++20 Engine):**
  * High-performance compiled engine operating without dynamic runtime overhead.
  * Direct execution of map algebra, spectral indices (NDVI, NDWI), and surface thermal anomaly transforms.
  * Deterministic calculation of the 10-Level Viability Index and vectorized multi-year time-series analysis.
* **Interoperability Bridge:** Zero-copy bindings via modern native interfaces (`pybind11` / C-ABI).

---

## 7. Ethics, Licensing & Legal Safeguards

### 7.1 Software License: GNU AGPLv3
This project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.
* **Network Copyleft:** If you modify, adapt, or incorporate this software into a network-accessible service or web API, you are legally required to make the complete source code available under this exact license (AGPL-3.0).
* **Anti-Enclosure Clause:** Proprietary fork encapsulation, closed-source commercial redistribution, or private software wrapping without source release is strictly prohibited.

### 7.2 Open Science & Public Data Ethical Policy
1. **Prohibition of Commercial Exploitation on Raw Data:** No individual or organization may charge for or restrict access to raw NASA Earth observation datasets ingested by this system. Satellite telemetry remains common public heritage.
2. **Fair Compute & Certification Boundaries:** Commercial monetization is strictly limited to verifiable cloud compute execution overhead, accredited human surveyor reviews, and official notarized documentation generated for commercial legal transactions.

### 7.3 Professional Disclaimer
*The Lk_7392 // Mercury platform provides technical diagnostic support based solely on historical remote sensing observations and public orbital sensors. It does not replace on-site geotechnical soil borings, precision topographic boundary land surveys, or structural engineering assessments. Neither the authors nor project contributors assume civil or commercial liability for third-party contractual, legal, or financial decisions derived from the use of this software.*

---

## 8. Authorship & Academic Lineage

* **Engineering & System Architecture:** Conceived, modeled, and developed within the Software Engineering / Computer Science curriculum, specializing in **Geospatial Database Modeling and High-Performance Scientific Computing**.
* **Organization:** Lk_7392 Initiative.
* **Scientific Collaboration:** Contributions and technical audits from the open-source community are welcomed via GitHub Pull Requests and Issues under AGPL-3.0 terms.
