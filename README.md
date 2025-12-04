# Gender Differences in Provider Communication About Colorectal Cancer Screening

## Project Description

This repository contains the analytic code and documentation for a study examining gender differences in provider communication about colorectal cancer (CRC) screening among U.S. adults aged 45 years and older. The analysis uses the 2024 Health Information National Trends Survey (HINTS 7) and was completed as part of the Advanced Data Analysis course (Fall 2025) final project.

The project evaluates whether men and women differ in being told by a healthcare provider that multiple CRC screening test options exist. The analysis also assesses whether this association varies by age group (45-49, 50-64, 65+).
---

## Dataset Description

- **Data source:** Health Information National Trends Survey 7 (HINTS 7, 2024), a nationally representative survey of U.S. adults conducted by the National Cancer Institute.The dataset includes information on health behaviors, communication patterns, healthcare access, and demographic characteristics.
For this project:

Only adults aged 45 and older were included.

Complete-case analysis was performed for all variables used in regression models.

Survey weights, strata, and cluster variables were applied to obtain nationally representative estimates.

---

## Files Included

- **`ADA final project.Rmd`**  
  Complete R Markdown file containing all data cleaning, recoding, survey design setup, descriptive tables, logistic regression models, effect modification testing, and diagnostics.

- `hints7_public.rda`  
  Public-use dataset from HINTS 7 (2024) used in this analysis.

- `README.md`  
  This file.

---

## What the Code Does

The R Markdown file performs the following steps:

### 1. Load required data and packages  
- Loads the public-use HINTS 7 dataset (`hints7_public.rda`).  
- Uses `pacman` to install and load all needed libraries.

### 2. Clean and recode variables  
- Converts age to numeric and restricts to adults 45+.  
- Creates age groups ("45-49", "50-64", "65+").  
- Recodes:
  - Sex at birth 
  - Provider CRC communication 
  - Race/ethnicity 
  - Education 
  - Household income 
  - Health insurance `
  - Healthcare utilization   
- Reassigns special HINTS missing codes (???9, ???7, ???4) to `NA`.

### 3. Construct analytic dataset  
- Selects final analysis variables including design weights.  
- Removes cases with any missing data (`drop_na()`) during complete case analysis.  
- Saves the final analytic dataset as `hints_cc`.

### 4. Create sample flow diagram  
A flow diagram is generated using DiagrammeR to visualize:
Total sample
Adults aged 45+
Exclusions due to missing exposure/outcome
Exclusions due to missing covariates
Final analytic sample

### 5. Specify survey design  
- Defines weights, strata, and clusters using:
  - Sampling weights`PERSON_FINWT0`
  - Strata`VAR_STRATUM`
  - Clusters `VAR_CLUSTER`

### 6. Generate Table 1  
- Uses `table1` package to create descriptive statistics stratified by gender.  
- Exports the table as an HTML file and then PNG (`table1.png`).

### 7. Survey-weighted logistic regression  
- **Unadjusted model:** examining gender and CRC communication 
- **Adjusted model:** Adjusts for age group, race/ethnicity, education, income, insurance, and healthcare visits.  
- Outputs odds ratios, 95% CIs, and p-values.

### 8. Effect modification  
- Tests interaction between sex at birth and age group.  

### 9. Model diagnostics 
- Fits an unweighted logistic regression for assumption testing.  
- Checks:
  - **Multicollinearity** with VIF  
  - **Model fit** using Hosmer-Lemeshow  
  - **Influential observations** using diagnostic plots

---

## How to Run the Code

1. **Download or clone the repository.**  

2. **Place hints7_public.rda in the project directory**

3. **Open ADA final project.Rmd in RStudio**

4. **Ensure all required packages install successfully**

5. **Run the R Markdown file**
Click Knit to generate the HTML report

##Author

Feven Gebrekidan
Course: Advanced Data Analysis . Fall 2025
Date: December 2025
