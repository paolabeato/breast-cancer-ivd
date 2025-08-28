# 🩺 Breast Cancer Prognostic Index Evaluation

This project applies **survival modeling techniques** to evaluate a composite *In-Vitro Diagnostic* (IVD) index for breast cancer prognosis. Using a **simulated cohort of 494 patients**, it replicates the workflow of an IVD validation study — from **data generation** and **Cox modeling** to **discrimination, calibration, and laboratory reproducibility** analyses. The pipeline is fully reproducible in **R + Quarto** and outputs a manuscript-ready HTML report.

---

## 📁 Project Overview

- **Data**: Fully simulated dataset (`analysis_ivd`) of 494 patients with clinical covariates, biomarker measures, and assay metadata  
- **Outcome**: 5-year disease-free survival (DFS)  
- **Tools**: R, Quarto, `survival`, `riskRegression`, `timeROC`, `broom`, `gt`, `ggplot2`, `lme4`, `binom`  
- **Deliverable**: Manuscript-style Quarto HTML report  
- **Manuscript**: [📄 View the full manuscript here](index.html)  

---

## 🔍 Methods

### 1. Data Simulation & Preparation
- Cohort of 494 patients with age, chemotherapy, BMI, and diagnosis year  
- Biomarker triplet (A, B, C) with realistic correlation structure  
- Pre-analytical/analytical variability: site, lot, operator, hemolysis, freeze–thaw  
- Weibull survival times tuned to achieve **40% 5-year event prevalence**

### 2. Prognostic Modeling
- **Primary model**: Cox proportional hazards with biomarkers + clinical covariates  
- **Index-only model**: CoxRisk score (locked-down index emulating an IVD)

### 3. Performance Evaluation
- **Discrimination**: Harrell’s C-index, time-dependent AUC, ROC curves  
- **Calibration**: intercept, slope, calibration plots  
- **Accuracy**: 5-year Brier score  
- **Diagnostic performance**: sensitivity, specificity, PPV, NPV, likelihood ratios (median cutoff)  
- **Reproducibility**: precision CVs (within-run, between-day), Bland–Altman plots, QC plots by site/lot/operator  

---

## ✅ Results Summary

| Model                  | C-index | 5-yr AUC | Calibration slope | Brier (5y) |
|------------------------|---------|----------|-------------------|------------|
| Primary prognostic     | 0.661   | —        | 0.94              | 0.228      |
| Index-only (CoxRisk)   | 0.643   | 0.592    | —                 | —          |

- 🎯 Event prevalence tuned to **40%** at 5 years  
- 📊 Risk distribution tightly centered near median → limited discrimination  
- 📈 Calibration: intercept ≈ **0.08**, slope ≈ **0.94**  
- 🎲 Brier score: **0.228** at 5 years  
- ⚙️ Precision: within-run CVs as low as **3.2%** and total CVs up to **11.4%**  
- 🔬 QC plots showed reproducibility across site, lot, and operator  

---

## 💡 Key Takeaways

- The **CoxRisk index** demonstrated **modest discrimination**, with performance constrained by tightly clustered risk predictions  
- **Calibration** was acceptable but imperfect, highlighting the importance of evaluating both slope and intercept  
- **Brier score** provided complementary insight into probability accuracy  
- **Laboratory precision analyses** (CVs, Bland–Altman, QC plots) showed consistent assay reproducibility under simulated conditions  
- Together, these analyses illustrate how **statistical modeling** and **laboratory evaluation** can be integrated into a unified framework for IVD validation  

---

## ⚠️ Limitations

- Data are **fully simulated** and do not capture all real-world heterogeneity  
- Missingness modeled as **MAR**; in practice, **MNAR** mechanisms may occur  
- Limited spread of risk estimates restricted model discrimination  
- Only biomarkers A, B, C included; adding molecular or genomic features could improve prognostic utility  

---

## 📄 Deliverables

- `breastcancer.html` → published as [**index.html**](index.html) for GitHub Pages  
- `breastcancer_files/` — Generated figures and tables  
---

## 🔑 Code Availability

The full R/Quarto source code for this analysis is **available upon request**.  
This repository highlights the **reproducible results** and manuscript-ready output.

---

## 👩‍💻 Author Notes

This project was created as a **portfolio piece** to demonstrate:  
- Applied skills in **biostatistics, survival analysis, and diagnostic evaluation**  
- Proficiency with **R, Quarto, and reproducible pipelines**  
- Integration of **statistical modeling** with **laboratory assay validation**  
- Emphasis on **interpretability, visual storytelling, and methodological rigor**  

---

