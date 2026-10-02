# COVID-19 Global Impact & Vaccination Analysis 🦠📊

**Author:** Mohammad Samreen  
**Role:** Data Science Intern @ Veda Technologies (Project 2)  
**Tech Stack:** Python (Pandas, NumPy), Google Colab, Power BI  

## 📑 Project Overview
This analysis evaluates the global trajectory of the COVID-19 pandemic, focusing specifically on the correlation between vaccination rollout speeds and the subsequent impact on case fatality rates (CFR) and total mortality. 

By engineering a robust data pipeline in Python and deploying an interactive dashboard in Power BI, this analysis moves beyond raw case tracking to answer a core analytical question: *Did mass immunization successfully decouple infection waves from mortality spikes?*

## 🗄️ Dataset
* **Source:** [Our World in Data (OWID)](https://ourworldindata.org/coronavirus)
* **Format:** Compact COVID-19 Dataset (CSV)
* **Scale:** Over 600,000+ rows spanning global daily reporting from 2020 to present.

## ⚙️ Methodology & Data Engineering
The raw dataset was processed using a custom Python pipeline to ensure data integrity and standardize reporting metrics. Key operations included:

1. **Data Cleansing:** 
   * Filtered out aggregate regional data (e.g., 'World', 'Europe') to isolate country-level metrics.
   * Handled missing daily reporting values using forward-filling (for cumulative totals) and zero-assumption techniques (for daily counts).
2. **Feature Engineering:**
   * **7-Day Rolling Averages:** Calculated to smooth out weekend reporting anomalies in new cases and deaths.
   * **Case Fatality Rate (CFR %):** Derived to track the lethality of the virus over time.
   * **Population Normalization:** Engineered "Per Million" metrics to allow for equitable benchmarking between countries of vastly different sizes.
   * **Doubling Time:** Calculated over a 7-day growth window.

## 📈 Power BI Dashboard Features
The resulting `cleaned_covid_data.csv` was ingested into Power BI to build an interactive, user-driven dashboard featuring:
* **Dynamic Slicers:** Filter by specific Country and Date ranges to isolate distinct pandemic waves.
* **KPI Summaries:** High-level cards tracking Maximum Total Cases, Maximum Total Deaths, Peak Vaccination Coverage, and Average CFR.
* **Wave Tracking:** A dual-axis line chart comparing case velocity against mortality velocity.
* **The Decoupling Visual:** A hybrid clustered-column and line chart proving the suppression of CFR (line) as vaccination percentages (columns) scale past 50%.

## 💡 Key Analytical Insights
1. **The Vaccine Decoupling Effect:** Once a country's vaccination coverage reached 50%–60%, the direct link between new case spikes and death spikes decoupled. Late 2021 and 2022 case surges produced significantly lower mortality peaks compared to earlier waves in 2020.
2. **CFR Stabilization Post-Rollout:** The Case Fatality Rate (CFR) was highly volatile and elevated during 2020 (averaging 4%–8% in early hotspots). Following global vaccine deployment, CFR steadily dropped and stabilized below 1.5% across most reporting nations.
3. **Per-Capita vs. Raw Numbers Discrepancy:** Relying solely on raw absolute totals misidentifies the hardest-hit regions. Normalizing by population reveals that several smaller nations experienced far higher per-capita mortality than larger countries with higher absolute counts.

## 🚀 How to Run the Project
1. **Data Pipeline:** Open `covid_data_pipeline.ipynb` in Google Colab or Jupyter Notebook and run all cells to fetch the live data from OWID and generate the cleaned CSV.
2. **Dashboard:** Open the `COVID19_Global_Impact.pbix` file in Power BI Desktop. Ensure the data source path points to your newly generated `cleaned_covid_data.csv`.
