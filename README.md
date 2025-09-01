# Ukraine War Sentiment Analysis on Reddit & YouTube

This project provides a multi-level sentiment analysis pipeline for public discourse on the war in Ukraine, leveraging data from Reddit and YouTube comments. It focuses on general sentiment, pro-peace vs. pro-conflict stances, and contextual sentiment around key political figures like Trump and Zelensky.

---

## 🚀 Project Overview

The core objective was to develop a reproducible data science pipeline for large-scale text analysis. The project integrates custom scripts for data collection from social media platforms with modern natural language processing (NLP) techniques to analyze online political discourse.

### 📋 Prerequisites

To run this project, you will need:

* **Python 3.10+**
* **YouTube Data API v3** key
* **Reddit OAuth2** credentials (client ID/secret, username/password, user agent)

---

## ⚙️ Analysis Pipeline

The entire analysis is executed within the `sentiment_analysis_final.ipynb` Jupyter notebook, following a structured sequence of steps:

### 1. Data Collection

Two custom Python scripts were developed to gather data directly from the platforms' official APIs. The raw data is saved to `data/raw/` in JSON format.

* **YouTube:** Queries the YouTube Data API for videos related to the Ukraine war. It collects video metadata and top-level comments with a minimum like threshold, including selected replies.
* **Reddit:** Authenticates via OAuth2 and searches specific subreddits for posts related to the war. It retrieves post metadata and comment threads, recursively extracting comments above a minimum score threshold.

### 2. Preprocessing

Before analysis, the comment data undergoes a series of cleaning steps:

* Removal of URLs, mentions, and punctuation.
* Filtering comments by date and minimum score.
* Flagging comments that contain war-related keywords.

### 3. Sentiment Analysis

A pre-trained **transformer-based model** (`distilbert-base-uncased-finetuned-sst-2-english`) is used to classify sentiment. This produces both a categorical label (positive/negative) and a numeric sentiment score.

### 4. War Stance Classification

A **heuristic approach** based on predefined keyword lists is used to classify comments as having a pro-peace, pro-conflict, or neutral stance.

### 5. Entity-Level Contextual Sentiment

The pipeline identifies and extracts sentence windows where key entities (e.g., **Trump**, **Zelensky**, **Peace**) are mentioned. Sentiment is then scored specifically within these contexts to understand public opinion toward each entity.

---

## 📈 Key Findings (Example Run)

An example run of the pipeline yielded the following insights:

### Reddit

* **Comments:** Approximately 211,000 comments were collected, with 73,000 being directly war-related.
* **War Sentiment:** The average sentiment towards the war was strongly negative, with an average score of **−0.53**.
* **Entity Sentiment:** Contextual sentiment for Trump, Zelensky, and Peace was found to be predominantly negative.

### YouTube

* **Comments:** Around 151,000 comments were gathered, with 57,000 related to the war.
* **War Sentiment:** The average sentiment was negative, with a score of **−0.30**.
* **Entity Sentiment:** Mentions of both Trump and Zelensky were significant, with their contextual sentiment being mostly negative.
