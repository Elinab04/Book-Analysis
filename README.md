# Using AI To Analyse Trends In Book Publishing

## Project Overview

This project explores the major themes and trends in recently published books by using Natural Language Processing (NLP) and topic modelling techniques. Inspired by discussions around repetition and patterns in present-day publishing, the project looks at the rise of similar themes in modern book descriptions. Book metadata and descriptions were gathered from the Google Books API. Following the preprocessing of the text data, Latent Dirichlet Allocation (LDA) was implemented to identify, categorise, and analyse the most frequently occurring topics within the dataset. The results provide insight into recurring genres and narrative themes in current publishing.
---

## Data Source
Google Books API
  - Metadata fields used include title, authors, publication date, categories, ratings (where available), and book descriptions.
  - A total of 1000 unique books were collected using authenticated requests via Google Cloud.

---
## Methodology
1. **API Integration**
   - Connected to the Google Books API using a Google Cloud project and API key.
   - Implemented pagination and throttling to manage quota limits.
   - Deduplicated records using unique volume IDs.

2. **Exploratory Data Analysis (EDA)**
   - Analysed missing values across metadata fields.
   - Examined publication year distribution and description length.
   - Identified sparsity in user-generated ratings data.

3. **Text Preprocessing**
   - Lowercasing text
   - Removing HTML tags and non-alphabetic characters
   - Tokenisation and stopword removal
   - Filtering out very short descriptions to improve topic quality

4. **Topic Modelling**
   - Applied Latent Dirichlet Allocation (LDA) using a bag-of-words representation.
   - Trained a 10-topic model on cleaned book descriptions.
   - Interpreted and manually labelled topics based on top keywords.
   - Assigned a dominant topic to each book for analysis and visualisation.

---
# Tools and Technologies Used
- **Python**
- **Google Colab**
- **Google Books API**
- **pandas** – data manipulation
- **requests** – API communication
- **matplotlib** – visualisation
- **nltk** – text preprocessing
- **gensim** – LDA topic modelling

---
## Key Findings
- Despite the diversity of books, several recurring themes emerged, including:
  - Romance and emotional relationships
  - Fantasy and magical worlds
  - Historical and literary fiction
  - Family relationships and conflict
  - Social and cultural commentary
- A small number of broad, human-experience-focused topics dominated the dataset, suggesting that contemporary book descriptions often emphasise universal life themes alongside genre-specific elements.

---
## Challenges and Limitations
- **API Quotas:**  
  Google Books API quota limits required careful request throttling and the use of multiple queries to reach the target dataset size.
  
- **Sparse Rating Data:**  
  Over 80% of books lacked ratings information, limiting the use of ratings as an analytical feature.
  
- **Variable Description Quality:**  
  Many books had very short or missing descriptions, reducing the final corpus used for topic modelling to 359 high-quality documents.

- **Topic Overlap:**  
  Some LDA topics were broad or overlapping, which is a known limitation of probabilistic topic models when applied to heterogeneous text.

---

## Repository Structure
- `notebook.ipynb` – Main Google Colab notebook containing data collection, EDA, and LDA modelling
- `google_books_1000_raw.csv` – Raw dataset collected from the Google Books API
- `README.md` – Project overview and documentation

---
## Credits
- Google Books API for providing access to book metadata
- Project inspired by discussions of thematic repetition in modern publishing
- Developed as part of an academic data analytics project
