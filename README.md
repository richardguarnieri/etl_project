# ETL Project - US Accidents
ITESM Data Analytics Boot Camp

Group Members: Erik Hernandez, Richard Guarnieri, Jonathan Ruiz and Abigail Guzmán

### Data Sources
We used two data sources for this project:
* Kaggle: https://www.kaggle.com/sobhanmoosavi/us-accidents
* United States Census: https://data.census.gov/cedsci/table?t=Commuting&tid=ACSST1Y2019.S0804&hidePreview=false

### Data Clean Up
#### Extracting and Transforming US Accidents Data
This file contains originally details of 4.2 million traffic accidents that took place in the United States, from February 2016 to Dec 2020.
We transform this dataset as following:
* Filtered the data only for 2019.
* Compressed the CSV file to allow the csv to be pushed within GitHub's threshold.
* Renamed the columns removing parenthesis and % sign to allow db table creation.

#### Extracting and Transforming Census Data
Our second file was found in the site data.census.gov and this is a dataset that contains the means of transportation to work by some caracteristics for workplace geography.
We transform this dataset as following:
* Extract the total for every state.
* Remove rows for car type classification.
* Remove irrelevant columns about transportation caracteristics.
* We leave the columns related to age and gender.
* Since the caracteristics columns were as string type, we changed it to floats and romoved caracters like commas and porcentages.
* We extract US code states from [ssa.gov](https://www.ssa.gov/international/coc-docs/states.html) wich later was converted to database and merged it with our census db.
* We renamed and reordered the columns.

### Loading into Postgres DB
We load and join our two databases to Postgres
![Image of PDB US Accidents](/screenshots/us_accidents_db.png)
![Image of PDB US Census](/screenshots/us_census_db.png)

### Data Analysis
We did an aditional transformation to our database: We grouped by State and count the total accidents per State and merged it with our join database.
We calculated the accidents per total vehicles % rate and analize the accidents per vehicles for the Top 15 States and the accidents for population from 16 to 19 age.

#### Accidents per Vehicles - Top 15 States
![Image of Accidents per vehicles](/screenshots/accidents_per_vehicles.png)

#### Accidents per Vehicles - Age Group 16-19 Years
![Image of Accidents per vehicles](/screenshots/accidents_per_vehicles_age16_19.png)
