---
title: "Inter-Rater Agreement Analysis"
date: 2021-10-31
summary: "Statistical analysis of diagnostic agreement among physicians using Fleiss' kappa"
tags:
  - stats
  - medical
  - r
categories:
  - Data Science
weight: 3
---

## The Challenge

When a doctor develops a new diagnostic model, it's crucial to validate how consistently multiple physicians apply it. We needed to measure the level of agreement between multiple doctors when classifying patient diagnoses.

## Our Solution

We implemented **Fleiss' kappa analysis** in R to statistically measure inter-rater reliability among multiple physicians evaluating patient cases.

## Why Fleiss' Kappa?

Unlike Cohen's kappa (which only supports two raters), Fleiss' kappa is designed for:

- Multiple raters (we had 4 physicians)
- Categorical classification data
- Statistical validation of agreement levels

## Technical Implementation

We used R with Jupyter notebooks for reproducible analysis:

```R
data <- read.csv("specific.csv", header=FALSE)
kappam.fleiss(data, exact=FALSE, detail=TRUE)
```

The results showed:
- **173 subjects** evaluated
- **4 raters** participating
- **Kappa = 0.788** indicating substantial agreement
- Detailed breakdown by diagnosis category

## Data Preparation

Our Python preprocessing pipeline:
- Transformed raw data from per-patient-per-doctor rows to matrix format
- Created separate analyses for three different assessment types
- Automated the data normalization process

## Results

- Validated strong agreement (kappa = 0.788) across physicians
- Identified specific diagnoses with highest/lowest agreement
- Provided statistical confidence (p-value < 0.05) that agreement wasn't chance
- Delivered actionable insights within hours of receiving data

## Technologies Used

- R with irr package for kappa calculations
- Python for data preprocessing
- Jupyter notebooks for reproducible analysis
- Conda for environment management
