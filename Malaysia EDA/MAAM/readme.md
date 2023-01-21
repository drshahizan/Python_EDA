# **Group Members:**
1. MIKHEL ADAM BIN MUHAMMAD EZRIN (A20EC0237)
2. AHMAD MUHAIMIN BIN AHMAD HAMBALI (A20EC0006)

## **Malaysia Hospital Patient Movement Analysis**

This dataset shows the flow of patients to/out of hospitals, with capacity and utilisation since early 2020 until 20th December 2022 (for this analysis). The dataset was taken from Malaysia's Ministry of Health (MoH) Github repository which anyone is free to use to perform data analysis. In this analysis, we will utilize Python and various libraries including mathplotlib, pandas, seaborn, and numpy to conduct our analysis


### Dataset Description
[`hospital.csv`](hospital.csv): Flow of patients to/out of hospitals, with capacity and utilisation.

1) `date`: yyyy-mm-dd format; data correct as of 2359hrs on that date
2) `state`: name of state, with similar qualification on exhaustiveness of date-state combos as PKRC data
3) `beds`: total hospital beds (with related medical infrastructure)
3) `beds_covid`: total beds dedicated for COVID-19
4) `beds_noncrit`: total hospital beds for non-critical care
5) `admitted_x`: number of individuals in category `x` admitted to hospitals, where `x` can be suspected/probable, COVID-19 positive, or non-COVID
6) `discharged_x`: number of individuals in category `x` discharged from hospitals
7) `hosp_x`: total number of individuals in category `x` in hospitals; this is a stock variable altered by flows from admissions and discharges

 
