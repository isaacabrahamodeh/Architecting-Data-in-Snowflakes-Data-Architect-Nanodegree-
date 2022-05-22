# Architecting-Data-in-Snowflakes-Data-Architect-Nanodegree-
In this project, an actual YELP and climate datasets of Las Vegas is used to build an enterprise data warehouse utilized in analyze the effects the weather on customer reviews of restaurants.

Restaurant rating data are sourced fro Yelp, the covid data is sourced from kaggle and the temperature and precipitation observations data are source from the Global Historical Climatology Network-Daily (GHCN-D) database

A leading industry cloud-native data warehouse system called Snowflake architecting the data in this project. The Data Warehouse (DWH) design in this project will be used for the purpose of reporting and online analytical processing (OLAP).

INITIAL STEPS

i. Snowflakes account creation

ii. Snowsql download and installation

iii. Database Projectdb creation

<img width="1484" alt="show db" src="https://user-images.githubusercontent.com/15156379/169716027-ea856de7-a09a-4ee6-bdca-ffcafae2835d.png">

iv. schema (Staging, ODS and Datawarehouse) Creation

v. Table creation in bothe schemas 


PROJECT DATA ARCHITECT DIAGRAM

The conceptual data architect diagram for the project was drawn in lucid see below
<img width="925" alt="Data Architect Diagram" src="https://user-images.githubusercontent.com/15156379/169716230-e6d29694-5f3e-4a5c-8147-91713ca23931.png">

The diagram show multiple data sources (Yelp, and weather data) ingesting data into the staging area. These raw JSON and CSV data were further transformed, curated and ingested into the Operational Data Store (ODS) and finally landed in the Datawarehouse for analytics work. All these data are stored in tables.

Tables are created in the staging schema and data are loaded into it for example the business;

<img width="519" alt="create table business" src="https://user-images.githubusercontent.com/15156379/169716776-ceb41f48-612b-4697-86ef-7cc36ce603d5.png">


<img width="843" alt="staging tables" src="https://user-images.githubusercontent.com/15156379/169716539-8880e554-b631-4bf0-9fa9-f904f91fdabd.png">

JSON and CSV files are copied into the tables in the staging schema using snowsql CLI

<img width="1585" alt="Transfer file 1" src="https://user-images.githubusercontent.com/15156379/169716689-8cc47a25-b64c-4846-a1b1-a3d2872182ad.png">

<img width="1585" alt="Transfer file 2" src="https://user-images.githubusercontent.com/15156379/169716703-d89831db-5748-4aca-9084-94b5f32c6314.png">


Similarly, tables are also created in ODS schema and data from the Staging schema tables are transformed and loadedonto those table

<img width="852" alt="ODS table" src="https://user-images.githubusercontent.com/15156379/169716572-82550646-23ab-4704-9516-0a47fc29fe45.png">

In general, 6 tables are created from the yelp dataset in both schemas and 2 tables are created fro the weather data. See the figure above.

Using SQL queries, data ingested into thr staging area, is transformed and stored in ODS. See screenshot of example SQL code

<img width="837" alt="table transformation ODS schema" src="https://user-images.githubusercontent.com/15156379/169717093-3ca8f66e-e9f1-4ec9-ac49-4609e0532e1f.png">


Entity Relationship Diagram - ERD was drawn on lucid. THis was useful in visualizing the data structures

<img width="943" alt="ER Diagram" src="https://user-images.githubusercontent.com/15156379/169717205-068055b7-4c3a-499b-8cf1-008a2a4eb8b1.png">

Using SQl queries particulaly SQL joins, yelp data was integrated with climate (weather data). For example;

<img width="672" alt="Integrating Yelp and Weather data" src="https://user-images.githubusercontent.com/15156379/169717358-fc0d5509-0d35-411b-8f90-bf7246dd2928.png">

Star schema was also drawn using lucid to understand the data structures and its relationship to facts (total_info) tables and the dimension tables

<img width="1097" alt="star schema" src="https://user-images.githubusercontent.com/15156379/169717298-5c11dc72-9942-4dac-a0c9-e3f6fd936e5b.png">

Also, using SQL queries, data ingested into the ODS was moved into the Data Warehouse DWH for analytics example;

<img width="606" alt="ODS to DWH" src="https://user-images.githubusercontent.com/15156379/169717432-57a61f34-74eb-4c30-8270-169e92e634f5.png">

While in the Data Warehouse (DWH), the cleaned data is ready for analytics. SQL queries was written to report the business name, temperature, precipitation, and rating. This was runned on the CLI

<img width="1113" alt="Query DWH schema" src="https://user-images.githubusercontent.com/15156379/169717517-619bd276-a740-4a8a-9e13-4554febcda94.png">

and the Snowflakes UI example;

<img width="2285" alt="Screenshot 2022-05-22 at 11 12 52" src="https://user-images.githubusercontent.com/15156379/169717587-987a2015-1288-47df-9105-b9cc158b0098.png">

PS: This is by no means, exhaustive. Alot can stil be done....

