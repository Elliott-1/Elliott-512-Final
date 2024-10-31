# Elliott-512-Final

# Goal
The goal of this project is to analyze the wildfires of Sioux Falls, SD. Then, with the data processed, to estimate the smoke produced during each fire season and predict the smoke produced over the next 25 years.

# Licensing and Data sourcing

The wildfire data for this project was collected and processed by US Geological Survey. The source data is located at: https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81

I source data about Sioux Falls, SD from the following websites:
FIPS: https://unicede.air-worldwide.com/unicede/unicede_south-dakota_fips_2.html

I also used sample code in my notebookfrom Dr. David McDonald which is licensed through CC-BY, linked here: https://creativecommons.org/licenses/by/4.0/

# Data produced

My notebook creates two files that are used in the visualizations and model building. Unfortunately, they are too large to include. The format for both is:  

1. data/wildfire_processed.csv - This CSV contains a list of wildfires within 1800 miles of Sioux Falls between 1960 and 2021
2. data/AQI_Sioux_Falls_1980_2021.csv - This CSV containins AQI data for Sioux Falls between 1980 and 2021
   
The data schema for these two files are given below with a sample:
wildfire_processed.csv (some columns are omitted)
```python
         OBJECTID  USGS_Assigned_ID Assigned_Fire_Type  Fire_Year  \
0        13526             13526           Wildfire       1961   
1        13527             13527           Wildfire       1961   
2        13528             13528           Wildfire       1961   
3        13529             13529           Wildfire       1961   
4        13530             13530           Wildfire       1961   

      average_distance_from_Sioux_Falls discovery_date prescribed_start  \
0                           1316.727447     1961-09-08              NaN   
1                           1280.780677     1961-07-10              NaN   
2                           1301.192369     1961-09-02              NaN   
3                           1369.776390     1961-07-12              NaN   
4                           1121.604327     1961-09-01              NaN   


      end_date  smoke_impact  
0          NaN  4.979188e-05  
1          NaN  4.183513e-05  
2          NaN  3.159300e-05  
3          NaN  2.736959e-05  
4          NaN  3.386964e-05  


[85496 rows x 41 columns]

```

AQI_Sioux_Falls_1980_2021.csv (some columns are omitted)
```python
            Nitrogen dioxide (NO2)  Sulfur dioxide  PM10 Total 0-10um STP  \
1980-05-03                     NaN             NaN                    NaN   
1980-05-09                     NaN             NaN                    NaN   
1980-05-15                     NaN             NaN                    NaN   
1980-05-21                     NaN             NaN                    NaN   
1980-05-27                     NaN             NaN                    NaN   


            PM2.5 - Local Conditions  Acceptable PM2.5 AQI & Speciation Mass  \
1980-05-03                       NaN                                     NaN   
1980-05-09                       NaN                                     NaN   
1980-05-15                       NaN                                     NaN   
1980-05-21                       NaN                                     NaN   
1980-05-27                       NaN                                     NaN   

...
2021-10-30                                       NaN     18.0  
2021-10-31                                       NaN      7.0  

[4346 rows x 9 columns]
```

# Notebook description:

I currently have four notebooks that are used to generate the results and figures. The two below are used to compile the wildfire data and AQI data respectively:
1. wildfire_data_generator.ipynb
2. EPA_AQI_data_generator.ipynb

The third is used to create the linear regression model that is used to predict the estimated smoke over the next 25 years.

3. smoke_impact_model_building.ipynb

The final notebook is used to create the visualizations for step 2.

4. Visualization_generator.ipynb


