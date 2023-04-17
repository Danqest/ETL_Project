# ETL_Project

## Y Finance

# Extract 

# Transform

# Load



## Nasdaq Scarping

# Extract Using the libraries request and beautifulSoup to make an http request and define variables such as main.url and page when requesting to the url 'https://www.nasdaq.com'. The beautiful soup function is used to parse the HTML content of the page response using HTML parser. The parsed HTML is stored in the variable soup. The a_tags variable will contain a list of all the anchor tags that match the given criteria, which have the class name 'content-feed__card-title-link'. 

# Transform # variable to_mongo is used to create a Pandas DataFrame to store the extracted data in a tabular format, where each row represents an article title and its corresponding URL. 

# Load mongo variable is establsihing a connection to a MongoDB server, creating a database and a collection, and converting the data from the to_mongo variable, which is a DataFrame, to a list of dictionaries. 

