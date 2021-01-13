# Wiener-Linien-Project
* Author: Stefan Roland Schwingenschlögl
* email: stefan.roland.schwingenschloegl@gmail.com
___

# Overview
This is my first project here on github. As Data Source I used the Wiener Linien Realtime API (http://www.wienerlinien.at/ogd_realtime/doku/). 
This project is used to analyze delays at specific stations in Vienna's public transport network. For this analysis I chose the stations "Margeretenplatz / Schönbrunner Straße", "Kardinal-Nagl Platz", "Gudrunstraße" and "Schönbrunn". These stations are important to me because I have either lived near these places myself or I have viewed a flat there. This should give me personal information about the area relevant to me where public transport works best.

In this specific analysis I collected delay data for the four mentioned stations on 17.12.2020 from 8:30 to 11:00. This data got directly inserted into the database after calling the API. In order to be able to follow the analysis without a database connection, this file is also stored in the folder `realtime_data` as `data_17_12.csv`. 

## Technology used:
* Programming Languages: Python, SQL
* Main focus:
  - Data Collection
  - API Calls
  - Connect Python with Database
* New Libraries:
  - pyodbc (Python)
  - beautifulSoup (Python)
  - requests (Python)

## Projectflow
For the analysis, first the data on all stations and travel routes, etc. were downloaded and cleaned if necessary. In the next step, this "static" data was written into an MS SQL Server database. The database architecture was taken from the structure of the csv files.  In the next step, a script was written that automatically queries the real-time API of Wiener Linien and writes the data to a stage-delay table in the database. In the last step, the data will be analysed.

All in all the following files are in this project:

1. `set_up_structure.ipynb`: Set up folder structure and download all static files from the Wiener Linien API documentation site
2. `static_file_cleaning.ipynb`: Clean static files 
3. `create_database.ipynb`: Create a new database and all tables in SQL Server Express using pyodbc. Insert all cleaned static files into these tables
4. `API_exctraction.ipynb`: Call the Wiener Linien API once a minute, get all relevant data from the json response and write automatically into the database
5. `data_exploration.ipynb`: Data analysis of the retrieved data

UNDER CONSTRUCTION
