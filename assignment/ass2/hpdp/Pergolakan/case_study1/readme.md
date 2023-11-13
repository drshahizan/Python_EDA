# Malaysian COVID-19 datasets (Cases, deaths and Vaccinations) <a href="Pergolakan_Assignment_2_Case_Study_1.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

**COVID-19** is a novel coronavirus that emerged in late 2019 and has since caused a global pandemic that has affected millions of people and disrupted many aspects of life. As of November 6, 2023, there have been over 32 million confirmed cases and over 1.2 million deaths worldwide due to COVID-19.

However, the situation varies widely across different countries and regions, depending on their vaccination rates, testing capacities, health systems, and public health measures.

In this report, we will examine the trend of the vaccines administered and the number of cases and deaths over time in Malaysia, one of the countries that has been severely hit by the pandemic.


|    Name           |           Matric Number       |                      
|-------------------|-------------------------------|
|Muhammad Fikri Bin Sharunazim    | A21EC0075       |
|Muhammad Farhan Bin Ibrahim|        A21EC0072      |
|Muhammad Adam Fahmi Bin Mohd Taufiq |A21EC0061|
|Mikhail Bin Yassin |A21EC0053                      |

---
# Overview
## Malaysian COVID-19 Dataset

The **Malaysian COVID-19 dataset** provides comprehensive information related to the COVID-19 pandemic in Malaysia. It covers various aspects, including daily recorded cases, clusters, testing data, healthcare facility utilization, deaths, and vaccination statistics. Specifically, the dataset includes the following key components:

1. **Cases**: Daily recorded COVID-19 cases at both the country and state levels.
2. **Clusters**: Exhaustive list of announced clusters with relevant epidemiological data points.
3. **Tests**: Daily tests (note: not necessarily unique individuals) categorized by type at both country and state levels.
4. **Healthcare**: Information on patient flow to and from COVID-19 Quarantine and Treatment Centers (PKRC), hospitals, and ICU bed capacity and utilization.
5. **Deaths**: Daily deaths due to COVID-19 at both country and state levels.
6. **Vaccinations**: Daily and cumulative vaccination data, including dose type, brand, and coverage at country, state, district, and demographic levels.

## Data Source

The dataset is sourced from the **Ministry of Health Malaysia (MoH-Malaysia)**. It is maintained and updated by various entities, including CPRC, CPRC Hospital System, MKAK, and MySejahtera.


## Purpose and Goals

The primary objective of analyzing this dataset is to gain insights into the COVID-19 situation in Malaysia.

## Tools and Techniques

To explore the dataset, you can use the following tools and techniques:

- **Python Libraries**: Pandas, NumPy, and Matplotlib/Seaborn for data manipulation, exploration, and visualization.
- **Jupyter Notebooks & Google Colab**: To document analyses, visualize data, and share insights.
- **Github**: For documentation purposes.

---


## The Dataset

All of the sets are available in the Official Minister of Health Malaysia (MoH-Malaysia) Github page.

## Data Dictionary
### Cases

- `date`: yyyy-mm-dd format; data correct as of 1200hrs on that date

- `state`: name of state (present in state file, but not country file)

- `cases_new`: cases reported in the 24h since the last report

- `cases_import`: imported cases reported in the 24h since the last report

- `cases_active`: Covid+ individuals who have not recovered or died

-  `cases_recovered` recovered cases reported in the 24h since the last report

- `cases_cluster`: number of cases attributable to clusters; the difference
between `cases_new` and the sum of cases attributable to clusters is the number of sporadic cases

### Death
- `date`: yyyy-mm-dd format; data correct as of 1200hrs on that date

- `state`: name of state (present in state file, but not country file)

- `deaths_new`: deaths due to COVID-19 based on **date reported to public**

- `deaths_bid`: deaths due to COVID-19 which were brought-in dead based on **date reported to public** (perfect subset of `deaths_new`)

- `deaths_new_dod`: deaths due to COVID-19 based on **date of death**

- `deaths_bid_dod`: deaths due to COVID-19 which were brought-in dead based on **date of death** (perfect subset of `deaths_new_dod`)

- `deaths_pvax`: number of partially-vaccinated individuals who died due to COVID-19 based on **date of death** (perfect subset of `deaths_new_dod`), where "partially vaccinated" is defined as receiving at least 1 dose of a 2-dose vaccine at least 1 day prior to testing positive, or receiving the Cansino vaccine between 1-27 days before testing positive.

- `deaths_fvax`: number of fully-vaccinated who died due to COVID-19 based on **date of death** (perfect subset of `deaths_new_dod`), where "fully vaccinated" is defined as receiving the 2nd dose of a 2-dose vaccine at least 14 days prior to testing positive, or receiving the Cansino vaccine at least 28 days before testing positive.

- `deaths_tat`: median days between date of death and date of report for all deaths reported on the day

## Vaccination
- `date`: yyyy-mm-dd format; data correct as of 2359hrs on that date

- `daily_partial` : number of individuals who received the first dose of a two-dose protocol

- `daily_partial_adol`: subset (already included) of daily_partial, but for individuals aged 12-17 only

- `aily_partial_child`: subset (already included) of daily_partial, but for individuals aged 5-11 only

- `daily_full`: number of individuals who completed their original protocol (whether the 2nd dose of a two-dose protocol, or a single-dose protocol)

- `daily_full_adol`: subset (already included) of daily_full, but for individuals aged 12-17 only

- `daily_full_child`: subset (already included) of daily_full, but for individuals aged 5-11 only

- `daily_booster`: number of individuals who received one dose beyond the original protocol

- `daily`: total doses administered

- `cumul_x`: cumulative doses falling into category x, where x is one of the daily categories
- `brandX`: denotes the number of 1st, 2nd, or 3rd doses administered for that

- `brand`; note that cansino2 is omitted as it is a single-dose protocol

- `pendingX`: number of records with an indeterminate brand, usually due to errors synchronising with the Vaccine Management System (VMS) blockchain

  
### Links to Datasets
Cases by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/cases_state.csv  
Death by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/epidemic/deaths_state.csv  
Vaccination by State: https://raw.githubusercontent.com/MoH-Malaysia/covid19-public/main/vaccination/vax_state.csv

### Link to Google Collab
<a href="Pergolakan_Assignment_2_Case_Study_1.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>


