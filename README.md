# Using AI To Analyse Trends In Book Publishing

## Project Overview

This project explores the major themes and trends in recently published books by using Natural Language Processing (NLP) and topic modelling techniques. Inspired by discussions around repetition and patterns in present-day publishing, the project looks at the rise of similar themes in modern book descriptions. Book metadata and descriptions were gathered from the Google Books API. Following the preprocessing of the text data, Latent Dirichlet Allocation (LDA) was implemented to identify, categorise, and analyse the most frequently occurring topics within the dataset. The results provide insight into recurring genres and narrative themes in current publishing.
---

## Data Source
Google Books API
  - Metadata fields used include title, authors, publication date, categories, ratings (where available), and book descriptions.
  - A total of 1000 unique books were collected using authenticated requests via Google Cloud.

---
## API Integration
   - Connected to the Google Books API using a Google Cloud project and API key.
   - Implemented pagination and throttling to manage quota limits.
   - Deduplicated records using unique volume IDs.

 ## Exploratory Data Analysis (EDA)
   - Analysed missing values across metadata fields.
   - Examined publication year distribution and description length.
   - Identified sparsity in user-generated ratings data.

## Text Preprocessing
   - Lowercasing text
   - Removing HTML tags and non-alphabetic characters
   - Tokenisation and stopword removal
   - Filtering out very short descriptions to improve topic quality


## Text Representation Strategies

Different models require different text representations:

- **Bag-of-Words (BoW)** — used for LDA and NMF  
- **TF–IDF weighting** — used for NMF  
- **Transformer embeddings** — used for BERTopic and SBERT clustering  

---

## LDA — Latent Dirichlet Allocation (Baseline)

LDA was implemented using the gensim library as a probabilistic baseline topic model.

**Process:**
- Tokenised descriptions converted to bag-of-words vectors
- Dictionary and corpus constructed
- Multiple topic counts tested
- Final model trained with 10 topics
- Top keywords extracted per topic
- Each book assigned a dominant topic based on highest probability

**Purpose:**
- Provide an interpretable probabilistic baseline
- Establish reference topic structure
- Support comparison with embedding-based models

**Observed limitation:**
- Topic overlap due to short, promotional text
- Some themes too broad

---

## NMF — Non-negative Matrix Factorisation (Baseline)

NMF was implemented as a matrix factorisation alternative to LDA, often more effective for shorter texts.

**Process:**
- TF–IDF document-term matrix constructed
- NMF decomposition applied
- Topic-word matrices extracted
- Top words per topic reviewed and labelled

**Purpose:**
- Compare factorisation vs probabilistic topic modelling
- Improve topic separation on sparse short text
- Provide second classical baseline

---

## BERTopic — Transformer-Based Topic Modelling (Baseline)

BERTopic combines transformer embeddings with clustering-based topic extraction.

**Process:**
- Sentence-transformer embeddings generated
- Dimensionality reduction applied
- Density-based clustering performed
- Topic keywords extracted using class-based TF–IDF

**Purpose:**
- Provide a modern embedding-based baseline
- Capture semantic similarity beyond word frequency
- Improve topic coherence for short descriptions

---

## SBERT + Clustering (Advanced Model)

An advanced modelling approach was implemented using SBERT embeddings with clustering.

**Process:**
- Book descriptions converted to dense semantic vectors using SBERT
- Embeddings clustered into topic groups
- Cluster parameters tuned for separation and stability
- Clusters manually interpreted and labelled

**Advantages:**
- Captures contextual meaning
- Handles short text better than BoW models
- Produces clearer semantic grouping
- Reduces topic overlap

---

## Model Comparison Strategy

Models are compared using:

- Topic keyword clarity
- Theme interpretability
- Topic overlap assessment
- Distribution balance
- Qualitative coherence review

Using multiple modelling approaches strengthens methodological validity and supports evidence-based model selection rather than assumption-driven choice.

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
## Challenges and Limitations
- **API Quotas:**  
  Google Books API quota limits required careful request throttling and the use of multiple queries to reach the target dataset size.
  
- **Sparse Rating Data:**  
  Over 80% of books lacked ratings information, limiting the use of ratings as an analytical feature.
  
- **Variable Description Quality:**  
  Many books had very short or missing descriptions, reducing the final corpus used for topic modelling to 359 high-quality documents.

- **Topic Overlap:**  
  Some topics are broad or overlapping, which is a known limitation of probabilistic topic models when applied to heterogeneous text.

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
