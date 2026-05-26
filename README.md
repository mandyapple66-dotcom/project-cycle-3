# 2026-Spring-Stat2-Cycle-3

## 👥 Group Information
* **Group Number:** Group 16
* **Member Names:** 113370212 顏名萱, 113370234 王奕晴

---

## ❓ Selected Research Question (Evolutionary Framework)

### 📌 Core Question (Original Question 2)
> **Is the proportion of current alcohol use different between male and female students?**
* **Context:** We initially aimed to evaluate whether adolescent drinking habits vary fundamentally by biological sex, or if the observed sample differences are simply due to random sampling variations.

### 🚀 Cycle 3 Expansion (Advanced Multi-Variable Inquiry)
While addressing the macro-level sex difference, we discovered that looking at sex in isolation obscures underlying developmental patterns. To break this analytical bottleneck, we **大膽引入了第二個核心變數：年齡（Age_Numeric）**。 This allows us to investigate a more profound, stratified question:
> **Does the relationship between biological sex and current alcohol use undergo a developmental trajectory across different chronological adolescent ages (12–18)?**

---

## 📊 Variables & Data Dictionary
To ensure full data integrity and reproducibility, raw categorical response codes from the CDC YRBS 2007 dataset were rigorously parsed (handling missing values via listwise deletion and removing invisible BOM characters using `utf-8-sig` encoding) into a clean analytical dataset ($N = 12,615$).

| Variable Type | Variable Name (Original) | Recoded Variable | Data Type | Description / Value Mapping |
| :--- | :--- | :--- | :--- | :--- |
| **Independent (Core)** | `WhatIsYourSex` | `Sex_Binary` | Binary Categorical | **0**: Male (n = 6,213)<br>**1**: Female (n = 6,402) |
| **Independent (Added)** | `HowOldAreYou` | `Age_Numeric` | Discrete Numeric | Mapped raw categorical codes 1–7 sequentially to chronological integers **12 to 18** years old. |
| **Dependent (Response)** | `CurrentAlcoholUse` | `Alcohol_Binary` | Binary Categorical | **0**: No current use (Originally code 1)<br>**1**: Active user within past 30 days (Originally codes 2 to 7) |

---

## 🛠️ Method Used: Dual Chi-Square ($\chi^2$) Tests of Independence
Rather than performing disconnected two-proportion z-tests, we utilize a unified **Chi-Square ($\chi^2$) Test of Independence** framework. This advanced approach accommodates multi-level discrete variables (Age) and ensures methodological alignment across both dimensions.

### Statistical Assumption Verifications:
* **Independence:** The CDC's multi-stage cluster sampling design guarantees distinct individual records.
* **10% Condition:** The total analytical sample ($N = 12,615$) constitutes less than 10% of the entire US high school student population.
* **Large Sample Expectation:** Due to our robust sample size, all expected frequencies in the cross-tabulation matrix cells vastly exceed the standard minimum rule-of-thumb threshold ($E_{ij} \ge 5$).

---

## 📈 Key Statistical Findings & Interpretations

### 1. Overall Sex Association (Answering Original Question 2)
* **Sample Observation:** Overall Male Alcohol Use Rate = **45.74%** | Female Alcohol Use Rate = **44.53%**.
* **Statistical Inference:** $\chi^2 = 1.8152$, $\text{df} = 1$, **$p\text{-value} = 0.1779$**.
* **Verdict:** Since $p > 0.05$, we **fail to reject the null hypothesis**. There is **no statistically significant difference** in the overall proportions of alcohol use between male and female adolescents. The minor 1.21% gap is entirely due to random sampling error.
* **Visual Proof:** This is illustrated in `stacked_alcohol_gender.png` (virtually identical structure) and proven via `confidence_interval_diff.png` (sensitivity analysis showing the test statistic fails to clear even the lowest 80% CI threshold).

### 2. Overall Age Association (The New Dimension)
* **Sample Observation:** Alcohol use spikes dramatically with maturity, starting at ~33% at age 14 and exploding to **53.17%** by age 18.
* **Statistical Inference:** $\chi^2 = 202.4067$, $\text{df} = 6$, **$p\text{-value} < 0.0001$**.
* **Verdict:** Strongly reject the null hypothesis. There is an **exceptionally significant statistical association** between chronological age and alcohol use.

### 💡 The Golden Insight: The Gender-Age Cross-over Effect
By exporting a fine-grained, 23-row nested structure (`inference_summary_table.csv`), we uncovered a hidden psychological transition phase that the macro-level Question 2 obscured, while accounting for sample size limitations:

* **⚠️ Critical Methodological Caveat (Ages 12-13):** Although the chart displays a very high drinking percentage for ages 12 ($83.33\%$) and 13 ($50.00\%$), our data infrastructure reveals that **their sample sizes are extremely small** ($n=12$ and $n=6$, respectively). These are extreme outliers caused by small-sample random fluctuation and hold no real statistical representation.
* **Early Adolescence (Ages 14-15 - High Sample Reliability):** With robust and reliable sample sizes (Age 14 $N=1,253$; Age 15 $N=2,889$), female students exhibit a notably *higher* propensity for current alcohol use than males (e.g., Age 14 Female: **38.15%** vs. Male: **27.23%**). This suggests an earlier behavioral or social initiation phase among young females.
* **Late Adolescence (Ages 17-18):** As sample sizes remain highly robust, male students experience a sharper behavioral acceleration and ultimately *overtake* females near legal adulthood (e.g., Age 18 Male: **55.53%** vs. Female: **50.54%**). This complex interaction is beautifully mapped in `alcohol_by_gender_and_age.png`.

---

## 💾 Core Project Deliverables (Artifacts Interaction)
All artifacts generated in this project act as unified, complementary pairs to maximize academic clarity:
1. **`stacked_alcohol_gender.png` & `confidence_interval_diff.png`:** The binary behavioral composition chart alongside the critical-value sensitivity plot, sealing the mathematical verdict on the **Original Question 2** (Sex overall).
2. **`alcohol_by_gender_and_age.png`:** The primary grouped bar chart optimized for cognitive impact, displaying the upward age trajectory and the visual crossover of genders.
3. **`inference_summary_table.csv`:** The 23-row full statistical infrastructure containing precise counts, proportions, and exact $\chi^2$ parameters for total, male, and female groupings across every age cohort.
