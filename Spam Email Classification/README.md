# **Spam Ham Classification using NLP**

This mini-project focuses on classifying emails as **spam** or **ham** (non-spam) using Natural Language Processing (NLP) techniques. The classification is performed using two popular models: **Bag of Words (BoW)** and **Term Frequency-Inverse Document Frequency (TF-IDF)**. The project demonstrates the step-by-step process of data preparation, text preprocessing, model training, and evaluation.

## **Project Overview**

In this project, emails are classified into two categories:
- **Ham**: Non-spam or legitimate emails.
- **Spam**: Unwanted or malicious emails.

This task is achieved using machine learning techniques along with NLP-based feature extraction methods like **Bag of Words (BoW)** and **TF-IDF**. The project includes the following steps:
1. Data Exploration
2. Text Preprocessing
3. Feature Extraction using Bag of Words and TF-IDF
4. Model Training and Evaluation
5. Comparison of Model Performance

## **Table of Contents**
1. [Installation](#installation)
2. [Data Exploration](#data-exploration)
3. [Text Preprocessing](#text-preprocessing)
4. [Modeling: Bag of Words](#modeling-bag-of-words)
5. [Modeling: TF-IDF](#modeling-tfidf)
6. [Model Evaluation](#model-evaluation)
7. [Results](#results)

## **Installation**

To run this project locally, follow the instructions below:

### 1. Clone the repository:
```bash

git clone https://github.com/AnasHasan786/Applied-NLP.git
cd Spam Email Classification
```

### 2. Install the necessary dependencies:
```bash
pip install -r requirements.txt
```

## **Data Exploration**

The dataset used in this project is email_classification.csv which contains the following columns:
- `email`: The content of the email.
- `label`: The label (ham or spam).

```
emails = pd.read_csv("data/email_classification.csv")
```

### **Dataset Info**

- Total rows: 179
- Labels: 100 "ham" emails, 79 "spam" emails

## **Text Preprocessing**

Text preprocessing is crucial for cleaning the data and making it ready for model training. The steps involved include:-

1. Removing non-alphabetic characters
2. Converting text to lowercase
3. Tokenizing and lemmatizing words
4. Removing stopwords

## **Modeling: Bag of Words**

In this step, I use CountVectorizer to extract features using the Bag of Words technique. I select the top 2500 features (words) and use a binary model to create a sparse matrix representation of the emails.

```bash
from sklearn.feature_extraction.text import CountVectorizer

cv = CountVectorizer(max_features=2500, binary=True, ngram_range=(2, 2))
X = cv.fit_transform(corpus_emails).toarray()
```

## **Modeling: TF-IDF**

I use TfidfVectorizer to transform the text data into a matrix of TF-IDF features. This technique helps emphasize important words while downplaying less relevant ones.

```bash
from sklearn.feature_extraction.text import TfidfVectorizer

tv = TfidfVectorizer(max_features=2500, ngram_range=(2, 2))
X = tv.fit_transform(corpus_emails).toarray()
```

## **Model Evaluation**

The performance of both models is evaluated using accuract and classification reports. Metrics include precision, recall, and F1-score for both "ham" and "spam" classes.

### **Evaluation for Bag of Words (BoW)**

* Accuracy: 0.75
* Classification Report:

```bash
                    precision      recall      f1-score    support
         False           0.55        1.00          0.71         11
          True           1.00        0.64          0.78         25 
      accuracy                                     0.75         36
     macro avg           0.78        0.82          0.75         36
  weighted avg           0.86        0.75          0.76         36
```

  ### **Evaluation for TF-IDF**

  * Accuracy: 0.92
  * Classification Report:

```bash
                    precision      recall      f1-score    support
         False           0.95        0.90          0.93         21
          True           0.88        0.93          0.90         15 
      accuracy                                     0.92         36
     macro avg           0.91        0.92          0.92         36
  weighted avg           0.92        0.92          0.92         36
```

## **Results**

Based on the evaluation, the TF-IDF model outperforms the Bag of Words model:

* TF-IDF Accuracy: 92%
* Bag of Words Accuracy: 75%

The TF-IDF model also shows better precision, recall, and F1-score for both "ham" and "spam" classes.
