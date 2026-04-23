# AI Book Trends Analysis

## Overview
This project uses AI and Natural Language Processing (NLP) to analyse thematic trends in book publishing. It collects book metadata and descriptions from the Google Books API, cleans and preprocesses the text, applies topic modelling techniques, and prepares the outputs for interactive visualisation in Power BI.

The project compares a classical topic modelling approach, **Latent Dirichlet Allocation (LDA)**, with **BERTopic**, including different clustering methods such as **HDBSCAN**, **KMeans**, and **Agglomerative Clustering**. The aim is to identify dominant and emerging themes in books and explore how these patterns can be analysed over time.

## What the project does
- Collects book data from the **Google Books API**
- Cleans and preprocesses book descriptions
- Applies **LDA** and **BERTopic** topic modelling
- Compares multiple BERTopic clustering approaches
- Generates final labelled topic outputs
- Prepares a **Power BI-ready dataset**
- Supports interactive dashboard analysis of book themes and trends

## Repository contents
This repository contains:

- **Code**
  - Python notebook(s) and scripts used for:
    - data collection
    - preprocessing
    - topic modelling
    - evaluation
    - exporting final outputs

- **Raw dataset**
  - The saved raw dataset collected from the Google Books API

- **Processed / final dataset for Power BI**
  - The final cleaned dataset with metadata and topic assignments, ready for dashboard use

- **Power BI file**
  - The `.pbix` dashboard file used to visualise themes, categories, and publishing trends

## Main models used
- **LDA (Latent Dirichlet Allocation)** – baseline topic model
- **BERTopic + HDBSCAN**
- **BERTopic + KMeans**
- **BERTopic + Agglomerative Clustering**

## Output
The final output of the project is an interactive **Power BI dashboard** that allows exploration of:
- publishing trends over time
- book categories
- topic distributions
- comparisons between topic modelling methods

## Notes
This project was developed as part of a final year university dissertation and focuses on both analytical modelling and practical visualisation.
