# NHANES-Diabetes-ML-Evaluation

# Abstract 
Type 2 Diabetes Mellitus (T2DM) is a major global public health challenge associated with substantial morbidity and mortality. Early identification of high-risk individuals is essential for timely intervention, yet traditional risk prediction approaches may inadequately capture the complex relationships among demographic, anthropometric, and clinical factors. This study evaluated whether routinely collected demographic, lifestyle, and biomarker variables could predict diabetes status using machine learning, while assessing performance differences between pre-COVID and COVID-era populations.

Data were obtained from the National Health and Nutrition Examination Survey (NHANES) 2017–2023. Diabetes status was defined using HbA1c according to established diagnostic criteria (HbA1c ≥6.5%). Following data integration, cleaning, feature engineering, and multicollinearity screening, two classification models were developed: regularised Logistic Regression (LR) and Support Vector Classifier (SVC). Hyperparameters were optimised using five-fold stratified cross-validation, and decision thresholds were tuned to prioritise recall for screening purposes. Performance was evaluated across pooled and temporally stratified cohorts using repeated train-validation-test splits over five random seeds.

Both models demonstrated strong discriminative performance, achieving ROC-AUC values ranging from 0.839 to 0.857. Differences between LR and SVC were negligible, with mean ROC-AUC gaps not exceeding 0.002 across cohort analyses. Threshold optimisation successfully prioritised sensitivity, producing recall values between 0.813 and 0.836, albeit with reduced precision (0.260–0.285). Performance declined modestly in the COVID-era cohort, where F1 scores decreased from approximately 0.42 to 0.40 for both models. Performance metrics reported throughout the study represent averages across cross-validation folds and five independent random-seed repetitions for each model and cohort.

Overall, Logistic Regression and SVC provided comparable predictive performance for diabetes classification within NHANES data. Given equivalent discrimination and greater interpretability, Logistic Regression represents the more practical option for population-level diabetes screening. Future work should incorporate survey weighting, subgroup fairness analyses, and external validation to strengthen generalisability and support clinical translation.

# Instructions
The information below contains everything necessary to run the code properly. Please read through all sections before running the code.

# Code & Analysis Tool
The project was created using Jupyter Notebook, and this Readme assumes the same tool is being used to run the script. The code is stored in a .jpynb file.

# Data Directory Configuration
To maintain reproducibility, ensure your local directory is structured as follows before running the scripts:

2017-2020_Data/ — Contains XPT files for the Pre-Pandemic cycle.

2021-2023_Data/ — Contains XPT files for the current cycle.

Note on File Paths:
In the main analysis script, you will find the following path definitions:


## --- UPDATE THESE PATHS ---
Action Required: Please update the strings above to match the local directory where you have saved the NHANES datasets. Using absolute paths is recommended to ensure the pandas read functions locate the .XPT files correctly.

data_path_pre = 'C:/Users/Malik/Documents/NHANES/2017-2020_Data' 

data_path_post = 'C:/Users/Malik/Documents/NHANES/2021-2023_Data'

# Dataset
The data used in this study are sourced from the National Health and Nutrition Examination Survey (NHANES). It was not included in this repo because the data are publicly available and can be downloaded directly from the CDC NHANES website, and because individual datasets are subject to intermittent updates as additional files are processed and released.

Dataset download instructions:
1. Create the folders aforementioned in the data directory
2. Download the data listed below from the 2017-2020 cycle and move them to the respective folder created
3. Repeat above for 2021-2023 in its respective folder
4. Update the paths mentioned in the code

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


#Technical Specifications:
Before running the code, make sure these libraries are the correct  versions being used:

sklearn: 1.3.0
pandas: 3.0.2
numpy: 1.26.4
matplotlib: 3.7.1
seaborn: 0.12.2
statsmodels: 0.14.0

# Running the Notebook
Once the above has been completed, you can restart and run the entire notebook.
