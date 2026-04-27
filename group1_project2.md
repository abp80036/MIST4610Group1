
# Group 1 Project 2

### Team Members
#### Lauren Harville - @4610LaurenGit
#### Andrew Heighton - @AndrewHeighton
#### Asanti Kumera - @asanti00
#### Aidan Pfeiffer - @abp80036
#### Doc Rush - @docrush
#### Violet Sofish - @VioletSofish


## Dataset Description
#### Database: COVID19_EPIDEMIOLOGICAL_DATA 
For this project, our team chose the COVID-19 Epidemiological dataset from the Snowflake Marketplace. We were drawn to it because it’s real-world data that has impacted numerous people across the world, so it feels more meaningful to work with compared to something more abstract. It also covers countries across the globe and tracks how things changed over time, which gives us a lot to explore and analyze when creating our questions and charts. We also liked that the dataset is fairly large and detailed. It’s not something where you can just pull one column and get an answer right away. Instead, we are able to look at trends, compare different regions, and really dig into the data.

#### Table: WHO_TIMESERIES
- 10 columns
- 238 rows

## Questions and Justification

### Question 1: Case Fatality Rate (CFR) by Country 
#### What is the probability of dying after contracting COVID-19?
Why it's meaningful: This question reveals global disparities in healthcare quality, demographics, and pandemic response by measuring outcomes rather than just case counts. It helps policymakers and researchers understand where COVID-19 was most and least deadly relative to confirmed infections.

Why it's non-trivial: CFR requires aggregating deaths and confirmed cases per country to compute a derived metric (SUM(deaths) / SUM(confirmed_cases)) * 100, then dynamically ranking and filtering results based on user input.

Columns/Tables used: CONFIRMED_CASES, DEATHS, COUNTRY_REGION

Interactive elements: Users toggle between most likely and least likely countries and control how many are displayed at once.

### Question 2: 
#### How many COVID-19 vaccinations were administered over time, by day?
Why it's meaningful: A time-series view of daily vaccinations reveals key inflection points in the global pandemic response — such as supply ramp-ups or booster campaigns — and allows meaningful comparison across countries and regions.

Why it's non-trivial: This requires time-series aggregation, date-based grouping, and dynamic country/region filtering — far beyond a simple lookup.

Columns/Tables used: ECDC_GLOBAL_WEEKLY, DATE, DAILY_VACCINATIONS, COUNTRY/REGION

Interactive elements: Users filter by country or region to isolate and compare vaccination rollout trends across different areas.

## Data Manipulations

Interactive Elements
### 1. Top N Slider (Mortality Chart) 
Controls how many countries appear in the bar chart (5–30). It rewrites the SQL LIMIT clause dynamically. Analytical value: the original hard-coded top 10 hides whether the next 10–20 countries have meaningfully different fatality rates, which matters for identifying regional patterns or outliers beyond the worst cases.
### 2. Country/Location Multi-Select (Vaccination Chart)
Filters the vaccination query using WHERE LOCATION IN (...). Analytical value: global totals mask huge regional disparities — isolating specific countries lets you compare the shape and timing of their roll-out curves directly against each other, which is invisible in an aggregate view.
### 3. Date Range Picker (Vaccination Chart) 
Adds WHERE DATE BETWEEN ... AND ... to the vaccination query. Analytical value: the full 2020–2023 range compresses early variation and makes the initial rollout look flat. Zooming into Q1 2021 reveals the early race to vaccinate; zooming into 2022 exposes booster campaign dynamics.
## Analysis and Results

### Chart 1 — Case-Fatality Rate (Bar Chart) 
Pulls from WHO_TIMESERIES and divides DEATHS_TOTAL_PER_100000 by CASES_TOTAL_PER_100000 to estimate how lethal COVID was relative to confirmed cases in each country. Originally hard-coded to show 10 countries.
<img width="3252" height="842" alt="image" src="https://github.com/user-attachments/assets/62f0eabd-45b7-4893-8b8b-7c0309922fec" />

### Chart 2 — Vaccinations Recorded Per Day (Area Chart) 
Pulls from OWID_VACCINATIONS and counts vaccination records grouped by date, showing the global roll-out trend over time.
<img width="3228" height="850" alt="image" src="https://github.com/user-attachments/assets/61820d9c-80a6-410f-bc12-27aae578b852" />


## Streamlit App



## AI Assistance Documentation
### What was prompted: 
The original Phase 2 app.py was provided and Claude was asked to reproduce both charts, add meaningful interactive filters, and improve the visual design.
### What changed: 
Parameterized SQL driven by UI state replaced hard-coded queries; a sidebar with three controls was added; a dark custom theme with KPI metric cards under each chart was introduced; duplicate-column handling was refactored into a shared helper.
### What was modified/rejected: 
@st.fragment wrappers were removed in favor of cleaner sidebar-driven reruns. A plotly migration was rejected to stay within Snowflake's sandboxed runtime. The CONTINENT column was corrected to LOCATION after a SQL compilation error revealed it didn't exist in the table. A execute_query.clear() call was added at startup to bust stale cached query IDs from earlier broken versions.


Case-Fatality Rate
<img width="3350" height="1749" alt="image" src="https://github.com/user-attachments/assets/5ada334f-79a0-43af-97fb-dfc6b71976dc" />


Vaccinations Recorded Per Day (Global Information off 10000 data points):
<img width="3338" height="1765" alt="image" src="https://github.com/user-attachments/assets/a2fa9e56-5385-4c77-873f-7b0923619b36" />


Vaccinations Recorded Per Day (With Selected Countries):
<img width="3280" height="1733" alt="image" src="https://github.com/user-attachments/assets/5707e79b-f203-4081-a5c2-81e0d7a2ff21" />

