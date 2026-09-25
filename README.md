# 🚲 NYC Citi Bike Data Analysis

## 📊 Dataset

This project analyzes NYC Citi Bike trip data along with station information and historical weather data.

The raw and processed datasets are **not included in this GitHub repository** because the trip data is large. Users can download the required datasets from the original data sources and place them in the project `data/` directory.

---

## 📁 Data Folder Structure

```text
data/
│
├── raw/
│   └── Citi Bike monthly trip CSV files
│
├── processed/
│   └── Cleaned and transformed trip data
│
└── external/
    ├── station_information.csv
    └── nyc_weather.csv
```

---

## 🚲 1. Citi Bike Trip Data

The main dataset contains historical Citi Bike trip records.

### Raw CSV files

The raw files contain trip-level information collected from Citi Bike's historical trip-data system.

Depending on the period, the schema can contain fields such as:

| Column               | Description                  |
| -------------------- | ---------------------------- |
| `ride_id`            | Unique identifier for a ride |
| `rideable_type`      | Type of bike used            |
| `started_at`         | Trip start timestamp         |
| `ended_at`           | Trip end timestamp           |
| `start_station_name` | Starting station name        |
| `start_station_id`   | Starting station ID          |
| `end_station_name`   | Ending station name          |
| `end_station_id`     | Ending station ID            |
| `start_lat`          | Starting latitude            |
| `start_lng`          | Starting longitude           |
| `end_lat`            | Ending latitude              |
| `end_lng`            | Ending longitude             |
| `member_casual`      | User type: member or casual  |

> **Note:** Citi Bike's historical data schema has changed over time. The cleaning process standardizes the available fields before analysis.

---

## 🧹 2. Processed Trip Data

The processed dataset is created after cleaning the raw trip files.

The cleaning process includes operations such as:

* Standardizing column names
* Converting timestamps
* Calculating trip duration
* Removing invalid trip records
* Removing duplicate ride IDs
* Cleaning station information
* Creating additional analytical features

Example derived fields include:

| Feature             | Description                             |
| ------------------- | --------------------------------------- |
| `trip_duration_min` | Trip duration in minutes                |
| `date_hour`         | Trip start time rounded to the hour     |
| `hour`              | Hour of the day                         |
| `day_of_week`       | Day of the week                         |
| `month`             | Month of the trip                       |
| `is_weekend`        | Weekend indicator                       |
| `trip_distance_km`  | Approximate trip distance in kilometers |

---

## 📍 3. Station Information

The station dataset contains information about Citi Bike stations.

### File

```text
data/external/station_information.csv
```

It is used to provide station-level information such as:

* Station ID
* Station name
* Latitude
* Longitude
* Station capacity

Station information is used during feature engineering and station-level analysis.

---

## 🌦️ 4. Weather Data

Historical NYC weather data is stored separately from the trip data.

### File

```text
data/external/nyc_weather.csv
```

The weather dataset contains hourly weather observations used for analyzing relationships between weather conditions and Citi Bike usage.

Example variables include:

| Column                 | Description                     |
| ---------------------- | ------------------------------- |
| `date_hour`            | Hour of the weather observation |
| `temperature_2m`       | Temperature                     |
| `precipitation`        | Precipitation                   |
| `wind_speed_10m`       | Wind speed                      |
| `relative_humidity_2m` | Relative humidity               |

The weather data is joined with trip data using the hourly timestamp.

---

## 🔗 Data Sources

### Citi Bike Trip Data

Official Citi Bike historical trip data:

https://citibikenyc.com/system-data

### Citi Bike Station Information

Official Citi Bike GBFS station information:

https://gbfs.citibikenyc.com/gbfs/en/station_information.json

### Historical Weather

Open-Meteo historical weather data:

https://archive-api.open-meteo.com/v1/archive

---

## 📥 Where to Put the Data

After downloading the datasets, place them in the following locations:

```text
data/
├── raw/
│   └── monthly Citi Bike trip CSV files
│
├── processed/
│   └── cleaned datasets
│
└── external/
    ├── station_information.csv
    └── nyc_weather.csv
```

The `data/` directory is excluded from GitHub because the datasets are large.

---

## ⚠️ Dataset Notes

The Citi Bike dataset is large and contains millions of trip records. Processing the complete historical dataset can require substantial memory and storage.

The project therefore keeps the raw and processed datasets locally rather than storing them directly in this GitHub repository.

The notebooks in this repository contain the code required to collect, clean, transform, and analyze the data.
