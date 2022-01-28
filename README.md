# PyBer Analysis

## Overview

Management asked to analyze ride data and city data to analyze how the rides in each city differentiated according to several metrics, including the type of city (Urban, Suburban and Rural), the number of drivers, the average number of rides and the average number of fares.

For this final assingment a summary DataFrame of the ride-sharing data by city type was created and, using Pandas and Matplotlib, a multiple-line graph that shows the total weekly fares for each city type.


### Resources
- Data source: The audit was performed on the files "city_data.csv" and "ride_data.csv" provided by PyBer management. The following images show the structure of the files.

    |**city_data.csv**                               |**ride_data_csv**                               |
    |:----------------------------------------------:|:----------------------------------------------:|
    |![city_data_file](/Resources/city_data_file.png)|![ride_data_file](/Resources/ride_data_file.png)|


- Software use to perform the analysis: Python 3.7.11, Anacoda 4.11, Jupyter Notebook 6.4.6

## Results

### Data by city type

#### Big picture

- The merged dataframe from the city data and ride data files shows the following statistics for 'fare', 'ride_id' and 'driver_count' variables.

    ![merged_dataframe](/Resources/pyber_data_df.png)

- Taking into consideration that this statistical summary includes all cities information, we get the following:
    - ***Ride_id:*** This number is not relevant for analysis as it refers to an id control number for each ride.
    - ***Fares:*** The range is pretty wide from $4.05 to $58.55, mean of $26.75 and a pretty large SD of $12.11.
    - ***Driver_count:*** There are cities with only one driver and cities with up to 73 drivers, making this also a wide range. The mean rider count per city is 29.
    
#### Per city type

- From the merged dataframe, we calculated metrics per city type ('Rural', 'Suburban', 'Urban') using the *groupby()* operation which involves some combination of splitting the object, applying a function, and combining the results.
    
    Example: Get the total rides for each city type 
    ```python
    city_rides_count = pyber_data_df.groupby(["type"]).count()["ride_id"]
    city_rides_count
    ```
    
- Finally, we obtained a summary dataframe with the calculations per city type. 

    ![summary_dataframe](/Resources/pyber_summary.png)

- Results:
    - Urban cities have 31 and 5 times more drivers than Suburban and Rural cities, respectively.
    - Urban cities have 2.6 and 13 times more drivers than Suburban and Rural cities, respectively.
    - Average fares per ride are greater in Rural and Suburban cities ($34.62 and $30.97) than that in Urban cities.
    - In the same token, Rural average fares per driver are 1.4 and 3.3 times greater than Suburban and Urban average fares, respectively.
    - The combination of number of rides and fares for each type of city, show that Urban cities have 62.7% ($39,584.38) of total fares, followed by Suburban with 30.5% ($19,356.33) and Rural with 6.8% ($4,327.93). 
    
        ![total_fares_distribution](/Resources/pie_total_fares.png)

    - Finally, we obtained the plot for total fares by city for weeks between dates 01-01-2019 to 04-29-2019. This graph shows the same results, over time, of how  Urban cities have the most income over Suburban and Rural cities.
    
        ![total_fares_series](/analysis/PyBer_fare_summary.png)

    - We can deduce from the statistics for this period, that all cities have their fares within a reasonable "stable" amount, although all three city types present a peak in the last week of February.  Also Urban cities remain above average during April.

        |Stat   | Rural |Suburban|Urban  |
        |:------|------:|-------:|------:|
        |mean   |230.22 |1051.96 |2180.34|
        |std    |113.52 |186.17  |213.69 |
        |min    |67.65  |721.60  |1661.68|
        |max    |501.24 |1412.74 |2470.93|


## Summary

Based on the results, we've seen that there are evident differences between city types.

   - There only 18 Rural cities, compared to Urban (66) and Suburban (36). Therefore, there should be a campaign to reach out more Urban cities.
   - In order to increase the number of rides in Rural and Suburban cities, the number of riders needs to increase.  If we look at the number of drivers per city type, Rural have an average of only 4.3 drivers per city, 13.6 per Suburban city and 36.4 drivers per Urban City.
   - Regarding fares, Rural and Suburban drivers show a higher fare than Urban cities, probably because of two factors: distances may be larger, and supply is more limited (less competition). There should be an analysis regarding trip duration to determine the most important factor.
