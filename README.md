# ETL_Project:

By Arthi Ranganathan, Colin Brooks, Cydney Goodwin-Hamel, Doug Hooper, and Uzma Azhar

# Yahoo Finance Stock Price Data

## Purpose:

Stock price data from Yahoo Finance (YF) is pulled from the yfinance Python library, which scrapes price data from the YF website over a defined start & end date for a particular stock ticker. This raw data is then fed into the ETL process to clean the data and prepare it for loading into the database, which in this case is PostgreSQL. This type of price data could be used in a reinforcement learning model for trading or used for backtesting trading strategies relative to the market.

## Extract:

Stock prices for the SP500 (SPY) were chosen to be downloaded from the yfinance Python libary from the 1/1/2022 start date to the 12/31/2022 end date. This downloaded data is then returned into a pandas dataframe indexed by date.

## Transform:

The resulting dataframe is adjusted to add a Ticker column to denote the ticker pulled (SPY) as well as adding the indexed dates to their own column. Other columns (open, high, low, close, volume) are renamed to more unique names (p_open, p_high, p_low, p_close, p_volume) to better align with usage in a database.

## Load:

As mentioned previously, the PostgreSQL database is used for this demonstration of ETL. This database was chosen as many different stock prices for the same (or other varying) dates can be added to a "prices" table, or other stock specific or market data (short availability, industry, sector, etc) can be added to database tables in a relational manner which provides a good use-case. The engine connection was created to load the data into postgres. A declarative_base was used to allow access to metadata and the database was connected using SQLAlchemy. The DataFrame was converted to a dictionary of records and a new instance was created. Session was created and used to handle the new instances and allowed for adding and committing data into the existing dataframe and table. And finally, a query was created to confirm the data was appropriately loaded in to the database.

# Nasdaq Market News Scraping

## Purpose:

Market news headlines and associated article URL links are scraped directly from the NASDAQ website using the beautifulsoup4 and requests Python libraries. The raw data is then fed into the ETL process to clean the data and prepare it for loading into the database, which in this case is MongoDB. This type of headline and URL data could be used in a NLP machine learning or further expanded to scrape data from each individual article's text.

## Extract:

Using the Python libraries 'request' and 'beautifulSoup' to make a http request and define reusable variables to hold the "nasdaq.com" URL and 'page' to store the requested data when using the request.get function. The beautifulsoup function is used to parse the HTML content of the 'page' response using HTML parser. The parsed HTML is stored in the variable 'soup'. The 'soup.find_all()' function is used to find all occurrences of the anchor element "a" which is consolidated into a list and further parsed for the hrefs (partial URLS) as well as the article titles; urls and titles are the looped into their own lists.

## Transform:

Both of the aformentioned lists are cleaned of invalid (blank) array components and then consolidated into a 'to_mongo' variable, which is a pandas Dataframe; the to_mongo variable appends the partial URLs to the originally defined 'nasdaq.com' variable which ultimately results in a Dataframe with two columns: article_title and article_url (which is a completed url).

## Load:

As mentioned previously, the MongoDB database is used for this demonstration of ETL. This database was chosen as there are no relational components of the data being collected which is simply variations of text data. As the data is non-relational, MongoDB provides a good use-case. The 'mongo' variable is used to establish a connection to a MongoDB server, creating a database and a collection, and converting the data from the to_mongo variable, which is a DataFrame, to a list of dictionaries. The data is then uploaded to the database.
