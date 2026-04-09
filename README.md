# 📈 Stock Market Sentiment Analysis

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/NLP-Sentiment%20Analysis-orange" />
  <img src="https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikit-learn&logoColor=white" />
  <img src="https://img.shields.io/badge/Logistic%20Regression-Classifier-9cf" />
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen" />
</p>

## 📌 Overview

This project applies **Natural Language Processing (NLP)** to financial news headlines in order to predict **DJIA (Dow Jones Industrial Average)** stock market movements. By analyzing the sentiment embedded in daily news, the model classifies whether the stock price will **go up (1)** or **go down / stay the same (0)**.

---

## 📂 Dataset

The dataset (`Stock Headlines.csv`) contains 25 top daily news headlines spanning multiple years, alongside a binary market label.

| Column | Description |
|---|---|
| `Date` | Date of the trading day |
| `Label` | `1` = Stock price went up, `0` = Stayed the same or went down |
| `Top1` – `Top25` | Top 25 news headlines for that day |

> **Train/Test Split:** Data before 2015 is used for training; data from 2015 onward is used for testing.

---

## 🔍 Project Workflow

### 1. Data Loading & Exploration
- Loaded the dataset using **Pandas**
- Visualized the distribution of the `Label` column (balanced binary classification)
- Dropped rows with missing values

### 2. Data Preprocessing
- Time-based train/test split: **pre-2015 → train**, **post-2014 → test**
- Removed all punctuation and special characters using **Regex**
- Converted all text to **lowercase**
- Merged the 25 headline columns into a single combined text per row

### 3. NLP Pipeline
For both train and test corpora:
- **Tokenized** each headline
- Removed **English stop words** (NLTK)
- Applied **Porter Stemming** to reduce words to their root form
- Joined processed tokens back into a clean string
- Built a **word corpus** for each split

### 4. Visualization
- Generated **WordCloud** visualizations for:
  - 📉 Headlines associated with *market decline*
  - 📈 Headlines associated with *market rise*

### 5. Feature Extraction
- Applied **CountVectorizer** with **bigram** (`ngram_range=(2,2)`) and `max_features=10,000`
- Captured two-word phrase relationships more relevant to financial sentiment

### 6. Model Training & Evaluation

Three classifiers were trained and compared:

| Model | Accuracy | Precision | Recall |
|---|---|---|---|
| **Logistic Regression** | ~85% | — | — |
| Random Forest | — | — | — |
| Multinomial Naive Bayes | — | — | — |

Performance evaluated using:
- Accuracy Score
- Precision & Recall
- Confusion Matrix (heatmap)

### 7. Prediction Function
- A reusable `stock_prediction()` function was created to predict on any arbitrary news headline
- Tested with random sample headlines from the test set

---

## 🛠️ Technologies Used

| Tool | Purpose |
|---|---|
| Python 3.x | Core programming language |
| Pandas / NumPy | Data loading and manipulation |
| NLTK | Stemming, stop word removal |
| scikit-learn | CountVectorizer, Logistic Regression, Random Forest, Naive Bayes |
| Matplotlib / Seaborn | Visualization and confusion matrices |
| WordCloud | Keyword visualization by sentiment |
| Jupyter Notebook | Interactive development |

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy scikit-learn nltk matplotlib seaborn wordcloud jupyter
```

```python
import nltk
nltk.download('stopwords')
```

### Run the Notebook
```bash
git clone https://github.com/MehmetErtass/Stock_Sentiment_Analysis.git
cd Stock_Sentiment_Analysis
jupyter notebook STOCK_SENTIMENT_ANALYSIS.ipynb
```

---

## 📁 Project Structure

```
Stock_Sentiment_Analysis/
│
├── STOCK_SENTIMENT_ANALYSIS.ipynb   # Main notebook
├── Stock Headlines.csv              # Dataset
└── README.md                        # Project documentation
```

---

## 💡 Sample Prediction

```python
sample_news = "Federal Reserve raises interest rates amid inflation fears"
result = stock_prediction(sample_news)
# Output: 0 → Price will go up | 1 → Price will stay same or go down
```

---

## 👨‍💻 Author

**Mehmet Ertaş**  
[![GitHub](https://img.shields.io/badge/GitHub-MehmetErtass-181717?logo=github)](https://github.com/MehmetErtass)
