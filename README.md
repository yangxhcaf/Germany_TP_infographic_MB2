# **Germany Temperature and Precipitation Infographic**
In this repository you will found how to extract temporal temperature and precipitation data using R from monthly datasets like ftp://opendata.dwd.de/. The process from the data download to the plot of the information is described step by step in the sections below. The final result consist in the summary of all graphs generated from the data as an Infographics. Inside [Opendata](ftp://opendata.dwd.de/climate_environment/CDC/grids_germany/) more monthly datasets can be used with this code like [drought_index](ftp://opendata.dwd.de/climate_environment/CDC/grids_germany/monthly/drought_index/) and [sunshine_duration](ftp://opendata.dwd.de/climate_environment/CDC/grids_germany/monthly/sunshine_duration/).

![InfoGraph](https://github.com/ajcastanedag/Germany_TP_infographic_MB2/blob/master/Graph_Sample/InfoGraph.png)

1.**Data Extraction**

In this section and using the script  [1.Data_Extraction](https://github.com/ajcastanedag/Germany_TP_infographic_MB2/blob/master/1.Data_Extraction.R) the information of surface air temperature and precipitation from the webpage will be  downloaded and converted into .csv files. The key points in this code are: First, the directory selection due to the whole folder system for the rest of the code and graphs is created in this step. In line #27 "Main_Fo <- choose.dir()" can be changed for any empty previously created directory. 

Second, the data download section starting on  line #91 will loop over all month folders from the web page and download all .asc.gz files keeping the same structure. In this step the years is obtained so its important to running it each time to assure the Years variable is correctly created. To avoid downloading data over and over, before each download step the existence of each file is checked so the loop can be run many times and  no duplicates will be downloaded, instead, "grid file already exist..." message will be printed.   

Third,  read ASCII-Grid-File step is executed in other big loop. In this step all .asc.gz files are read  and particular modifications are performed such as appliance of coordinate system (EPSG: 31467) and values modifications like Temp/10 accordingly to Description.pdf files found in each dataset. As well, in this step Large RasterStack is created and saved for each month containing all years as layers. 

Finally, a data frame is created and for each month in each year the mean temperature in all Germany is calculated, as well the minimum, maximum and mean value in all months is calculated per year. The data frame structure looks like the following table and its exported as a .csv file. Once the values are calculated the whole procedure is repeated for the precipitation dataset. 

| Year | Jan  | Feb  | ...  | Min  | Mean  | Max   |
| :--: | :--: | :--: | :--: | :--: | :---: | ----- |
| 1881 | -5.4 | 0.1  | ...  | -5.4 | 18.65 | 7.35  |
| 1882 | 0.4  | 1.7  | ...  | 0.43 | 16.78 | 8.39  |
| ...  | ...  | ...  | ...  | ...  |  ...  | ...   |
| 2019 | 0.6  | 3.9  | .... | 0.63 | 19.77 | 10.27 |



2.**Big Circles Plot**



![Mill_Graph](https://github.com/ajcastanedag/Germany_TP_infographic_MB2/blob/master/Graph_Sample/Mill_Graph.png)

3.**Stripes Plot**

![Year_Stripes](https://github.com/ajcastanedag/Germany_TP_infographic_MB2/blob/master/Graph_Sample/Year_Stripes.png)

2.**Bivariate Map**
![Bivariate](https://github.com/ajcastanedag/Germany_TP_infographic_MB2/blob/master/Graph_Sample/Bivariate.png)




