# 2026-Spring-Stat2-Cycle-3

## 👥 Group Information
* **Group Number:** Group 16
* **Member Names:** 113370212 顏名萱, 113370234 王奕晴

## ❓ Selected Research Question
> **Is the proportion of current alcohol use different between male and female
students?**

We aim to evaluate whether adolescent drinking habits vary fundamentally by biological sex, or if the observed sample differences are simply due to random sampling variations.

---

## 📊 Variables & Data Dictionary
The variables selected and extracted from the raw YRBS 2007 dataset are defined as follows:

| Variable Type | Variable Name (Original) | Recoded Variable (Binary) | Description / Value Mapping |
| :--- | :--- | :--- | :--- |
| **Grouping / Independent** | `WhatIsYourSex` | `Sex_Binary` | **0**: Male (Originally code 2)<br>**1**: Female (Originally code 1) |
| **Response / Dependent** | `CurrentAlcoholUse` | `Alcohol_Binary` | **0**: No current use (Originally code 1)<br>**1**: Active user (Originally codes 2 to 7) |

---

## 🛠️ Method Used
### Two-proportion $z$-test
To determine if the observed difference in alcohol use between female and male students is statistically significant, we utilize a **Two-Independent-Sample $Z$-Test for Proportions**. This method allows us to test the null hypothesis ($H_0: p_{\text{female}} - p_{\text{male}} = 0$) and construct a **95% Confidence Interval (CI)** to estimate the true magnitude of the difference between the two population parameters.

The analytical process involves:
* **Data Preparation:** Filtering missing responses (Listwise deletion) to establish a clean, effective sample of **12,659 adolescents**, and recoding variables into binary formats ($0$ or $1$).
* **Statistical Estimation:** Computing sample proportions ($\hat{p}$), standard error under the pooled proportion assumption, and evaluating the resulting $z$-statistic against the standard significance level ($\alpha = 0.05$).

---

## 📝 Short Final Conclusion
Based on our statistical analysis of 12,659 participants ($n_{\text{female}} = 6,425, n_{\text{male}} = 6,234$):

* **Sample Observation:** The sample proportion of current alcohol use was slightly lower in females ($\hat{p} = 44.6\%$) compared to males ($\hat{p} = 45.8\%$), yielding a point estimate difference of $-1.19\%$.
* **Statistical Inference:** The two-sample $z$-test resulted in a $z$-statistic of $-1.3442$ and a **$p$-value of $0.1789$**, which is much higher than the standard significance level ($\alpha = 0.05$). Additionally, the 95% confidence interval for the difference $[-2.92, 0.54]$ successfully contains 0.
* **Final Takeaway:** We **fail to reject the null hypothesis**. There is **no statistically significant difference** in the proportions of current alcohol use between male and female adolescents in the 2007 YRBS population. The minor variation observed in our sample is attributed to random sampling error.
