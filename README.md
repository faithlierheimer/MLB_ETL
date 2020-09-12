# ETL Project: MLB Stats
This project aims to Extact, Transform, and Load data from a variety of sources into a database.

## Sources Used
-Stadium Beer Pricing from [data.world](https://data.world/makeovermonday/2018w43-what-will-a-beer-cost-you-at-every-major-league-ba) (CSV Format)

-MLB Stats from [MLB-StatsAPI](https://github.com/toddrob99/MLB-StatsAPI/wiki) (JSON Format)

-Web Scrape from [ESPN STATS](http://www.espn.com/mlb/history/leaders/_/breakdown/season/year/2018) (BeautifulSoup Object)

## Beer Pricing

### Extract:

A CSV was downloaded from [data.world](https://data.world/makeovermonday/2018w43-what-will-a-beer-cost-you-at-every-major-league-ba). 

The CSV was then imported into a Pandas data frame in a Jupyter Notebook.

### Transform:

Using Pandas, the "nickname" column was dropped and all the columns were renamed.

### Load:

Once the Pandas dataframe was cleaned up, it was converted into a dictionary usings the Pandas to_dict() function. 

With the data in the proper format, it was then loaded into a MongoDB Collection: beer_dict

MongoDB was selected to store our data since our data has common attributes (primarily team name), but has different numbers of columns and data points. Our data is also more heterogenous than homogenous and therefore is better suited for MongoDB.

## MLB API

### Extract:

Using [MLB-StatsAPI](https://github.com/toddrob99/MLB-StatsAPI/wiki.) a variety of hitting statistics were collected.

First the player IDs were collected using the lookup_player command from the API Wrapper. Using a for loop, the player ID was used to collect the selected stats for each player. The collected data was then loaded into  Pandas data frame. 

### Transform:

Pandas was used to drop duplicate values and null values were replaced with zeros.

### Load:

Again, Pandas was used to convert the data frame into a dictionary and then uploaded to a new MongoDB Collection: api_dict

## ESPN Web Scrape

### Extract:

Data was scraped from [ESPN STATS](http://www.espn.com/mlb/history/leaders/_/breakdown/season/year/2018)


Utlizing the BeautifulSoup Module, the html information was scraped from ESPN's website. Using the find and find_all functions, the statistics were pulled from the BeautifulSoup object.

Then a for loop was used to add each player's statistic into a Pandas Dataframe.

### Transform:

Pandas was used to drop the following statistics: ['YRS','BB','G','2B','3B'].

These were dropped to match the data from the API statistics.

### Load:

Pandas was used again to convert the data into a dictionary and then loaded into a new MongoDB Collection: scraped_stats_dict
