# ems-forecasting

This repository is an appendix to the master's thesis. It contains the code that was produced when working with the data.

## Appendix A: Dataset Preparation
The original dataset is available from this link: https://data.cityofnewyork.us/Public-Safety/EMS-Incident-Dispatch-Data/76xm-jjuj

At the time of writing this text in January 2023, the source file has a size of 5.6 GB, which is too large to load it into computer memory for processing. Downsizing is done with “File_Downsize.py”, dividing the file into 10 chunks of 560 MB each.

## Appendix B: Data Preparation
“Data_Preparation.ipynb” loads all the chunks and combines them back together. It selects the desired time frame to keep and handles NaN and wrong values. Columns are formatted. 
Large buildings in Manhattan have their own zip code. Zip code mapping is done to assign those buildings the zip code of the surrounding zip code area they are located in.
Zip codes are aggregated into neighbourhoods. The resulting data frame is exported as “data_part_clean4.csv”

## Appendix C: Modelling and Forecasting
“Final_Code.ipynb” loads “data_part_clean4.csv”. Additional information for dynamic population density is required from the corresponding GitHub repository (https://github.com/citrusvanilla/manhattanpopulationexplorer). A modified version that maps the original zones to the required neighborhoods and zip codes is named "density_reference4.csv". 

Features are extracted from date-time. Columns for hour, weekday and month undergo cyclical encoding. Population density is merged into the data frame. Lag is introduced, lag mean for MEDIC method is built. 
Forecasting is done for all combinations and all models. Each aggregation grouping is individually exported as result file.

## Appendix D: Graphical Data Exploration
"Graphics_Data_Exploration.jpynb" includes all code to create the figures that were used for describing and exploring the dataset and population density.

## Appendix E: Graphical Presentation of Results
"Graphics_Results_Presentation.ipynb" contains the code for all the graphics that were created for presenting the findings of the research.