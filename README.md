# Project 5
## Wild Fires in the United States


*By: Tyler Zarnik & Asher Lewis* 

---

## Problem Statement

Congress is in charge of allocating funds to deal with wildfires in the United States. The allocation of these funds is made difficulty to due the unpredictable varying nature of wildfires. To try to contend with this reality Congress has asked our team to predict if wildfires are increasing both in terms of frequency and size. In addition to this Congress wanted us to see if the The Normalized burn ratio is a good index to see the characteristics of wildfires. To this end our team used several time series models scored on RMSE to see if there was in fact an increase.

## Executive Summary

As this was a government problem, the data our team was given was only from government sources.  This was a great hindrance and greatly impacted our results and findings. The data was primarily gathered from two sources: The Monitoring Trends in Burn Severity([MTBS](https://www.mtbs.gov/)) and the National Climatic Data Center ([NOAA](https://www.ncdc.noaa.gov/a)) we used data from starting from the year 2000 and ending in the year 2018.  Unfortunately, as is often the case with government data, there was a tremendous amount of data munging that we had to do in order to get the data usable. After spending an absurd amount of time of getting the data to be readable we combined our weather data and fire data into one CSV with called “fire.csv” .

The next thing that was done on the data was EDA and making maps with the data.  We managed to make an interactive map that was a time-lapse of all the fires occurring in our data. It was at this point that are EDA showed that the NBR data was very unhelpful for the modeling process. This point was furthered by research into NBR which ultimately showed us a similar conclusion. This realization informed our decision of how we would proceed with the modeling.

After trying a DBSCAN model we concluded that our data would not work well with this model, so, we ended up modeling our data with several Time Series models. We realized that most of the features in our data did not serve to help our DBSCAN model  and this was similar situation in our 
Time Series Models. We ending up modeling on the size of fires over  month and the frequency of the wildfires over  a month and we compared wildfires to prescribed fires.

---

## Table of Contents

1. [Loading Packages and Reading Data](#Loading-Packages-and-Reading-Data)
1. [Background Infomation](#Background-Infomation)
1. [Data Dictionary](#Data-Dictionary)
    - [The false promise of the dNBR](#The-false-promise-of-the-dNBR)
1. [Data Cleaning](#Data-Cleaning)
1. [EDA](#EDA)
1. [Model Preparation](#Model-Preparation)
1. [Modeling](#Modeling)
    - [Model 1. Time Series](#Model-1.-Time-Series)
    - [Model 2. Time Series](#Model-2.-Time-Series)
1. [Model evaluation](#Model-evaluation)
1. [Conclusions and Recommendations]([Conclusions-and-Recommendations)
2. [References](#References)


--- 

## Data Dictionary


|Feature|Type|Dataset|Description|
|---|---|---|---|
|fire_id|object|fire.csv| Sequential unique whole numbers that are automatically generated and serve as an ID|
|fire_name|object|fire.csv| Name of fire (UNNAMED if not identifiable from source fire occurrence databases)|
|asmnt_type|object|fire.csv| Fire mapping assessment strategy (Initial (SS) (SS=single scene), Initial, or Extended)|
|fire_type |object|fire.csv|Documented type of fire (WF: Wildfire, Rx: Prescribed Fire; UNK:Unknown)|
|pre_id|object|fire.csv|Landsat or Sentinel scene ID of pre-fire scene|
|post_id|object|fire.csv|Landsat or Sentinel scene ID of post-fire scene|
|nd_t|int64|fire.csv|No data threshold (in dNBR index values)|
|ig_t|int64|fire.csv|Documented type of fire (Increased greenness threshold (in dNBR index values)|
|low_t|int64|fire.csv|Unburned/Low threshold (in dNBR index values; NBR index units for single scene assessments)|
|mod_t| int64|fire.csv|Low/Moderate burn severity threshold (in dNBR index values; NBR index units for single scene assessments)|
|ig_date |datetime|fire.csv|Date of fire ignition (from source fire occurrence databases)|
|lat |float64|fire.csv| Latitude of calculated centroid of the fire perimeter|
|long |float64|fire.csv| Longitude of calculated centroid of the fire perimeter|
|acres |int64|fire.csv|Number of acres mapped|
|state|object|fire.csv| State fire occurred in|
|daily_state_temp|float64|fire.csv|The combined average temperature, in fahrenheit, taken from all weather stations across a state|

## Conclusions and Recommendations

In order for more definitive recommendations to be drawn, Have indexes that are able to more accurately describe and codify fires. Data needs to be collected that captures a longer period of time. Improve objectivity of NBR.

Overall the data does not contain explanatory power or features to tackle the problem statement.However, this project has been thoroughly researched and finished to its conclusion which gives us a strong base to say our conclusions out of knowledge rather than out of ignorance. While our model does preform decently it does not address the overall problem. Even if the data did show an increasing trend as well as considerable multiplicative seasonality, our model with the data captured through exogenous variables is not able to accurately capture or forecast this change. If variables with more objectivity were provided or simply a more fleshed out and devwloped data set by the MTBS was given, we might be able to improve our model. While dbnr is on a larger scale generally from -1000 to 1000, the data is often labeled in only a few common categories.a
  

## References


- Sayad, Y.O.; Mousannif, H.; Al Moatassime, H. Predictive modeling of wildfires: A new dataset and machine learning approach. Fire Saf. J. 2019, 104, 130–146. 

- https://www.mtbs.gov/

- https://www.noaa.gov/

- Mermoz, M.; Kitzberger, T.; Veblen, T.T. Landscape influences on occurrence and spread of wildfires in Patagonian forests and shrublands. Ecology 2005, 86, 2705–2715. [

- San-Miguel-Ayanz, J.; Schulte, E.; Schmuck, G.; Camia, A.; Strobl, P.; Liberta, G.; Giovando, C.; Boca, R.; Sedano, F.; Kempeneers, P.; et al. Comprehensive monitoring of wildfires in Europe: The European Forest Fire Information System (EFFIS). In Approaches to Managing Disaster—Assessing Hazards, Emergencies and Disaster Impacts; Tiefenbacher, J., Ed.; InTech: London, UK, 2012; ISBN 978-953-51-0294-6.

- https://www.kaggle.com/nagarajbhat/australian-bushfire-map-analysis

- SARIMAX **Author**: Mahdi S. (DSI-NYC)_