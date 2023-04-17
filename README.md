# ETL_Project

## Y Finance

# Extract Importing pandas as pd, from sqlalchemy import create_engine, create_engine is a function used for connection to databases, and import yfinance imports the yfinance library for retreiving financial data. yf.downlaod function is used to retreive stock market data for the SPY ticker (S&P 500 ETF) with secified start and end parameters. 

# Transform The retreived S&P 500 data is downloaded in a DataFrame as variable name df_spy. A new column is added called ticker and sets its value as 'SPY' using df_spy['ticker'] = 'SPY'. Several columns from the dataframe were renamed to indicate the open, high, low, close, adjusted close, and volume fields. 

# Load A database engine using SQLAlchemy library to connect to a PostgreSQL database with the specified strings such as username, password, hotname, port number, and database name was created. The declarative_base(), engine, engine.connect(), and columns names were created to establish a connection to a PostgreSQL databse, defines a SQLAlchemy model for a table named 'SPYfinance', creates the table in the database, and sets up a sessions object for performing database operations. The df_spy DataFrame was converted into a list of dictionaries where each dictionary represents a row of data from the DataFrame. The to_dict() method of the DataFrame is used with the argument 'records' to specify that the resulting dictionary should have a list of dictionaries with each dictionary representing a record (row) from the DataFrame. Finally, a query was made using the SQLAlchemy engine, loading the data into a Pandas DataFrame using the pd.read_sql_query() function



## Nasdaq Scarping

# Extract Using the libraries request and beautifulSoup to make an http request and define variables such as main.url and page when requesting to the url 'https://www.nasdaq.com'. The beautiful soup function is used to parse the HTML content of the page response using HTML parser. The parsed HTML is stored in the variable soup. The a_tags variable will contain a list of all the anchor tags that match the given criteria, which have the class name 'content-feed__card-title-link'. 

# Transform # variable to_mongo is used to create a Pandas DataFrame to store the extracted data in a tabular format, where each row represents an article title and its corresponding URL. 

# Load mongo variable is establsihing a connection to a MongoDB server, creating a database and a collection, and converting the data from the to_mongo variable, which is a DataFrame, to a list of dictionaries. 

