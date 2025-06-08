# Bank Reviews Scraper and Cleaner

## Overview
This project scrapes user reviews from Google Play Store apps for three Ethiopian banks: Commercial Bank of Ethiopia, Bank of Abyssinia, and Dashen Bank. It preprocesses the scraped data by cleaning, formatting, and filtering to prepare a combined dataset for analysis.

## Features
- Scrapes up to a specified number of reviews per bank from Google Play Store.
- Uses the English interface of Google Play Store for scraping.
- Cleans data by removing reviews with missing essential fields and duplicates.
- Formats review dates uniformly.
- Combines cleaned reviews across banks only if each meets a minimum review count threshold.
- Outputs the combined cleaned dataset as a CSV file.

## Usage
1. Configure app IDs, review counts, and minimum required reviews per bank.
2. Run the scraper to fetch reviews.
3. Clean the scraped data (no language filtering applied).
4. Validate if each bank meets the minimum reviews count.
5. Save combined dataset when criteria are met.

## Notes
- The `lang` parameter controls the Play Store interface language, not review content language.
- Review content language filtering is not applied in this version.
- The scraper may return fewer reviews than requested depending on app availability.

## Dependencies
- `google_play_scraper`
- `pandas`
- `datetime`

## Output
A CSV file containing cleaned reviews from all banks that meet the minimum review count.

---

This setup enables easy data collection and preprocessing for sentiment analysis or customer feedback studies on Ethiopian bank mobile apps.
