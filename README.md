# CN-to-AD Conversion Prediction: OASIS-3 Structural MRI Analysis

Predicting conversion from cognitively normal (CN) to Alzheimer's disease (AD) 
using baseline structural MRI, demographics, and genetic risk data from the 
OASIS-3 dataset — plus supporting cross-sectional and longitudinal analyses 
of structural biomarkers across the CN → MCI → AD spectrum.

## Dataset
OASIS-3 (Open Access Series of Imaging Studies): FreeSurfer-derived structural 
MRI output (2,681 scans, 203 features), demographics (1,378 subjects), and 
longitudinal CDR clinical assessments (8,626 visit records).

## Notebooks

**01_data_exploration** — Merges FreeSurfer, demographics, and CDR data into 
diagnostic groups (CN/MCI/AD, n=960 subjects); derives ICV-corrected hippocampal 
volume and cortical thickness features.

**02_statistical_validation** — Kruskal-Wallis and Bonferroni-corrected 
Mann-Whitney U tests confirm significant differences across CN/MCI/AD groups in 
hippocampal volume, entorhinal thickness, and precuneus thickness (all p < 1e-25); 
large effect sizes throughout (Cohen's d > 1.0, CN vs AD).

**03_classification** — Cross-sectional CN vs AD classification comparing 
Logistic Regression, Random Forest, and XGBoost (n=756, 5-fold CV).

**04_longitudinal_analysis** — Tracks hippocampal atrophy across repeat scans 
(up to 10 scans/subject). CN-to-AD converters show hippocampal atrophy at ~4.5x 
the rate of stable CN subjects (p=4.05e-07, n=334 with ≥1 year follow-up).

**05_conversion_prediction** — Core predictive model: forecasts future CN-to-AD 
conversion using only *baseline* (pre-conversion) structural MRI, demographic, 
and APOE4 features (n=542, 44 converters). Logistic regression achieves 
**AUC = 0.834** (5-fold cross-validated) with proper class-imbalance handling. 
Risk-quartile stratification shows strong enrichment: highest-risk quartile 
converts at 22.2% vs 0% in the lowest quartile (2.7x over the 8.3% population 
base rate).

**06_preclinical_signatures** — Compares baseline structural features between 
eventual converters and stable CN subjects. Converters show significantly lower 
baseline hippocampal volume, entorhinal thickness, precuneus thickness, and 
amygdala volume — years before clinical diagnosis (all p < 1e-3) — supporting a 
detectable preclinical structural signature.

## Key Result
Baseline structural MRI + demographics + APOE4 genotype predict future CN-to-AD 
conversion with AUC = 0.834 (5-fold CV, logistic regression), with the 
highest-risk quartile converting at 2.7x the population base rate.

## Limitations
Small converter cohort (n=44) limits statistical power. Single-cohort, 
observational data — no external validation or causal claims.

## Tools
Python, pandas, scikit-learn, XGBoost, SHAP, SciPy, Matplotlib
