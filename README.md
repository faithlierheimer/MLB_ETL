# ETL Project: MLB Stats
This project aims to Extact, Transform, and Load data from a variety of sources into a database.

## Sources Used
-Stadium Beer Pricing from [data.world}(https://data.world/makeovermonday/2018w43-what-will-a-beer-cost-you-at-every-major-league-ba)

-MLB Stats from [MLB-StatsAPI](https://github.com/toddrob99/MLB-StatsAPI/wiki.)

-Web Scrape from [ESPN STATS](http://www.espn.com/mlb/history/leaders/_/breakdown/season/year/2018)

## Beer Pricing

### Extract

A CSV was downloaded from [data.world}(https://data.world/makeovermonday/2018w43-what-will-a-beer-cost-you-at-every-major-league-ba). 

The CSV was then imported into a Pandas dataframe in a Jupyter Notebook.

### Transform

Using Pandas, the "nickname" column wad dropped and all the columns were renamed.

### Load

Once the Pandas dataframe was cleaned up, it was converted into a dictionary usings the Pandas to_dict() function. 

With the data in the proper format, it was then loaded into a MongoDB Collection.