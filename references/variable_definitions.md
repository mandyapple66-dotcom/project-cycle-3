# Reference Part 1: Variable and Group Definitions

This document outlines the data processing logic and definitions used for the Project Cycle 3 analysis. It ensures transparency and reproducibility by documenting how raw data was transformed into analytical variables.

## 1. Variable Coding Reference
The source of the data is the **YRBS 2007 Codebook**. The raw categorical values were recoded into binary variables to facilitate two-sample proportion inference.

### Behavior Variable: `CurrentAlcoholUse`
We transformed the frequency-based codes into a binary "Success/Failure" format:
* **Recoding Logic:**
    * **Success (1):** Codes **2 through 7**. These represent students who reported drinking alcohol on at least one day during the past 30 days.
    * **Failure (0):** Code **1**. This represents students who reported drinking 0 days (no alcohol use) during the past 30 days.
* **Justification:** This transformation allows us to compare the *proportion* of students currently using alcohol rather than the average frequency of use.

## 2. Group Definitions
The analysis compares two independent populations based on biological sex.

* **Exposed Group (1): Female**
    * **Source Code:** `WhatIsYourSex` = 1.
    * **Analytical Label:** Defined as 1 to serve as the primary group of interest for this proportion comparison.
* **Comparison Group (0): Male**
    * **Source Code:** `WhatIsYourSex` = 2.
    * **Analytical Label:** Defined as 0 to serve as the baseline comparison group.

## 3. Summary of Binary Variables
Following the Project Cycle 3 Section 6 guidelines, our final processed dataset utilizes the following binary structure:

| Variable Name | Value = 1 | Value = 0 |
| :--- | :--- | :--- |
| `Sex_Binary` | Female (Exposed Group) | Male (Comparison Group) |
| `Alcohol_Binary` | Current Alcohol Use (Success) | No Current Alcohol Use (Failure) |

---
**Note:** All missing values (NaN) and invalid response codes were excluded during the data cleaning phase (documented in `01_Data_Cleaning.ipynb`) to ensure statistical validity.
