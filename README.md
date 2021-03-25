# Udacity Data Engineering Course

## Intro
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

## Data set

Their are two data sets. one is user activity log and song meta.

- User Activity Log
```
{
    "artist":null,
    "auth":"Logged In",
    "firstName":"Walter",
    "gender":"M",
    "itemInSession":0,
    "lastName":"Frye",
    "length":null,
    "level":"free",
    "location":"San Francisco-Oakland-Hayward, CA",
    "method":"GET",
    "page":"Home",
    "registration":1540919166796.0,
    "sessionId":38,
    "song":null,
    "status":200,
    "ts":1541105830796,
    "userAgent":"\"Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.143 Safari\/537.36\"",
    "userId":"39"
}
```

- Song meta data
```
{
    "num_songs": 1, 
    "artist_id": "ARJIE2Y1187B994AB7", 
    "artist_latitude": null, 
    "artist_longitude": null, 
    "artist_location": "", 
    "artist_name": "Line Renaud", 
    "song_id": "SOUPIRU12A6D4FA1E1", 
    "title": "Der Kleine Dompfaff", 
    "duration": 152.92036, 
    "year": 0
}
```

## Postgres Data Models / Table Schema / Star Schema

#### songplays(Fact Table)
|column|type|extra|
|-|-|-|
|id|SERIAL|PRIMARY KEY|
|start_time|TIMESTAMP|NOT NULL|
|user_id|INT|NOT NULL|
|level|VARCHAR||
|song_id|VARCHAR||
|artist_id|VARCHAR||
|session_id|INT|NOT NULL|
|location|VARCHAR||
|user_agent|VARCHAR|NOT NULL|
#### users(dimenion table)
|column|type|extra|
|-|-|-|
|user_id|INT|PRIMARY KEY|
|first_name|VARCHAR||
|last_name|VARCHAR||
|gender|VARCHAR||
|level|VARCHAR|NOT NULL|

#### songs(dimenion table)
|column|type|extra|
|-|-|-|
|song_id|VARCHAR|PRIMARY KEY|
|title|VARCHAR||
|artist_id|VARCHAR||
|year|INT||
|duration|FLOAT||

#### artists(dimenion table)
|column|type|extra|
|-|-|-|
|artist_id|VARCHAR|PRIMARY KEY|
|name|VARCHAR||
|location|VARCHAR||
|lattitude|NUMERIC||
|longitude|NUMERIC||

#### time(dimenion table)
|column|type|extra|
|-|-|-|
|start_time|TIMESTAMP|PRIMARY KEY|
|hour|INT||
|day|INT||
|week|INT||
|month|INT||
|year|INT||
|weekday|VARCHAR||


## Current Environment info

- Docker
- Python 3(latest is recommended. currently 3.9 is latest)
- python-libraries(psycopg2, pandas)
- Jupyter(notebook) **only for test**


## Steps For ELT complete process
- Run create_tables.py file to Create Database and tables.
- Then run elt.py file to process all songs and log data from data folder and store them in database.


