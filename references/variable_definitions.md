# Reference Part 1: Variable and Group Definitions

This document outlines the data processing logic and definitions used for the Project Cycle 3 analysis. It ensures transparency and reproducibility by documenting how raw data was transformed into analytical variables.

## 1. Variable Coding Reference

The source of the data is the YRBS 2007 Codebook. The raw categorical values were recoded into appropriate formats (binary and discrete numeric) to facilitate categorical data analysis and stratified trend evaluation.

### Behavior Variable: CurrentAlcoholUse
We transformed the frequency-based codes into a binary "Success/Failure" format:
* **Recoding Logic:**
  * **Success (1):** Codes 2 through 7. These represent students who reported drinking alcohol on at least one day during the past 30 days.
  * **Failure (0):** Code 1. This represents students who reported drinking 0 days (no alcohol use) during the past 30 days.
* **Justification:** This transformation allows us to compare the proportion of students currently using alcohol rather than the average frequency of use.

### Demographics Variable: HowOldAreYou (New)
To observe developmental trends across adolescence, the original CDC age category codes were mapped directly into their corresponding biological ages as an integer variable:
* **Recoding Logic:**
  * Code `1` $\rightarrow$ `12` (Represents 12 years old or younger)
  * Code `2` $\rightarrow$ `13` (Represents 13 years old)
  * Code `3` $\rightarrow$ `14` (Represents 14 years old)
  * Code `4` $\rightarrow$ `15` (Represents 15 years old)
  * Code `5` $\rightarrow$ `16` (Represents 16 years old)
  * Code `6` $\rightarrow$ `17` (Represents 17 years old)
  * Code `7` $\rightarrow$ `18` (Represents 18 years old or older)
* **Justification:** Converting codes into chronological age integers (`Age_Numeric`) allows the analysis script to dynamically filter specific ranges (e.g., focusing on the 12–18 age bracket) and plot chronological trend lines or grouped bar charts sequentially.

---

## 2. Group Definitions

The primary analysis compares independent populations based on biological sex.

* **Exposed Group (1): Female**
  * **Source Code:** `WhatIsYourSex` = 1.
  * **Analytical Label:** Defined as 1 to serve as the primary group of interest for proportion comparisons.
* **Comparison Group (0): Male**
  * **Source Code:** `WhatIsYourSex` = 2.
  * **Analytical Label:** Defined as 0 to serve as the baseline comparison group.

---

## 3. Summary of Processed Variables

Following the Project Cycle 3 guidelines, our final processed dataset utilizes the following structured format ($N = 12,615$):

| Variable Name | Data Type | Value / Label Definition |
| :--- | :--- | :--- |
| **Sex_Binary** | Binary (0/1) | `1` = Female (Exposed Group)<br>`0` = Male (Comparison Group) |
| **Alcohol_Binary** | Binary (0/1) | `1` = Current Alcohol Use (Success)<br>`0` = No Current Alcohol Use (Failure) |
| **Age_Numeric** | Numeric (Integer) | Discrete chronological age values ranging from **12 to 18**. |

> **Note:** All missing values (`NaN`), blank entries, and invalid response codes were systematically stripped out using an explicit file parser with `utf-8-sig` encoding during the data cleaning phase to prevent hidden BOM characters from corrupting the analytical sample.
