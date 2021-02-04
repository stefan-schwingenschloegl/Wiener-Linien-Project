# Wiener-Linien-Project
* Author: Stefan Roland Schwingenschlögl
* email: stefan.roland.schwingenschloegl@gmail.com
___

# Overview
This is my first project here on github. As Data Source I used the Wiener Linien Realtime API (http://www.wienerlinien.at/ogd_realtime/doku/). 
This project is used to analyze delays at specific stations in Vienna's public transport network. For this analysis I chose the stations "Margeretenplatz / Schönbrunner Straße", "Kardinal-Nagl Platz", "Gudrunstraße" and "Schönbrunn". These stations are important to me because I have either lived near these places myself or I have viewed a flat there. This should give me personal information about the area relevant to me where public transport works best.

In this specific analysis I collected delay data for the four mentioned stations on 02.02.2021 from 8:16 to 22:00. This data got directly inserted into the database after calling the API. Since I have extracted the data from the API and the data ownership does not lie with me, I cannot publish the raw data. This data is only used for this analysis. The analysis is accessible in the file 'data_exploration.ipynb'.

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

# Results
In this section the results of my analysis can be seen.

| stop_name                            | count | mean  | std   | min    | 25%   | 50% | 75%   | max   |
|--------------------------------------|-------|-------|-------|--------|-------|-----|-------|-------|
| Gudrunstraße                         | 662.0 | 1.16  | 73.85 | -286.0 | -27.0 | 0.0 | 11.75 | 728.0 |
| Kardinal-Nagl-Platz U                | 162.0 | 45.28 | 65.96 | -55.0  | 0.0   | 5.5 | 78.00 | 297.0 |
| Margaretenplatz, Schönbrunner Straße | 506.0 | 4.36  | 87.07 | -770.0 | -46.0 | 5.5 | 44.00 | 499.0 |
| Schönbrunn U                         | 169.0 | -4.36 | 71.87 | -234.0 | -38.0 | 0.0 | 5.00  | 284.0 |
