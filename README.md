# Elliott-512-Final

# Goal
The goal of this project is to analyze wildfires near Sioux Falls, SD, estimate the smoke produced during each fire season, and predict smoke levels over the next 25 years. Additionally, this project explores the financial impact of wildfires by analyzing historical budget data for wildfire suppression and forecasting future spending trends in relation to smoke production and wildfire acreage.

# Licensing and Data sourcing

The wildfire data for this project was collected and processed by US Geological Survey. The source data is located at: https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81

I used AQI estimates with a tutorial from the following link: https://www.epa.gov/outdoor-air-quality-data/how-aqi-calculated

I source data about Sioux Falls, SD from the following websites:
FIPS: https://unicede.air-worldwide.com/unicede/unicede_south-dakota_fips_2.html

I also used sample code in my notebookfrom Dr. David McDonald which is licensed through CC-BY, linked here: https://creativecommons.org/licenses/by/4.0/

I used CPI data from the following government website: https://www.minneapolisfed.org/about-us/monetary-policy/inflation-calculator/consumer-price-index-1913- . This data is public to use.

I used South Dakota Budget and Wildfire statistics from the following site: https://bfm.sd.gov/ACFR/. This data is public to use. 

# Repo structure
This repo contains three folders.
1. Notebooks: Contains all Jupyter notebooks used to generate data and plots. The ordering order and how to run them is listed in the "Reproducibility section".
2. data: Contains data used in the notebooks. Notably missing is USGS_Wildland_Fire_Combined_Dataset.json which can be downloaded below and wildfire_processed.csv which can either be downloaded at the Google Drive link below or generated using wildfire_data_generator.ipynb.
3. docs: Contains the Part 1 and Part 4 (final) writeups

# Reproducibility

To start, navigate to the notebooks folder: 

Then, run the wildfire_data_generator.ipynb . To run this notebook, you need the file USGS_Wildland_Fire_Combined_Dataset.json file. This is located at: https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81. The output of this notebook will generate a file called "wildfire_processed.csv". The schema is included below:

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
Unfortunately, wildfire_processed.csv is too large to include in the Github. A link is provided to directly download: https://drive.google.com/file/d/1S8wFWi5luMXpHIN3u52sQy1fusFb8DGD/view?usp=sharing

Then run the notebook EPA_AQ_data_generator.ipynb, this notebook requires a EPA AQI API account. Enter in your account details and then run the notebook to collect AQI data. This data is saved as AQI_{city_name}_{start_year}_{end_year}.csv. This file is located in the data folder. The schema looks like: 

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
The third notebook, Visualization_generation.ipynb uses the outputs of the previous two notebooks to generate several figures. These figures were used in my writeups.

The fourth notebook smoke_impact_model_building.ipynb, uses wildfire_processed.csv to predict my computed smoke metric for the next 25 years.

The final notebook Expansion_notebook.ipynb, uses data/wildfire_processed.csv, data/wildfire_budget_information.csv, and data/year_cpi.txt to create models predicting the yearly wildfire suppresion budget using historical and future wildfire data. Also generates relevant figures used in the final writeup.

The schema for wildfire_budget_information.csv:
```python
   Year  Amount spent (in thousands of USD)  \
0  2001                              1890.0   
1  2002                              1692.0   
2  2003                              1300.0   
3  2004                              3500.0   
4  2005                              2800.0   

                                       Link  Page according to PDF  \
0  https://bfm.sd.gov/ACFR/SD_CAFR_2001.PDF                   60.0   
1  https://bfm.sd.gov/ACFR/SD_CAFR_2002.PDF                   75.0   
2  https://bfm.sd.gov/ACFR/SD_CAFR_2003.PDF                   31.0   
3  https://bfm.sd.gov/ACFR/SD_CAFR_2004.PDF                   31.0   
4  https://bfm.sd.gov/ACFR/SD_CAFR_2005.PDF                   32.0   

   Wildfire acreage  
0               NaN  
1           55976.0  
2          116933.0  
3           73585.0  
4            7309.0  
```

The schema for year_cpi.txt:

```python
   Year    CPI
0  2001  177.1
1  2002  179.9
2  2003  184.0
3  2004  188.9
4  2005  195.3
```



