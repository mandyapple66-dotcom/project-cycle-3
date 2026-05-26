# Reference Part 2: Methodology and Statistical Assumptions

This document justifies the selection of the statistical methods used in this project and verifies that the necessary mathematical assumptions are satisfied for a valid inference.

## 1. Method Choice
**Statistical Method:** Two-Proportion z-test

### Justification:
The research question compares the proportion of current alcohol use between two distinct groups (Male and Female students).
* **Group Variable (Independent):** `Sex_Binary` is a categorical variable with two levels (0 = Male, 1 = Female).
* **Response Variable (Dependent):** `Alcohol_Binary` is a categorical variable with two levels (0 = No Use, 1 = Current Use).
* **Objective:** Since both variables are binary and we are comparing two independent populations, the **Two-Proportion z-test** is the most appropriate method to determine if a significant difference exists between the two proportions.

## 2. Statistical Assumptions Assessment

To ensure the validity of the z-test and the resulting p-value, the following conditions have been evaluated:

### I. Independence
* **Individual Independence:** Each participant in the YRBS 2007 survey is an individual student. There is no reason to believe that the alcohol use of one student influences another in a way that violates independence at the national scale.
* **10% Condition:** The total sample size (n ≈ 12,659) is significantly less than 10% of the entire population of high school students in the United States. This ensures that the sampling without replacement does not affect the independence of the trials.

### II. Randomization
* **Data Source:** The data comes from the Youth Risk Behavior Surveillance System (YRBSS), which utilizes a multi-stage cluster sampling design to produce a representative sample of students in the United States. This satisfies the requirement for a random or representative sample.

### III. Success/Failure Condition (Large Sample Approximation)
For the sampling distribution of the difference in proportions to be approximately normal, each group must have at least 5 "successes" and 5 "failures."
* **Mathematical Requirement:** $n_1\hat{p}_1 \ge 5$, $n_1(1-\hat{p}_1) \ge 5$, $n_2\hat{p}_2 \ge 5$, $n_2(1-\hat{p}_2) \ge 5$.
* **Empirical Observation:**
    * Female Successes: 2,864 | Failures: 3,561
    * Male Successes: 2,853 | Failures: 3,381
* **Conclusion:** All values are significantly greater than 5 (the minimum is 2,853). Therefore, the normal approximation for the z-test is highly appropriate.

---
**Summary:** All statistical assumptions for the Two-Proportion z-test are satisfied. The results of the hypothesis test and confidence intervals can be considered reliable.
