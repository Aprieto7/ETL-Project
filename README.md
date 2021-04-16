# ETL-Project

## EXTRACTION

The goal of this project is to compare trends in cryptocurrency values with popularity in media and frequency of hits in public forums. In order to do this, we will extract cryptocurrency data from Kaggle documenting daily highs, lows, and volumes traded, as well as scrape posts from the r/CryptoCurrency page on Reddit to analyze traction gained.


### r/CryptoCurrency

Link: https://www.reddit.com/r/CryptoCurrency/top/.json?f=flair_name%3A%22TRADING%22

- This data will be scraped from the Reddit website, and pulled into Jupyter Notebooks in .json formats to ultimately be cleaned up. 

### Kaggle "Criptocurrencies" 

Link: https://www.kaggle.com/gorgia/criptocurrencies?select=bitcoin_usd_gwa.csv

- This data will be downloaded in CSV format before ultimately being loaded into the database. 



## TRANSFORMATION

### r/CryptoCurrency
- Using some webscraping, we are able to pull in data from the Reddit website. 
- Reddit provides many columns indicating whether the post was liked, flared, etc. which leads to many 'N/A' values. We were able to drop 40 columns quickly using `drop.na()` function.
- There is an `over_18` column that you can filter to just rows set as `False` in order to exclude posts with explicit language.
- We ended up dropping 112 down to 68 just columns by removing N/As, 0s, as well as redundant and useless columns.

### Kaggle "Criptocurrencies" 
- The Kaggle website is provides relatively clean data. We chose Bitcoin, Ethereum, Bitcoin Cash.


## LOAD


