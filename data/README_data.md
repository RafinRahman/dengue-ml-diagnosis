# Data Directory

## Source Dataset

**Citation:** Mojumdar MU, Sarker D, Assaduzzaman M, Sajeeb MAH, Rahman MM, Bari MS, et al. Structured clinical and haematological dataset for early dengue diagnosis in Bangladesh. Mendeley Data; 2024. V1.
**DOI:** 10.17632/673swz9tb4.1
**URL:** https://data.mendeley.com/datasets/673swz9tb4/1
**License:** CC BY 4.0

## Download Instructions

1. Go to https://data.mendeley.com/datasets/673swz9tb4/1
2. Click **Download All** (no login required)
3. Extract the ZIP and place `Dengue_clinical_dataset.csv` in this `data/` directory

## Data Dictionary

| Column | Type | Description |
|---|---|---|
| Id | Integer | Anonymised patient identifier (excluded from modelling) |
| Gender | String | Patient sex (Male / Female) |
| Age | Integer | Age in years (range 1 to 87) |
| Platelet Count | Integer | Platelet count in cells/µL |
| WBC | Integer | Total white blood cell count in cells/µL |
| Location | String | Sub-district within Munshiganj (excluded from modelling) |
| Fever | Boolean | Fever present at presentation |
| Duration_of_Fever | Integer | Duration of fever in days (0 = afebrile) |
| Headache | Boolean | Headache present |
| Muscle_Pain | Boolean | Muscle pain present |
| Rash | Boolean | Rash present |
| Vomiting | Boolean | Vomiting present |
| Outcome | String | Dengue diagnosis: Positive (n=697) or Negative (n=321) |

## Collection Context

Data were collected at Life Aid General Hospital and Diagnostic Limited, Munshiganj, Dhaka, Bangladesh, during confirmed dengue outbreak periods. Diagnosis was determined by NS1 antigen testing and/or clinical assessment per WHO 2009 criteria. All personally identifiable information was removed before deposition.

## Feature Engineering Applied in Pipeline

- `Gender` → `Gender_num` (Male=1, Female=0)
- `Fever`, `Headache`, `Muscle_Pain`, `Rash`, `Vomiting` → integer (1/0)
- `Location` and `Id` excluded
- Full feature set: Age, Gender_num, Platelet Count, WBC, Fever_num, Duration_of_Fever, Headache_num, Muscle_Pain_num, Rash_num, Vomiting_num
- CBC-only feature set: Age, Gender_num, Platelet Count, WBC
