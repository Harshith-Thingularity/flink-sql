# flink-sql
## Prerequisites

   - Docker installed
   - Docker Compose installed
   - make installed
   - bash or similar terminal
   - Internet connection to download dependencies
##  Navigate to the project directory
```
cd ~/Downloads/tooling-library-main/projects
```
## Start the Flink SQL Client Project
First, move into the flink-sql-client directory
```
cd flink-sql-client
```
## build and start the services using Docker Compose
```
sudo docker-compose up --build -d
```
## Download Required Dependencies
```
./get_deps.sh
```
This script downloads Flink connectors, AWS SDKs, and other dependencies into the jars/ folder.
## Build and Run Flink SQL Client
```
sudo make all
```
You will see the Flink SQL CLI startup screen

## creation of random fake data using datagen connector
```
CREATE TABLE fake_table (
    id INT,                 
    name STRING,
    age INT,
    status STRING
) WITH (
    'connector' = 'datagen',
    'rows-per-second' = '1',   
    'fields.id.min' = '1',
    'fields.id.max' = '1000',
    'fields.name.length' = '10',
    'fields.age.min' = '18',
    'fields.age.max' = '80',
    'fields.status.length' = '7'
);
```
Random data is generarated. One rwo is generated each second in this case 
## query of the data 
```
SELECT * FROM fake_table;
```
This will generate the data with random values for the specified fields (id, name, age, status)

## To Stop docker services
```
sudo docker-compose up --build -d
```

