# Wiener-Linien-Project
* Author: Stefan Roland Schwingenschlögl
* email: stefan.roland.schwingenschloegl@gmail.com
___

# Overview
This is my first project here on github. 
It is used to analyse delays at specific stations in Vienna's public transport network. This is important for me because I have either lived near these places myself or I have viewed a flat there. This should give me personal information about the area relevant to me where public transport works best.

## Projectflow
For the analysis, first the data on all stations and travel routes, etc. were downloaded and cleaned if necessary. In the next step, this "static" data was written into an MS SQL Server database. The database architecture was taken from the structure of the csv files.  In the next step, a script was written that automatically queries the real-time API of Wiener Linien and writes the data to a stage-delay table in the database. The data is then loaded from the stage table using an ETL process and cleaned using Python. The cleaned data should then be loaded into another table. In the last step, the clean data is loaded from this table and analysed.

All in all the following files are in this project:

* set_up_structure.ipynb: Set up folder structure and download all static files from the Wiener Linien API documentation site

UNDER CONSTRUCTION
