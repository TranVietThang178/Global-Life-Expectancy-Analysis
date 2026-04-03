# 🌍 Global Determinants of Life Expectancy (2002–2022)
### A Multivariate Analysis Using an ELT Data Pipeline

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?logo=pandas&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-Public-E97627?logo=tableau&logoColor=white)
![Data Source](https://img.shields.io/badge/Data-Our%20World%20in%20Data-crimson)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📋 Overview

This project investigates the global determinants of life expectancy across **180+ countries from 2002 to 2022** by integrating seven open datasets into a unified analytical framework. A complete **Extract → Load → Transform (ELT)** pipeline was built in Python to merge, clean, and export the data, with exploratory analysis conducted in-notebook and interactive dashboards published on Tableau Public.

The project was completed as part of the **Data Operations & Management** module of the MSc in Data Science at **Atlantic Technological University**.

---

## 🔬 Research Questions

- How has global life expectancy changed from 2002 to 2022?
- Which socio-economic, healthcare, and environmental factors are most strongly associated with life expectancy?
- What actionable insights can inform public health policy?

---

## 📊 Interactive Dashboard

🔗 **[View the full interactive Tableau dashboard here](https://public.tableau.com/views/Life_Expectancy_Visualisation/Life_Expectancy_2002?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

Key dashboards include:
- **World Map Comparison** — Life expectancy by country in 2002 vs 2022
- **Change Map** — Life expectancy improvement per country over 20 years
- **GDP & Emissions** — Preston Curve relationship between income and health outcomes
- **Vaccination & Child Mortality** — Inverse relationship across four time periods
- **Healthcare Spending** — Spending vs outcomes coloured by income bracket
- **Diet Composition** — Macro-nutrient breakdown trends 2002–2022

---

## 🗂️ Repository Structure

```
life-expectancy-analysis/
│
├── README.md
│
├── notebook/
│   └── Life_Expectancy_Analysis.ipynb   # ELT pipeline + exploratory analysis
│
├── data/
│   └── life_expectancy_analysis.xlsx    # Cleaned unified dataset (180+ countries)
│
├── tableau/
│   └── screenshots/
│       ├── map_2002.png
│       ├── map_2022.png
│       ├── map_change.png
│       ├── gdp_vs_life_expectancy.png
│       ├── vaccination_child_mortality.png
│       ├── healthcare_spending.png
│       └── diet_composition.png
│
├── requirements.txt
│
├── LICENSE
│
├──.gitignore
│
└── report/
    └── Life_Expectancy_Report.pdf       # Full academic report
```

---

## 🛠️ Pipeline Architecture

```
┌─────────────────┐    ┌──────────────┐    ┌─────────────────┐
│     EXTRACT      │    │     LOAD     │    │    TRANSFORM    │
│                  │    │              │    │                 │
│ 7 CSV datasets   │───▶│ Pandas       │───▶│ • Inner merges  │
│ from OWID API    │    │ DataFrames   │    │ • Column rename │
│                  │    │              │    │ • Year filter   │
└─────────────────┘    └──────────────┘    │ • Country clean │
                                           └────────┬────────┘
                                                    │
                              ┌─────────────────────▼──────────────────┐
                              │              EXPORT & VISUALISE         │
                              │  Excel (.xlsx) → Tableau Public         │
                              └────────────────────────────────────────┘
```

---

## 📦 Datasets

All datasets sourced from [Our World in Data](https://ourworldindata.org), which aggregates data from WHO, World Bank, UN, FAO, UNICEF, and the Global Carbon Project.

| Dataset | Key Variable | Original Source |
|---|---|---|
| Life Expectancy at Birth | `Average Life Expectancy` | UN World Population Prospects |
| Vaccination Coverage | `DTP3 / MCV1 / POL3 (%)` | WHO / UNICEF (WUENIC) |
| GDP per Capita | `GDP per Capita (USD)` | World Bank (constant USD) |
| Healthcare Expenditure | `Health Spending per Capita` | WHO Global Health Expenditure DB |
| Diet Composition | `Calories by Macro-nutrient` | FAO Food Balance Sheets |
| CO₂ Emissions | `Total CO2 Emissions` | Global Carbon Project |
| Child Mortality Rate | `Child Mortality Rate` | Gapminder / UN IGME |

---

## 🔑 Key Findings

- **Global life expectancy rose by ~4 years** from 2002 to 2022, with the greatest gains in Sub-Saharan Africa, South Asia, and East Asia
- **GDP per capita** shows a strong log-linear (Preston Curve) relationship with life expectancy, with diminishing returns above ~$20,000/capita
- **Vaccination coverage** (DTP3, MCV1, POL3) increased consistently across all periods and is inversely correlated with child mortality — the strongest public health signal in the data
- **Healthcare spending** alone does not predict outcomes — system efficiency and governance matter more than expenditure level
- **CO₂ emissions** are strongly linked to economic development but show no direct short-term relationship with life expectancy
- **Dietary macro-nutrient composition** remained stable; total calorie intake rose steadily, with carbohydrates consistently representing ~62–63% of intake

---

## ⚙️ How to Run the Notebook

**Prerequisites**
```bash
pip install -r requirements.txt
```

**Run**
```bash
git clone https://github.com/YOUR_USERNAME/life-expectancy-analysis.git
cd life-expectancy-analysis
jupyter notebook notebook/Life_Expectancy_Analysis.ipynb
```

> The notebook fetches all datasets directly from the Our World in Data API — no manual downloads required. An internet connection is needed to run the Extract & Load section.

---

## 📁 Output

Running the notebook end-to-end produces `life_expectancy_analysis.xlsx` — a cleaned, merged dataset ready for import into Tableau or any other BI tool. The dataset contains:
- **180+ countries**
- **Up to 21 years** of observations per country (2002–2022)
- **13 variables** spanning health, economic, environmental, and nutritional domains

---

## ⚠️ Limitations

- Analysis is based on country-level averages, which may mask sub-national inequalities
- Inner merge strategy retains only countries with complete data across all seven datasets, which may bias results towards nations with stronger statistical reporting infrastructure
- Findings are correlational — causal relationships cannot be inferred without further modelling
- Dietary data are highly aggregated and may not capture meaningful within-country nutritional variation

---

## 📚 References

1. Our World in Data (2024). https://ourworldindata.org
2. World Bank (2024). *World Development Indicators*. https://databank.worldbank.org
3. WHO/UNICEF (2024). *WUENIC Immunization Coverage Estimates*
4. Global Carbon Project (2024). *Global Carbon Budget*. https://globalcarbonbudget.org
5. FAO (2024). *FAOSTAT Food Balance Sheets*. https://www.fao.org/faostat
6. Gapminder (2023). *Child mortality estimates*. https://www.gapminder.org

Full references available in the [project report](report/Life_Expectancy_Report.pdf).

---

## 👤 Author

**Viet Thang Tran**
MSc in Data Science — Atlantic Technological University
