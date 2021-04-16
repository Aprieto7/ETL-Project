<img width="695" alt="image" src="https://user-images.githubusercontent.com/69091074/115091069-1eb36880-9edc-11eb-80f4-dfefe1166481.png">


# ETL-Project

The goal of this project is to collect the data needed to compare trends in cryptocurrency values with popularity in media and frequency of hits in public forums. In order to do this, we will extract cryptocurrency data from Kaggle documenting daily highs, lows, and volumes traded, as well as scrape posts from the r/CryptoCurrency page on Reddit to analyze traction gained.

## EXTRACTION

### r/CryptoCurrency

Link: https://www.reddit.com/r/CryptoCurrency/top/.json?f=flair_name%3A%22TRADING%22

- This data will be scraped from the Reddit website, and pulled into a Jupyter Notebook in `.json` formats using `requests` to be cleaned up. 

### Kaggle "Criptocurrencies" 

Link: https://www.kaggle.com/gorgia/criptocurrencies?select=bitcoin_usd_gwa.csv

- This data will be downloaded in CSV format and pulled into Jupyter for clean up before ultimately being loaded into the database. 

## TRANSFORMATION

- Using `pandas` library to view each set, we were able to clearly look at the data and clean up where necessary.

### r/CryptoCurrency

- Reddit provides many columns indicating whether the post was liked, flared, etc. which leads to many 'N/A' values. We were able to drop 40 columns quickly using `drop.na()` function.
- There is an `over_18` column that you can filter to just rows set as `False` in order to exclude posts with explicit language.
- We ended up dropping 112 down to just 54 columns by removing N/As, 0s, as well as redundant and useless columns.
- Sample of cleaned data:<img width="1159" alt="Screen Shot 2021-04-16 at 5 23 51 PM" src="https://user-images.githubusercontent.com/69091074/115089826-c7f85f80-9ed8-11eb-9aef-e69a0ca345f6.png">

### Kaggle "Criptocurrencies" 
- The Kaggle website is provides relatively clean data. We chose Bitcoin, Ethereum, Bitcoin Cash.
  1) Fetch the data and use .info() to look at data.
  2) Look for the count of NA if any.
  3) Append needed columns for crypto currency 
  4) Iterate over the data frame row by row.
  5) Drop not needed columns.
  6) Set index to the crypto name.
  7) Combining all tables.
  8) Load the data in sqlite

- Sample of cleaned data: <img width="468" alt="image" src="https://user-images.githubusercontent.com/69091074/115088480-d7c27480-9ed5-11eb-8ae8-120753fda73b.png">



## LOAD

- Using SQLAlchemy, both sets of cleaned up data were pushed in SQLite database (one table for each set of data). 
