
The Feature Database generation consists of two steps: 

| Notebook      | Source        | Description |
| ------------- | ------------- | ----------- |
| [Make Labels](featureDB_make_labels.ipynb)   | [Github](https://github.com/SpatioTemporal/featureDB/blob/main/make_labels.ipynb) | Loads the precipitation values from IMERG data and clears all the values below a given threshold. Then, it runs a Connected Components algorithm to find the connected areas of precipitation and label them. Finally, it stores the results in pickle format. The results are all the labels or the most significant 20 or 100 labels. |
| [Make DF](featureDB_make_df.ipynb) |  [Github](https://github.com/SpatioTemporal/featureDB/blob/main/make_df.ipynb)  | The second step in generating the feature database is to load the labels from the first notebook and convert them into STARE data frames. It creates STARE trixles and daily aggregates for the data. Then, it writes them in GeoPackge database format.|

Subsetting notebooks:

| Notebook      | Source        | Description |
| ------------- | ------------- | ----------- |
| [POMD-PF](POMD-PF.AIST.10202022.ipynb)   |  | This notebook compares actual Satellite data with simulated results from a computer model. It starts by reading IMERG satellite data and GEOS5 model data. Then, it subsets the data by keeping the most significant rain values and ignoring unimportant ones, such as those in small or low rain areas. It draws many graphs that compare the actual and simulated data.|
| [IMERG Analyze](999-H0-00-IMERG-Analyze-1.ipynb)  | [Github](https://github.com/SpatioTemporal/STARE-Cookbooks/blob/develop/contrib/jupyter/999-H0-00-IMERG-Analyze-1.ipynb) | (Unlike the POMD-PF example, which subsets the rain values based on the significance of the data, this notebook is an example of geographic region subsetting.) The notebook reads US states geographical data and converts them into STARE trixels. Then, it selects only the geographic region corresponding to one US state (Virginia). It proceeds by selecting features (from the feature database created with make_labels and make_df as described above) in this area of interest. Furthermore, it chooses one event from the labeled events. This rainy event has a temporal and spatial extent. The notebook calculates some helpful values, such as the duration of the event and the total precipitation. It shows a graph with the spatial extent of the event beyond the area of interest (Virginia).  |
