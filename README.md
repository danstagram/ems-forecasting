# ems-forecasting

This repository is an appendix to the master's thesis. It contains the code that was used in the preparation and analysis of the data.

The original dataset is available from this link: https://data.cityofnewyork.us/Public-Safety/EMS-Incident-Dispatch-Data/76xm-jjuj

At the time of writing this text in January 2023, the source file has a size of 5.6 GB, which might be too large for computer memory. Downsizing is done with “File_Downsize.py”, dividing the file into 10 chunks of 560 MB each.

“Data_Preparation2.ipynb” loads all the chunks and combines them back together. It selects the desired time frame to keep and handles NaN and wrong values. Columns are formatted. 
Large buildings in Manhattan have their own zip code. Zip code mapping is done to assign those buildings the zip code of the surrounding zip code area they are located in.
Zip codes are aggregated into neighbourhoods. The resulting data frame is exported as “data_part_clean4.csv”

“Final_Code10.ipynb” loads “data_part_clean4.csv”. Additional information for dynamic population density is loaded from their GitHub repository (https://github.com/citrusvanilla/manhattanpopulationexplorer). Features are extracted from date-time. Columns for hour, weekday and month undergo cyclical encoding. Population density is merged into the data frame. Lag is introduced, lag mean for MEDIC method is built. 
Forecasting is done for all combinations and all models. Each aggregation grouping is individually exported as result file.
