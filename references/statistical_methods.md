# Reference Part 2: Methodology and Statistical Assumptions

This document justifies the selection of the statistical methods used in this project and verifies that the necessary mathematical assumptions are satisfied for a valid inference based on the processed dataset ($N = 12,615$).

## 1. Method Choice

### Primary Statistical Method: Chi-Square ($\chi^2$) Test of Independence & Stratified Exploratory Analysis
To analyze the relationships among biological sex, age, and alcohol consumption, we transition from the standard two-proportion z-test to a robust **Chi-Square ($\chi^2$) Test of Independence**. Furthermore, we execute an exploratory stratification by chronological age to track behavioral trends across adolescent developmental stages.

* **Group Variable 1 (Independent):** `Sex_Binary` (Categorical, 2 levels: 0 = Male, 1 = Female).
* **Group Variable 2 (Exploratory Stratifier):** `Age_Numeric` / `Age` (Discrete integer levels spanning ages 12 through 18).
* **Response Variable (Dependent):** `Alcohol_Binary` / `Alcohol_Status` (Categorical, 2 levels: 0 = No Use, 1 = Current User).

### Justification:
1.  **Association Testing:** The Chi-Square test evaluates whether a statistically significant association exists between biological sex and current alcohol use status by comparing our observed contingency counts against expected counts under the null hypothesis ($H_0$: Sex and Alcohol Use are independent).
2.  **Sensitivity and Threshold Evaluation:** By evaluating the actual calculated $\chi^2$ statistic against multiple alpha-driven critical values (ranging from 80% to 99% confidence), we perform a robustness check to see how stable our statistical conclusions remain across different decision frameworks.
3.  **Developmental Stratification:** Tracking alcohol usage rates by individual age cohorts (12–18) allows us to visually inspect whether the gender dynamic shifts as adolescents mature.

---

## 2. Statistical Assumptions Assessment

To ensure the validity of the Chi-Square inference and subsequent visualizations, the following mathematical conditions have been evaluated and verified:

### I. Independence
* **Individual Independence:** Each participant in the YRBS 2007 survey represents a distinct individual student sampled via a national framework. There is no structural reason to suggest the behavior of one student clusters with or influences another in a manner that violates independence at the national level.
* **10% Condition:** Our high-quality analytical sample ($n = 12,615$) is substantially smaller than 10% of the millions of high school students residing in the United States in 2007, guaranteeing that sampling without replacement does not impede the independence assumption.

### II. Randomization
* **Data Source:** The Youth Risk Behavior Surveillance System (YRBSS) utilizes a rigorous multi-stage cluster sampling design to yield a representative sample of US youth, successfully satisfying the random sampling criteria.

### III. Expected Cell Count Condition
* **Mathematical Requirement:** For a Chi-Square test of independence to be valid using standard asymptotic distributions, the expected frequency ($E_{ij}$) in each cell of the $2 \times 2$ contingency table must be $\ge 5$.
* **Empirical Observation:** Given our massive total sample size ($N = 12,615$), the minimum cell frequency in our gender-by-alcohol cross-tabulation vastly exceeds the required threshold of 5, providing an exceptionally stable mathematical foundation.

---

## 3. Summary of Output Visualizations

The statistical analysis script (`02_Statistical_Analysis.ipynb`) systematically exports three core figures to the outputs directory to visually support our findings:

1.  **`stacked_alcohol_gender.png` (Composition of Alcohol Use Status by Gender):** A 100% stacked bar chart detailing the exact percentage distribution of "Current User" vs. "No Use" within both male and female groups to evaluate the raw difference in proportions.
2.  **`confidence_interval_diff.png` (Chi-Square Critical Values vs. Actual Statistic):** A sensitivity plot comparing our calculated Chi-Square test statistic ($\chi^2 \approx 1.8152$, $\text{df} = 1$) against the critical value barriers at 80%, 85%, 90%, 95%, and 99% confidence levels. It visually demonstrates that the actual statistic fails to cross even the lowest critical value threshold, directly aligning with our fail-to-reject decision ($p \approx 0.178$).
3.  **`alcohol_by_gender_and_age.png` (Current Alcohol Use Proportion by Age and Gender):** A dual-factored bar plot illustrating alcohol use percentages stratified by age (12–18) and grouped by gender. This reveals a clear upward trajectory in alcohol prevalence as students age, while allowing side-by-side gender comparisons within each cohort.
