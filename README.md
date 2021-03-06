# stock-tracker [![Build Status](https://travis-ci.org/alecc08/stock-tracker.svg?branch=master)](https://travis-ci.org/alecc08/stock-tracker) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/f858fc237304469f812601459d3f3e29)](https://www.codacy.com/app/alecc/stock-tracker?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=alecc08/stock-tracker&amp;utm_campaign=Badge_Grade)
NodeJS stock tracker. Read historical stock data from an API to store in local DB. Offer API to integrate data into a dashboard. https://github.com/alecc08/stock-tracker-dashboard

Using Alphavantage API to get data. You can get your own API key from them at https://www.alphavantage.co

### Note: Alphavantage is free but they request not to query them over 100 calls per minute. Please respect this limit or contact them to work something out. This application shouldn't have any need get anywhere near that volume, as the data returned will be from the database unless the stock wasn't already obtained.

## API Endpoints:

### Update a stock:
```
POST
/stocks

 - Params
   -stockCode

Ex: POST /stocks stockCode:MSFT
```

### Auto update stocks
There's a cron job that runs at your time of choosing to update all stocks in the database. You can change this time in ```config.js```

### Get a stock:
```
GET
/stocks

 - Params
   -stockCodes : Comma seperated list of stocks
   -start : YYYY-MM-DD format date start
   -end   : YYYY-MM-DD format date end

Ex: GET /stocks stockCodes:MSFT,FB,GOOG start:2017-01-01 end:2017-02-02
```

### Get an account:
```
GET
/accounts

 - Params
   -accountId 

Ex: POST /stocks stockCode:MSFT
```

### Create an account:
```
POST
/accounts
 - Params
    -accountName
```

### Run sql on DB

> To run some custom sql directly into the db, simply run the dbConsole.js file with node
```
node dbConsole
```
>Then you can run any sql statement followed by a semicolon to execute the query. E.g.
```
SELECT * FROM stock_history;
```