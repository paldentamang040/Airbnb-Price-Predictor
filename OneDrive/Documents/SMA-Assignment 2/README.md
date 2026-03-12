# AML-3203 — Assignment 2

**Text Analytics & Simple Recommender**

## Dataset

- **Source:** Kaggle — **Twitter US Airline Sentiment**
- **URL:** https://www.kaggle.com/datasets/crowdflower/twitter-airline-sentiment

**How to download (Kaggle API):**

```bash
# 1) Install and authenticate Kaggle CLI (put kaggle.json in ~/.kaggle)
pip install kaggle
# 2) Download the dataset
kaggle datasets download -d crowdflower/twitter-airline-sentiment -p data/ --unzip
```

---

## What to submit

1. **Report**:
   - **Markdown (`.md`) — preferred**, or
   - Word (`.docx`), or
   - PDF (`.pdf`)

2. **Code** — one **Jupyter notebook**:
   - `A2_<lastname_firstname>.ipynb`.

---

## Objectives

Using the Twitter US Airline Sentiment dataset, you will:

1. Discover themes using **topic modeling**. There are different algorithms and techniques to achieve this — you must justify your choice.
2. Measure and analyze **sentiment** using **LLMs** (you can get free access through platforms like **Groq or Google AI Studio**).
3. Implement a **simple Knowledge-based recommender system**, where the input is a tweet (query) and the system returns the top 10 most similar tweets.

---

## Requirements & Rubric

### 1) Problem framing (10%)

- One crisp business question (e.g., “What themes drive negative experiences, and what content should we surface/reply to first?”).
- Define a success signal/metric (coverage of top issues, improved surfacing, etc.).

### 2) Data import & EDA (5%)

### 3) Text preprocessing (10%)

### 4) Topic modeling (15%)

### 5) Sentiment analysis (20%)

### 6) Knowledge-based recommender (20%)

### 7) Communication, reproducibility & presentation (20%)

- Clear figures; concise narrative.
- Notebook runs **top-to-bottom**, fixed random seeds, params documented.
- No need to prepare a PPT; just present your work by explaining your report and code.

---

## Report structure (guide)

1. Title & team; dataset source & date downloaded
2. Business question & success metric
3. Methods: preprocessing, toipc-modeling, sentiment, recommender
4. Results: concise figures/tables
5. Recommendations: 2–3 actionable ideas; how to validate (A/B test)
6. Limitations & ethics
7. References (libraries, dataset)

---
