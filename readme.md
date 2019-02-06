# Guide: Exploring & Processing Datasets

## planning

- what questions need to be answered
- how much time available for exploration
- how should final results be exported

## overview of data sources

- how many files
- file concatenation (dataset split across multiple files)
- size 
- format
- automated export or hand-made spreadsheet
- importable
- level of cleaning required
- spreadsheets: multiple sheets

## general data quality

- duplicates
- consistency: data recorded each time for event
- accuracy: does data reflect reality
- completeness: missing values
- objectivity: reasons for data bias
- precision
- validity: conformation to business rules, formats, standards
- credibility: data reasonable
- staleness: age of data

## overview of data fields

### field type

- numeric, binary, categorical (nominal/ordinal), text, id, geographic, financial, time

### field completeness

- what percentage of rows have a non-empty value
- placeholder values

### field quality

- format errors
- spelling and typing mistakes

### field usefulness

- can this field be used in answering one of the questions required
- is the meaning of values clear from the column name

##### id fields

- used to link entities between data sources
- exploratory outer joins to see what links up and what does not 

##### numeric fields

- min, max, avg
- distribution
- units of measurement

##### categorical fields

- nominal: no inherent order (categories)
- ordinal: order important (very poor, bad, fair, good, perfect)
- number of distinct values
- fixed, or may change in future
- distribution (counts grouped by)
- identify numeric fields that can be aggregated over

##### text fields

- can rows be linked by looking at key words
- normalization: casing, remove punctuation, whitespace, stopwords
- nlp overview: most common words, verbs, entities

##### geographic fields

- formats: GPX, KMZ, GIS, latlng, geojson
- which projection
- identify id fields
- objects: points, areas, polygons, strings

##### financial fields

- currency / denomination
- time span of data set: inflation relevance
- decimal and thousand seperator

##### time fields

- consistent data format
- min, max
- multiple entries for object: meaning of time between events
- aggregation periods: dependant on industry, organisation


## tooling

### relation databases

#### when to use

- relational data
- need to use other tools that require SQL interface
- sql expertise on hand
- data too big to fit in memory
- require GIS queries via postgis, spatialite
- possiblity of app web app built on top of analysis
- clean once, several analysts can connect to server (postgres)
- window functions

#### options

- sqlite
- postgres

#### query and visualization

- datasette
- jetbrains datagrip (pycharm)
- grafana (time series)
- superset

### python

#### when to use

- rapid exploration
- python expertise on hand
- simple datasets without relational mapping
- need to move data from and to excel files
- list libraries used in `requirements.txt`

#### options

- pandas

#### query and visualization

- jupyter notebook
- altair
- bokeh
- seaborn

## frontend

### approaches

#### build static html files

Use a python script with database connection and templating library
to build out html files.

- psycopg2 (postgres)
- sqlite3 (stdlib, sqlite)
- jinja2 (templating)
- pathlib, shutil, distutils (stdlib)
- pygal
- altair

#### build single page app (SPA)

Use when high levels of interactivity required and dataset can fit into browser.

- vuejs
- d3

### libraries

#### visualizations

- d3


#### geo

- leaflet & extensions
- turf.js


## interpretation

It is imperative that each visualization is given a title and intepretation. Do not
assume that anyone else will understand what the viz signifies. Make even the most
obvious interpretation clear.


## deployment

### static output

- github pages
- rsync to server with nginx


## general

- always rename columns to lower snake case: "Functional Location" -> "functional_location"

## reading material

TODO

