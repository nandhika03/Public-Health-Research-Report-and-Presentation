## Public-Health-Research-Report-and-Presentation - Geospatial Influenza Impact Analysis (United States, 2018–2019)

### Overview
This project analyzes the spatial distribution of influenza activity in the United States during the 2018–2019 flu season using geospatial analysis and basic statistical modeling. The study integrates CDC influenza surveillance data, U.S. Census multigenerational household data, and state-level boundaries to explore geographic clustering patterns and potential social vulnerability factors. ArcGIS Pro 3 was used for spatial analysis and visualization, and Python was used for data cleaning, aggregation, and exploratory modeling.

---

### Key findings
![img](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/blob/main/Maps/hotspotanalysis.jpeg)
![img](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/blob/main/Maps/whereflufindsahome.png)
- **Hotspot analysis (Getis-Ord Gi\*)** identified statistically significant clustering of high flu positivity rates in several **Southeastern U.S. states** (e.g., Georgia, Alabama, Mississippi) and low-activity clusters in parts of the **Northern Plains**.
- **Choropleth maps of mean lab-confirmed flu positivity** showed clear regional variation, but **multigenerational household percentage exhibited weak correlation** with flu positivity at the state level.
- **Random Forest regression** failed to meaningfully predict state-level flu positivity (**R² = -0.46, RMSE = 2.46**), confirming limited predictive signal in the selected features.

> Key figures referenced in the report:
> - Overall Flu Positivity Map (state-level)
> - Hotspot Analysis Map (Getis-Ord Gi\*)

[Link to final report PDF](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/blob/main/Maps/HOTSPOT.pdf)
[Link to figures directory](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/tree/main)

---

### Data Sources
- **U.S. State Boundary Shapefile**  
  Source: U.S. Census Bureau – Cartographic Boundary Files  
  [Census boundary file link](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/blob/main/Data/US_state_outofgis.csv)

- **ILINet (CDC FLUVIEW)**  
  Weekly Influenza-like Illness (ILI) surveillance data (2018–2019 season)  
  [CDC FLUVIEW data link](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/blob/main/Data/Cleaned_Datasets.zip)

- **ICL NREVSS Clinical Labs (CDC)**  
  State-level laboratory-confirmed influenza testing results  
  [DC Clinical Labs data link](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/blob/main/Data/Cleaned_Datasets.zip)
  
- **Multigenerational Household Data (ACS 2018)**  
  Table B11017 from data.census.gov  
  [ACS table link](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/blob/main/Data/Multigen_HH_Cleaned.csv)

---

### Data Cleaning and Feature Engineering
- Removed zero-variance and non-informative columns (e.g., Region Type, fully missing % Weighted ILI).
- Dropped rows containing non-numeric placeholder values (`X`) in lab datasets (531 rows removed).
- Engineered a **Season_Week** variable to standardize CDC flu season timing:

- Final datasets:
- ILINet: **2809 × 7**
- Clinical Labs: **2278 × 9**

[Placeholder: Link to cleaned datasets]

---

### Methodology
1. Imported cleaned CSVs and U.S. state boundaries into **ArcGIS Pro 3**.
2. Addressed one-to-many relationships by aggregating weekly data to **season-level state summaries** using geodatabases.
3. Aggregated metrics:
 - ILINet: total ILI cases, total patients (sum), % unweighted ILI (mean)
 - Clinical Labs: total specimens, Influenza A/B counts (sum), positivity rates (mean)
4. Joined aggregated tables to state boundaries using **Join Field**.
5. Produced spatial visualizations:
 - Choropleth maps (graduated colors)
 - Proportional symbol overlays
 - Hotspot analysis using **Getis-Ord Gi\***
6. Conducted exploratory data analysis and tested a **Random Forest regression model** in Python.

[Link to Python notebooks](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/tree/main)

---

### Exploratory Data Analysis
- Strong correlation observed between **ILI case counts and total patient volume**, as expected.
- Weak or negligible linear relationship between **multigenerational household percentage** and **mean lab-confirmed flu positivity**.
- Feature distributions were skewed, reflecting population differences across states.

[Link to EDA code](https://github.com/nandhika03/Public-Health-Research-Report-and-Presentation/tree/main)

---

### Machine Learning Experiment
- Model: Random Forest Regression
- Target: Mean lab-confirmed flu positivity
- Performance:
- **R²:** -0.46
- **RMSE:** 2.46
- Outcome: Model performance was poor; results were not used for mapping or inference.

---

### Limitations
- Analysis conducted at the **state level**, which may mask localized patterns.
- Only **one flu season (2018–2019)** analyzed.
- Environmental variables (temperature, humidity) and vaccination rates were not fully integrated.
- Multigenerational household structure alone is insufficient to explain flu positivity patterns.

---

### Future Work
- Incorporate healthcare access, vaccination coverage, and socioeconomic indicators.
- Extend analysis across multiple flu seasons.
- Perform finer-scale analysis at the **county or metropolitan level**.
- Explore time-series or spatial regression approaches.

---

### Authors
- **Nandhika Rajmanikandan** – MS Data Science, Michigan Technological University  
- **Frank Ofusu** – MS Health Informatics, Michigan Technological University  

---

### License
This project is intended for educational and non-commercial use. Attribution is appreciated.

