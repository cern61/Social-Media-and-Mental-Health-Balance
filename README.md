# 📱🧠 Social Media & Mental Health Balance

### A data science study of how digital habits relate to stress, sleep quality, and happiness

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-data%20analysis-150458?logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-visualization-3F4F75?logo=plotly&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-notebook-F37626?logo=jupyter&logoColor=white)

> *Final project for **Introduction to Data Science** — supervised by Muhammet Sinan Başarslan.*

---

## 📖 Overview

Social media is part of everyday life, but what does heavy use actually do to our well-being? This project explores that question end to end: from raw survey-style data to exploratory analysis, a literature-informed risk score, and an interactive machine-learning tool that estimates an individual's mental-health risk level.

The analysis covers **500 users** and combines demographic information, social media usage, and self-reported well-being metrics. The dataset has **no missing values**, so the focus stays on analysis rather than imputation.

## 🎯 Objectives

- Understand how **screen time, sleep, stress, exercise, and happiness** relate to each other
- Compare **gender groups** and **social media platforms** in terms of stress and happiness
- Build a transparent, **literature-grounded risk score** from normalized well-being indicators
- Train a **Random Forest classifier** and wrap it in an interactive per-user analysis tool

## 🗂️ Dataset

Kaggle dataset: *Mental Health and Social Media Balance* (500 records).

| Column | Description |
|---|---|
| `User_ID` | Unique user identifier (U001–U500) |
| `Age` | Age of the user |
| `Gender` | Male / Female / Other |
| `Social_Media_Platform` | Main platform used |
| `Daily_Screen_Time(hrs)` | Average daily screen time |
| `Sleep_Quality(1-10)` | Self-reported sleep quality |
| `Stress_Level(1-10)` | Self-reported stress level |
| `Days_Without_Social_Media` | Days spent offline from social media |
| `Exercise_Frequency(week)` | Weekly exercise sessions |
| `Happiness_Index(1-10)` | Self-reported happiness |

## 🔬 Methodology

**1. Data preparation** – Loading, structure inspection, and missing-value check.

**2. Exploratory analysis** – Density (KDE) plots for all seven numeric variables, plus a correlation heatmap.

**3. Segment analysis** – Platform preferences by gender, gender distribution, stress and happiness by gender (box plots), and average stress and happiness by platform.

**4. Risk scoring** – Using Min-Max normalization, a composite **Depression Risk Score** is computed from four indicators, inspired by research from Twenge et al. (2019) and Primack et al. (2017):

```
Risk = ( Stress + Screen Time + (1 − Sleep Quality) + (1 − Happiness) ) / 4
```

Users are then grouped into **Low** (≤ 0.4), **Medium** (0.4–0.7), and **High** (> 0.7) risk levels.

**5. Machine learning** – A `RandomForestClassifier` (100 trees) predicts the risk level, exposed through an **interactive `ipywidgets` interface**: enter a User ID, view the profile, and get a predicted risk level with a tailored recommendation.

## 💡 Key Findings

- 😴 **Screen time and sleep quality** show the strongest negative relationship, consistent with late-night screen exposure disrupting sleep.
- 😰 **Stress and happiness** are strongly and negatively related.
- 📈 **Higher screen time** is associated with **higher stress** and **lower happiness**.
- 🏃 **Exercise** shows a modest but positive effect, lowering stress and raising happiness.
- 📲 **Platforms differ:** visually driven, notification-heavy platforms tend to be linked with higher stress, while X and LinkedIn-style networks are linked with lower stress and higher happiness.
- ⚖️ Most users fall into the **Medium** risk group, suggesting that digital life is a matter of *balance* rather than a simple good-or-bad.

## 🚀 Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/cern61/Social-Media-and-Mental-Health-Balance.git
cd Social-Media-and-Mental-Health-Balance

# 2. Install dependencies
pip install pandas numpy seaborn matplotlib plotly scikit-learn ipywidgets jupyter

# 3. Place the dataset next to the notebook
#    MentalHealthSocialMediaBalance.csv

# 4. Launch the notebook
jupyter notebook SocialMediaMentalHealthBalance.ipynb
```

> The interactive User ID tool requires a Jupyter environment with `ipywidgets` enabled (it also works in Google Colab).

## 📁 Repository Structure

```
├── SocialMediaMentalHealthBalance.ipynb   # Full analysis & interactive tool
├── MentalHealthSocialMediaBalance.csv     # Dataset (add from Kaggle)
└── README.md
```

## ⚠️ Limitations & Future Work

We believe in being transparent about what this project is and isn't:

- **Not a clinical tool.** The risk score is a heuristic built from self-reported data and is meant for educational exploration, not diagnosis.
- **Correlation ≠ causation.** The findings describe associations; they do not prove that social media causes changes in well-being.
- **Label and model overlap.** The risk level is derived from the same features the Random Forest uses, so the model largely learns the scoring formula. Its predictions should be read as a demonstration of the pipeline, not as independent predictive validation.
- **Small sample.** With 500 records, results may not generalize to wider populations.

**Next steps:** train/test split with cross-validation, validation against an independent clinical-style outcome, feature importance analysis, and a lightweight web dashboard (e.g., Streamlit) for the interactive tool.

## 👥 Team

| Name |
|---|
| Ceren Naz Dervişoğlu |
| Betül Tok |
| Zeynep Aslı Çakmak |
| Gülseli Ocakcı |

## 📚 References

1. Twenge, J. M., et al. (2019). *Trends in U.S. Adolescents' Mental Health and Its Relation to Digital Media Use.* Journal of Abnormal Psychology.
2. Primack, B. A., et al. (2017). *Social Media Use and Perceived Social Isolation Among Young Adults in the U.S.* American Journal of Preventive Medicine.
3. U.S. Department of Health and Human Services (2023). *Social Media and Youth Mental Health: The U.S. Surgeon General's Advisory.*
4. Kaggle: *Mental Health and Social Media Balance* dataset.

---

<p align="center">⭐ If you found this project interesting, feel free to star the repo!</p>