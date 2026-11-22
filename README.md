# Global-Health-Insights-Onyx-Nov-2026

# 🌍 Global Health Insights
### Onyx DataDNA Dataset Challenge · November 2026

An interactive two-page healthcare analytics dashboard built in Microsoft Power BI, exploring pandemic impact on elective care performance and healthcare workforce pressure across 32 countries and 212 fictional health system regions.

![Power BI](https://img.shields.io/badge/Tool-Power%20BI-yellow)
![Analytics](https://img.shields.io/badge/Focus-Healthcare%20Analytics-blue)
![Challenge](https://img.shields.io/badge/Challenge-Onyx%20DataDNA-orange)
![Status](https://img.shields.io/badge/Project-Completed-green)

---

## 🖼️ Dashboard Preview

| Page | Description |
|---|---|
| Page 1 | Pandemic Impact & Elective Care Performance |
| Page 2 | Healthcare Workforce: Availability & Pressure |


<img width="1678" height="941" alt="image" src="https://github.com/user-attachments/assets/f6ca2c74-7c59-475c-8d29-bb678e2fdfdb" />

---

<img width="1680" height="940" alt="image" src="https://github.com/user-attachments/assets/add6b20a-3fbe-498b-a2ca-44cd91d05fd0" />


<!-- Add your dashboard screenshots below -->

<!--
![Page 1](Screenshots/Page_1.png)
![Page 2](Screenshots/Page_2.png)
-->

---

## 🏆 Challenge Brief

Built for the **Onyx DataDNA November 2026 Dataset Challenge**.

The objective was to analyse healthcare system performance before, during and after the pandemic, with a focus on elective care waiting times, recovery patterns, workforce availability, staffing vacancies and burnout.

The dashboard explores how healthcare systems experienced disruption and how workforce pressures evolved between 2018 and 2024.

---

## 📁 Dataset Overview

The dataset follows a star-schema approach, consisting of three dimension tables and two fact tables.

| Table | Rows | Description |
|---|---:|---|
| `dim_country` | 32 | Country information, WHO regions, income groups and healthcare models |
| `dim_date` | 28 | Quarterly date information, years, quarters and pandemic phases |
| `dim_health_system` | 212 | Fictional healthcare regions and system characteristics |
| `fact_health_performance` | 5,936 | Quarterly healthcare performance indicators |
| `fact_workforce` | 1,484 | Annual healthcare workforce survey records |

**Dataset Coverage:**
- 32 countries
- 212 fictional health system regions
- 2018–2024 reporting period
- 5,936 healthcare performance records
- 1,484 workforce records

---

## 📊 Page 1: Pandemic Impact & Elective Care Performance

This page analyses elective care waiting times and recovery patterns across countries and WHO regions.

### KPI Cards

- Waiting Time 2019
- Waiting Time 2021
- Waiting Time 2024
- Recovery Gap
- Average Waiting Time
- Waiting Time Increase
- Waiting Time Increase %

### Visualisations

| Visual | Description |
|---|---|
| Quarterly Elective Waiting Time Trend | Tracks quarterly waiting time changes from 2018 to 2024. |
| Top 10 Countries by Elective Waiting Time (2021) | Compares the countries with the highest waiting times in 2021. |
| Countries with the Highest Recovery Gaps (2024) | Highlights countries with the largest gaps against the pre-pandemic baseline. |
| Recovery Gap Across WHO Regions (2024) | Compares recovery gaps across WHO regions. |
| Top 3 Countries with the Highest Elective Waiting Times (2024) | Uses a doughnut chart to compare the three countries with the highest waiting times in 2024. |

### DAX Measures

<details>
<summary><strong>📈 Elective Care Measures (12 measures)</strong></summary>

```dax
Average Waiting Time =
AVERAGE(
    fact_health_performance[elective_wait_weeks]
)

Waiting Time 2019 =
CALCULATE(
    [Average Waiting Time],
    dim_date[year] = 2019
)

Waiting Time 2021 =
CALCULATE(
    [Average Waiting Time],
    dim_date[year] = 2021
)

Waiting Time 2024 =
CALCULATE(
    [Average Waiting Time],
    dim_date[year] = 2024
)

Waiting Time Increase =
[Waiting Time 2021] - [Waiting Time 2019]

Waiting Time Increase % =
DIVIDE(
    [Waiting Time Increase],
    [Waiting Time 2019]
)

Waiting Time Reduction =
[Waiting Time 2021] - [Waiting Time 2024]

Waiting Time Reduction % =
DIVIDE(
    [Waiting Time Reduction],
    [Waiting Time 2021]
)

Recovery Gap =
[Waiting Time 2024] - [Waiting Time 2019]

Pre-Pandemic Baseline =
CALCULATE(
    [Average Waiting Time],
    REMOVEFILTERS(dim_date),
    dim_date[pandemic_phase] = "Pre-Pandemic"
)

Waiting Time Change =
[Average Waiting Time] - [Pre-Pandemic Baseline]

Waiting Time Change % =
DIVIDE(
    [Waiting Time Change],
    [Pre-Pandemic Baseline]
)
```

</details>

---

## 👥 Page 2: Healthcare Workforce: Availability & Pressure

This page explores workforce availability, staffing shortages, international recruitment and burnout across healthcare systems.

### KPI Cards

- Average Doctors per 1,000
- Average Nurses per 1,000
- Average Vacancy Rate
- Average Burnout Index
- Average International Recruitment
- Total Workforce Records

### Visualisations

| Visual | Description |
|---|---|
| Country-Level Workforce Performance Table | Compares average doctors and nurses per 1,000 people across countries. |
| Workforce Pressure: Vacancy Rate vs Burnout Index | Scatter chart exploring the relationship between vacancy rates and workforce burnout. |
| International Recruitment Across Health Systems | Compares international recruitment percentages across countries. |
| Countries Facing the Highest Workforce Vacancy Rates | Highlights countries with higher workforce vacancy rates. |
| Healthcare Workforce Burnout: Annual Trend (2018–2024) | Displays the annual trend in the average burnout index. |

### DAX Measures

<details>
<summary><strong>🏥 Healthcare Workforce Measures (6 measures)</strong></summary>

```dax
Average Doctors per 1000 =
AVERAGE(
    fact_workforce[doctors_per_1000]
)

Average Nurses per 1000 =
AVERAGE(
    fact_workforce[nurses_per_1000]
)

Average Vacancy Rate =
DIVIDE(
    AVERAGE(fact_workforce[vacancy_rate_pct]),
    100
)

Average Burnout Index =
AVERAGE(
    fact_workforce[burnout_index]
)

Average International Recruitment =
DIVIDE(
    AVERAGE(fact_workforce[international_recruit_pct]),
    100
)

Total Workforce Records =
COUNT(
    fact_workforce[workforce_id]
)
```

</details>

---

## 🎛️ Interactive Power BI Features

### Field Parameters
Implemented Field Parameters to switch between different workforce indicators within the same chart, including:
- Average International Recruitment
- Average Vacancy Rate

### Bookmarks
Used Power BI Bookmarks to support interactive report views and navigation.

### Slicers
Added interactive slicers to explore the dashboard across different dimensions.

**Page 1:**
- Year
- Area Type

**Page 2:**
- Country Name
- WHO Region
- Area Type
- Survey Year

### KPI Cards
Created KPI cards to highlight important healthcare performance and workforce indicators.

### Data Visualisations
Experimented with different visual types:
- Line charts
- Bar charts
- Doughnut charts
- Scatter charts
- Tables
- KPI cards

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|---|---|
| Microsoft Power BI | Dashboard development, data modelling and visualisations |
| DAX | Measures, calculations and KPI development |
| Microsoft Excel | Dataset handling and review |
| Figma | Dashboard design inspiration and layout exploration |
| Power BI Field Parameters | Dynamic measure selection |
| Power BI Bookmarks | Interactive report views |

---

## 📚 Key Learning Outcomes

This was my first-ever analytics challenge, undertaken after approximately one month of Power BI course experience and having created only three dashboards.

Through this challenge, I gained practical experience in:

- Creating KPI cards and meaningful metrics.
- Writing and understanding DAX measures.
- Working with Field Parameters and Bookmarks.
- Building interactive reports using slicers.
- Exploring different chart types and visualisations.
- Improving dashboard layouts and visual hierarchy.
- Exploring Figma design tools.
- Understanding relationships between fact and dimension tables.
- Presenting insights through data storytelling.

---

## 🙌 Acknowledgements

A special thank you to **Crystal Andrea Dsouza** for her guidance, support and help with troubleshooting throughout this journey.

Thank you to **Onyx Data and the DataDNA Challenge community** for providing this opportunity to learn, experiment and grow.

This first challenge has been a valuable learning experience, and I look forward to participating in more analytics challenges.

---

## ⚠️ Dataset Disclaimer

The dataset is synthetic. Country names and selected reference attributes are based on public sources, while healthcare performance, workforce and spending figures are simulated. Health system regions are fictional.

**Synthetic data, DataDNA November 2026 challenge.**

---

### Project Information

| Detail | Information |
|---|---|
| Project | Global Health Insights |
| Challenge | Onyx DataDNA November 2026 |
| Domain | Healthcare Analytics |
| Primary Tool | Microsoft Power BI |
| Report Pages | 2 |
| Dataset Period | 2018–2024 |
| Developer | Candy Angeleye Dsouza |

