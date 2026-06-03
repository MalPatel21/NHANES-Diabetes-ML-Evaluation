# NHANES-Diabetes-ML-Evaluation

# Abstract 
This project develops and evaluates a machine learning pipeline to predict diabetes status (defined as $HbA1c \ge 6.5\%$) using data from the National Health and Nutrition Examination Survey (NHANES). Utilizing a regularized Logistic Regression framework, the analysis focuses on the clinical trade-offs between sensitivity and precision in a public health screening context. The model prioritizes a 90% target recall to minimize missed diagnoses, critically assessing the implications of the resulting false-positive rate and the model's generalizability across population cohorts.
 
# Data Directory Configuration
To maintain reproducibility, ensure your local directory is structured as follows before running the scripts:

2017-2020_Data/ — Contains XPT files for the Pre-Pandemic cycle.

2021-2023_Data/ — Contains XPT files for the current cycle.

Note on File Paths:
In the main analysis script, you will find the following path definitions:


## --- UPDATE THESE PATHS ---
data_path_pre = 'C:/Users/Malik/Documents/NHANES/2017-2020_Data' 

data_path_post = 'C:/Users/Malik/Documents/NHANES/2021-2023_Data'
## ---------------------------
Action Required: Please update the strings above to match the local directory where you have saved the NHANES datasets. Using absolute paths is recommended to ensure the pandas read functions locate the .XPT files correctly.

# Dataset
The data utilized in this study is sourced from the National Health and Nutrition Examination Survey (NHANES).

Source: CDC NHANES Website

Cycles used: [2017-2020 and 2021-2023 ].
Files used:
(Cycle 2017-2020)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_DEMO.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_DEMO.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_BMX.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_BMX.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_BPXO.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_BPXO.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_GHB.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_GHB.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_BIOPRO.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_BIOPRO.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_TRIGLY.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_TRIGLY.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_CBC.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_CBC.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_HSCRP.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2017/DataFiles/P_HSCRP.xpt)

(Cycle 2021-2023)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/DEMO_L.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/DEMO_L.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/BMX_L.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/BMX_L.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/BPXO_L.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/BPXO_L.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/GHB_L.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/GHB_L.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/BIOPRO_L.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/BIOPRO_L.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/TRIGLY_L.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/TRIGLY_L.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/CBC_L.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/CBC_L.xpt)
[https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/HSCRP_L.xpt](https://wwwn.cdc.gov/Nchs/Data/Nhanes/Public/2021/DataFiles/HSCRP_L.xpt)


Technical Specifications:
sklearn: 1.3.0
pandas: 3.0.2
numpy: 1.26.4
matplotlib: 3.7.1
seaborn: 0.12.2
statsmodels: 0.14.0
