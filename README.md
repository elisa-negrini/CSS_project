# Sentiment Analysis on the War in Ukraine

## Project Description

This project analyzes the evolution of public sentiment towards the Russia-Ukraine war through comments on social media platforms like Reddit and YouTube. The study focuses on how sentiment shifts in correspondence with major political and military events, with a particular emphasis on events involving Donald Trump and Volodymyr Zelensky. This analysis is situated within the field of Computational Social Science (CSS), applying sentiment analysis techniques to capture the emotional reactions of the online public.

## Methodology

### 1. Data Collection

Data was gathered from two primary sources:

* **Reddit**: Comments extracted from various subreddits related to keywords such as "Putin," "Russian invasion," "Trump," "Zelensky," and "war ukraine."
* **YouTube**: Comments from videos related to the war in Ukraine and to Trump and Zelensky.

### 2. Data Preprocessing

The text from the comments underwent the following preprocessing steps:

* **Text Cleaning**: Removal of URLs, user mentions, and non-alphanumeric characters.
* **Normalization**: Conversion of all text to lowercase.
* **Filtering**: Only comments with a score of at least 5 on Reddit were considered, and dates were managed to align data from both platforms.

### 3. Sentiment Analysis

A pre-trained Transformer-based model was used for the sentiment analysis:

* **Model**: `distilbert-base-uncased-finetuned-sst-2-english`, an efficient model for sentiment classification.
* **Multi-level Approach**:
    * **General Sentiment**: Classification of comments as positive, negative, or neutral.
    * **Contextual Sentiment**: Analysis of sentiment towards specific entities (Trump, Zelensky, peace) by examining the context of the sentences in which they are mentioned.
    * **Stance on the War**: Classification of comments as "pro-peace" or "pro-conflict" based on specific keywords.

## Main Results

The analysis revealed the following key findings:

* **General Sentiment on the War**:
    * On **Reddit**, 76.7% of comments related to the war have a negative sentiment, with an average score of -0.527.
    * On **YouTube**, 65.2% of comments have a negative sentiment, with an average score of -0.297.
* **Sentiment Towards Entities**:
    * **Trump**: Has a negative average sentiment on both platforms (-0.493 on Reddit, -0.379 on YouTube).
    * **Zelensky**: Sentiment towards Zelensky is also predominantly negative, with scores of -0.339 on Reddit and -0.361 on YouTube.
    * **Peace**: The concept of peace is associated with a negative sentiment (-0.442 on Reddit, -0.191 on YouTube), suggesting that discussions about peace often occur in contexts of criticism or frustration.
* **Correlations**: A strong positive correlation was observed between the general sentiment on the war and the sentiment towards Trump and Zelensky, indicating that discussions about these figures are closely linked to opinions on the conflict.

## Repository Structure

* `/data`: Contains the raw datasets collected from Reddit and YouTube.
* `/results`: Contains the processed datasets with sentiment analysis and the generated plots.
* `sentiment_analysis_final.ipynb`: The Jupyter notebook containing all the code for the analysis.
* `Computational_Social_Science.pdf`: The research paper describing the study in detail.

## How to Run the Project

1.  **Clone the repository**:
    ```bash
    git clone [https://github.com/elisa-negrini/CSS_project.git](https://github.com/elisa-negrini/CSS_project.git)
    ```

2.  **Install the dependencies**:
    Ensure you have Python installed, along with the following libraries:
    ```bash
    pip install pandas numpy re transformers torch matplotlib seaborn wordcloud scikit-learn nltk
    ```

3.  **Run the notebook**:
    Open and run the `sentiment_analysis_final.ipynb` file in a Jupyter environment. The notebook will load the data, perform the analysis, and save the results in the `/results` folder.
