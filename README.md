# 🎬 IMDb Movie Review Sentiment Analysis

This project performs sentiment analysis on the **IMDb dataset of 50,000 movie reviews**, classifying them as either **positive** or **negative**. It offers a comprehensive walkthrough of a **Natural Language Processing (NLP)** pipeline, covering data cleaning, feature extraction, model training, and evaluation.

A unique aspect of this project is the **comparative analysis** of three popular text vectorization techniques:

- Bag-of-Words (BoW) using `CountVectorizer`
- TF-IDF using `TfidfVectorizer`
- Word Embeddings via a custom-trained `Word2Vec` model

---

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Methodology](#methodology)
  - [1. Data Loading and Cleaning](#1-data-loading-and-cleaning)
  - [2. Text Preprocessing](#2-text-preprocessing)
  - [3. Feature Extraction and Modeling](#3-feature-extraction-and-modeling)
- [📊 Results](#results)
- [🚀 How to Use](#how-to-use)
- [🧩 Dependencies](#dependencies)

---

## 📘 Project Overview

The main objective is to build and evaluate an ML model for **binary sentiment classification**. The process includes:

- Preprocessing the raw text data
- Encoding labels
- Applying multiple vectorization techniques
- Training and comparing models using a `RandomForestClassifier`

---

## 🧪 Methodology

### 1. Data Loading and Cleaning

- Loaded IMDb dataset using `pandas`
- Checked for null values and removed **418 duplicate reviews**
- Encoded sentiment labels:  
  - `positive` → `1`  
  - `negative` → `0` using `LabelEncoder`

---

### 2. Text Preprocessing

A `preprocess_text()` function was used to clean and normalize the reviews:

- Lowercase conversion
- HTML tag removal (`<br />`)
- URL removal
- Punctuation and number removal
- Stopword removal (NLTK)
- Emoji removal & whitespace normalization
- Tokenization and lemmatization using `WordNetLemmatizer`

---

### 3. Feature Extraction and Modeling

Three vectorization techniques were explored. A `RandomForestClassifier` was trained on each representation:

#### a. Bag-of-Words (BoW)
- Used `CountVectorizer` (top 30,000 features)
- Tried both unigrams and bigrams

#### b. TF-IDF
- Used `TfidfVectorizer` to assign weights to words based on their document frequency

#### c. Word2Vec Embeddings
- Trained a custom `Word2Vec` model using `gensim`
- Converted reviews to document vectors by **averaging word vectors**

---

## 📊 Results

| Feature Extraction Method        | Classifier              | Test Accuracy |
|----------------------------------|--------------------------|---------------|
| BoW (Unigrams)                   | Gaussian Naive Bayes     | ~68.6%        |
| BoW (Unigrams)                   | Random Forest Classifier | ~85.0%        |
| BoW (Unigrams + Bigrams)         | Random Forest Classifier | ~85.5%        |
| TF-IDF (Unigrams)                | Random Forest Classifier | ~84.8%        |
| Word2Vec (Averaged Embeddings)   | Random Forest Classifier | ~83.9%        |

📝 **Conclusion:**  
The **Bag-of-Words with bigrams** approach yielded the highest accuracy. While Word2Vec is a powerful embedding technique, **word frequency alone proved to be more effective** in this task.

---

## 🚀 How to Use

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/imdb-sentiment-analysis.git
   cd imdb-sentiment-analysis
