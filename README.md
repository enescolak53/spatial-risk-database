# spatial-risk-database
Spatial database architecture using PostgreSQL and PostGIS for real estate seismic risk analysis.



## Project Overview
This project is a spatial database architecture designed to analyse property listings in relation to seismic risk zones. Developed using **PostgreSQL** and **PostGIS**, this system imports raw, unstructured property data (CSV) and converts it into highly structured, map-ready geometric objects (WGS 84 / SRID 4326).

##  Data Architecture: Real, Simulated Data
To build a robust and scalable analysis platform, the database schema is strictly separated into two logical categories:
- **Real-World Data Tables:** Contains actual property listings, preserving the raw and authentic state of the real estate market.
- **Simulated & Risk Data Tables:** Dedicated tables structured specifically for algorithmic risk scoring, proximity simulations, and spatial modeling against fault lines. 

##  Key Engineering Features

- **Robust ETL Process:** Raw real estate data is imported into a staging table. Dirty data (e.g., shifted columns due to commas in descriptions, missing coordinates) is handled defensively.
- **Spatial Transformation:** Converted `TEXT` coordinates into `DOUBLE PRECISION` and utilized PostGIS functions (`ST_MakePoint`, `ST_SetSRID`) to project 24,000+ properties onto a real-world map.
- **Defensive Database Design:** Prevented system rollbacks during bulk imports by validating data integrity *after* staging, rather than strictly enforcing types upon initial insertion.

##  Tech Stack
- **Database:** PostgreSQL 16+
- **Spatial Extension:** PostGIS
- **Management Tool:** pgAdmin 4
- **Version Control:** Git & GitHub

## Repository Contents
- `risk_platform_db.sql`: The complete database dump, including table schemas, PostGIS configurations, and **24,000+ cleansed spatial records**.

## ⚙️ How to Run Locally

-Download the spatial-risk-database file to your computer,
-Set up the database:
-Open pgAdmin 4.
-Create a new, empty database (e.g. test_database).
-In the browser menu on the left, right-click on the database you have just created and select the PSQL Tool.
-In the black terminal window that opens, enter the command within the following  "    " to run the backup file:
      "  \i 'C:/path/to/your/folder/spatial-risk-database/afad_rsik_platform_db.sql'  "           
-And enter (Ensure the folder path does not contain spaces or special characters (like ü, ş, ç). We recommend moving the .sql file to a simple path like C:/proje/ before running.) 
Once you scroll to the bottom of the page and click the green **‘Commit changes’** button, the repository setup guide will be complete.
