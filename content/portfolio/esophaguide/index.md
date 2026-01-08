---
title: "EsophaGuide - Assisted Diagnosis System"
date: 2020-12-15
summary: "Mobile-friendly diagnostic assistance application for swallowing disorders"
tags:
  - medical
  - software
categories:
  - Healthcare Technology
weight: 1
---

## The Challenge

Working with doctors specializing in swallowing disorders, we needed to create a system to assist in complicated diagnoses based on patient history and test results.

## Our Solution

We built and deployed a **mobile-friendly application** that allows physicians to go step by step through:

- Patient history collection
- Test results analysis
- Previous surgery and treatment review
- Diagnostic scoring and visualization

The application implements custom scoring algorithms developed in close partnership with medical experts. Points are assigned to different conditions and test results, then mapped to x,y,z coordinates on a 3D graph where different regions indicate different likely diagnoses.

![EsophaGuide Screenshot](/images/esophaguide.png)

## Key Features

- **Step-by-step data collection** - Guided workflow for physicians
- **Custom scoring algorithms** - Developed with domain experts
- **3D visualization** - Color-coded plotting of diagnostic regions
- **Bulk import** - File upload for testing large datasets
- **Automated testing** - Validation against hundreds of patient records

## Results

- Successfully validated against expert clinical assessments
- Matches diagnoses made by specialized physicians
- Automated testing ensures algorithm accuracy over time
- Mobile-friendly interface allows use in clinical settings

## Technologies Used

- Python for backend processing
- Custom scoring algorithms
- 3D data visualization
- Mobile-responsive web application
