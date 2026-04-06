# 🇮🇳 Household Consumption Expenditure Survey (HCES) 2022-23 — MPCE Analysis

> **Course:** Communicating Economics | MA Economics — Semester 2  
> **Assignment:** Data Visualisation — Recreating graphs from the *Data for India* dashboard

---

## 📌 Overview

This project analyses India's **Household Consumption Expenditure Survey (HCES) 2022-23** data to estimate **Monthly Per Capita Consumption Expenditure (MPCE)** — one of the most widely used measures in poverty assessment.

The analysis recreates key visualisations from the [Data for India](https://www.dataforindia.com/) dashboard using raw survey microdata and population weights.

---

## 📊 Visualisations

### A. Average Household & Per Capita Monthly Consumption Expenditure
- Average Monthly Household Consumption Expenditure across India
- Average MPCE (Monthly Per Capita Consumption Expenditure) across India
- Broken down by **rural and urban** sectors

### B. Average MPCE by Consumption Quintiles
- Population divided into 5 consumption classes (quintiles)
- Shows inequality in consumption expenditure across the distribution
- Computed using the `cut()` function in R

### C. Average MPCE by Social Group
- Disaggregated by social categories (SC, ST, OBC, Others)
- Highlights consumption disparities across social groups in India

---

## 🗂️ Data Sources

| File | Description |
|------|-------------|
| `Level 3` (.dta) | Household social characteristics (social group, religion) |
| `Level 14` (.dta) | Household consumption values (Food, Consumables, Durables) |
| `Level 15` (.dta) | Household size by questionnaire visit |
| `tabulation_state_code.xlsx` | State code to state name mapping |

> ⚠️ **Raw data files are not included** in this repository due to file size limits.  
> They can be downloaded from the [MoSPI HCES 2022-23 portal](https://mospi.gov.in/web/mospi/download-tables-data/-/reports/view/templateTwo/25706?q=results-table).

---

## ⚙️ Methodology

### MPCE Calculation

1. **Expenses standardised to 30 days:**
   - 7-day items → multiplied by `30/7`
   - 30-day items → used directly
   - 365-day items → multiplied by `30/365`

2. **Three expenditure categories combined:**
   - Food (`Questionnaire F`) — Section A1
   - Consumables (`Questionnaire C`) — Section B1 *(item 539 excluded — imputed rent)*
   - Durables (`Questionnaire D`) — Section C1

3. **Weighted averages** used throughout to ensure national/state representativeness:

```r
MPCE = sum(TE * Weights) / sum(Household.Size.F * Weights)
```

### Population Weights
Sample weights (`mult / 100`) are applied to all averages so results are representative at the national level, not just sample averages.

---

## 🛠️ Tools & Packages

- **Language:** R
- **Packages:** `tidyverse`, `dplyr`, `ggplot2`, `haven`, `readxl`
- **Visualisation:** `ggplot2`

---

## 📁 Repository Structure

```
📦 hces-mpce-analysis/
├── 📄 README.md
├── 📄 mpce_analysis.R              # Main R script
├── 📄 Communicating-economics.html # Full analysis output
├── 📄 Data_for_India.html          # Dashboard recreation
└── 📄 Assignment_Brief.pdf         # Original assignment instructions
```

---

## 📈 Key Findings

- India's average MPCE (2022-23) is approximately **₹3,773** (rural) and **₹6,459** (urban)
- Significant consumption inequality exists across quintiles — the top quintile consumes several times more than the bottom
- Consumption gaps across social groups reflect broader structural inequalities in the Indian economy

---

## 📚 References

- Ministry of Statistics & Programme Implementation (MoSPI). *Household Consumption Expenditure Survey 2022-23.* Government of India.
- Data for India Dashboard: [dataforindia.com](https://www.dataforindia.com/)
- HCES 2022-23 Report — Chapter 2: Survey Design & MPCE Estimation Methodology

---

## 👤 Author

**Ravi S**  
MA Economics | Semester 2  

---

*This project was completed as part of the Communicating Economics course. All analysis and visualisations are original work based on publicly available government survey data.*
