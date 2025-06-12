# Fintech App Review Analysis – Ethiopian Banks

---

This project analyzes user feedback from the Google Play Store for three major Ethiopian mobile banking apps:  
**Commercial Bank of Ethiopia**, **Bank of Abyssinia**, and **Dashen Bank**.

It includes scraping, cleaning, sentiment analysis, theme extraction, data storage in Oracle, and insights visualization. All designed to simulate a real-world fintech data pipeline.

---

## Objectives

- Collect and clean real user reviews from mobile banking apps.
- Quantify customer sentiment using traditional and transformer-based models.
- Extract common themes from reviews using NLP techniques.
- Store enriched review data in a relational Oracle database.
- Visualize trends and provide actionable product/UX recommendations.

---

## Tools

| Category         | Tools Used |
|------------------|-------------|
| Scraping         | `google-play-scraper` |
| NLP & Sentiment  | TextBlob, VADER, DistilBERT (Transformers) |
| Theme Extraction | spaCy |
| Data Storage     | Oracle XE 21c, `oracledb` |
| Visualization    | Matplotlib, Seaborn, WordCloud |


---


---

## Review Scraping & Cleaning

- Scraped Google Play reviews for:
  - `com.combanketh.mobilebanking` (CBE)
  - `com.boa.boaMobileBanking` (BOA)
  - `com.dashen.dashensuperapp` (Dashen)
- Cleaned for:
  - Missing `review`, `rating`, or `date`
  - Duplicate reviews
  - Uniform date formatting
- Only included banks with at least **400 valid reviews**

> **Note**: Google Play's `lang` parameter only affects interface language, not review content language.

---

##  Sentiment & Theme

### Sentiment Analysis:
- Models used:
  - `TextBlob`
  - `VADER`
  - `distilbert-base-uncased-finetuned-sst-2-english` (Transformers)
- Final sentiment labels adjusted using star ratings

### Thematic Analysis:
- Used spaCy + rule-based clustering
- Themes: `"App Experience"`, `"Login Issues"`, `"Crash/Performance"`, `"Positive Feedback"`, etc.
- Outputs:
  - `all_banks_reviews_with_sentiment.csv`
  - `all_banks_reviews_with_themes.csv`
  - `all_bank_reviews.csv` (merged)

---

## Oracle Database Storage

- Created relational schema in Oracle XE:
  - `banks(id, name)`
  - `reviews(id, review, rating, sentiment, themes, ...)`
- Used `oracledb` to insert >2,400 enriched records into Oracle
- Verified table creation, insertion, and review counts

---

## Visual Insights

Generated and saved 5 key plots:

1. **Sentiment Distribution by Bank**
2. **Theme Frequency by Bank**
3. **Word Cloud (Positive Reviews)**
4. **Rating Distribution**
5. **Monthly Sentiment Trends**



## Insights

### Positive Drivers
- Fast, smooth transfers
- Simple and intuitive interface

### Common Pain Points
- Login failures and blocked accounts
- Crashes, app not loading, poor stability

### Bank Comparison

| Bank | Strength | Issue |
|------|----------|-------|
| CBE | UI and speed praised | Login reliability |
| BOA | Support praised | App errors common |
| Dashen | Popular UI branding | Crash complaints |

### Recommendations

- Add **biometric login** & reset support
- Include **crash reporting** and analytics
- Provide **FAQ/chatbot** for faster help

---

## Bias & Limitations

- Only **English reviews** were analyzed
- Emoji-based sentiment was not analyzed
- Dataset skewed toward **extreme sentiment** (1⭐/5⭐)
- Many moderate or Amharic-language users may be underrepresented

---

## How to Run

1. Ensure **Oracle XE** is installed and running on your machine.  
   (Default DSN: `localhost/XEPDB1`)

2. Install project dependencies using:
   ```bash
   pip install -r requirements.txt
    ```
3. Run each stage of the pipeline in sequence:

- Add **biometric login** & reset support

- Scrape live reviews from the Google Play Store

- Clean and preprocess the data

- Perform sentiment analysis and extract themes

- Store enriched data in Oracle

- Generate visualizations and insights

---

> **Note**: No raw review data is included in the repository. The pipeline must fetch fresh data during execution.
---

## Installation

```bash
pip install pandas matplotlib seaborn transformers spacy google-play-scraper vaderSentiment textblob wordcloud oracledb

```
