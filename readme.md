<img width="1470" alt="/index" src="https://github.com/user-attachments/assets/c66389f1-a037-4d01-9854-c6eaed14c645" />

<div align="center">
  <h1>STAY</h1>
</div>

## 👋🏻 Getting Started
**Visit https://stay-frontend-topaz.vercel.app/**

## ⚙️ Technologies Used
- **Next.js** – React framework for SSR and SSG
  
- **TypeScript with JSX** – Typed JavaScript for better development

- **Tailwind CSS** – Utility-first CSS framework
  
- **PostCSS** – For processing styles


## ✂️ Customized learning plan
<img width="1470" alt="/create-plan" src="https://github.com/user-attachments/assets/c50f80e6-e6c6-4533-9147-dcfe359d3c65" />

- **Tailored** to your ADHD severity, education level, age group, and preferred subjects  

- **Boost** your focus and productivity with ADHD-specific strategies  

- **Simple** and intuitive: fill in your details, then click “Generate Your Personalized Study Plan”  

- **Achieve** your learning goals with a clear, structured roadmap  

## XGBoost ADHD Prediction Model Using SMOTE
### Overview
This repository contains an XGBoost classification model trained on the HYPERAKTIV dataset 1 to predict Attention-Deficit/Hyperactivity Disorder (ADHD) in humans. The model uses sensor data (actigraphy/heart rate) and clinical assessments to achieve 71% accuracy 1.
### Dataset
The model is trained on the HYPERAKTIV dataset 1 containing:
- **103 participants**: 51 ADHD patients + 52 clinical controls
### Features
- **Demographics**: Age group, sex
- **Sensor data**: Motor activity (ACC), heart rate variability (HRV)
- **Clinical scores**: ASRS, WURS, CPT-II, MADRS
- **Diagnostic flags**: Comorbidities (BIPOLAR, ANXIETY)
- **Target**: ADHD (1=diagnosed, 0=control)
### Model Architecture
XGBoost Configuration
```python
XGBClassifier(
    objective='binary:logistic',
    max_depth=3,
    learning_rate=0.1,
    n_estimators=100,
    random_state=6
)
```
### Preprocessing Pipeline
- **Data Cleaning**:
  Deduplicate by ID
  Cast IDs to UTF-8 strings
  Handle missing values with fill_null(-1)
- **Feature Engineering**:
  Exclude non-predictive columns (ACC_TIME, HRV_TIME)
  Align train/test IDs using semi-joins 3
- **Input Requirements**:
  811 features (post-feature engineering)
  All features must be numeric (Polars→Pandas conversion required)
Results
Accuracy
71%
Precision
61%
Recall
67%
F1-Score
63%

Example Output :
[[0.10907203 0.890928]]  # [P(non-ADHD), P(ADHD)]
