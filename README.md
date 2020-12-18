## Map of bird observation/occurrences along riparian corridors in the state of Utah in 2019
### Data for the map is from three sources

    1. https://www.gbif.org/ "Bird Occurrences - GBIF | Global Biodiversity Information Facility"
    2. State Boundaries - Natural Earth / geojson.xyz
    3. NHD Streams - https://gis.utah.gov/data/water/lakes-rivers-dams/

The data was explored, wrangled and test mapped in Pandas and GeoPandas using Jupyter Notebooks. There are four notebooks in total:

### bird_occurrences_utah_clean.ipynb 
This notebook goes through initial process of cleaning raw data downloaded from Global Biodiversity Information Facility. It imports python libraries matplotlib, pandas and numpy. Initially reading in the raw csv data, inspecting it removing unecessary columns and selecting a subset of species. The subset of species analysis was done in QGIS - where each number of species were summed in a summary table and basic stattistics were run. With these results a new csv file written that will be manipulated further in the next notebook.

### bird_occurrences_utah_explore.ipynb
This notebook explores the spatial side of our initial csv data plus NHD streams and United States boundaries. We import the same libraries as the first notebook with the addition of shapely and GeoPandas. We read and convert each input dataset as GeoPandas Dataframes. The United States Data is inspected and extracted as a geoseries of Utah, then written to geoJSON. 

Next the NHD streams data is inspected for crs and plotted. It's apparent that we have way too much data for the purpose of this map. Using a conditional statement we pullout only the major streams. Plotting them again we can see that the density is much reduced. This file is then written to GeoJSON.

Finally, we read in the csv created in notebook **bird_occurrences_utah_clean.ipynb**. The data isn't interpreting the geometry column correctly. So we need to convert our lat/lon columns to integer and use the gpd_pointsfrom_xy() method to make sure the coumns are being read correctly. The birds are then plotted for visual inspection and finally written to a geoJSON file.

### Map Description
The map itself displays bird occurrences/observations in 2019. Each classified (colored) point represents a sigle observation of 1 of 11 sampled species. The species were selected based on the following criteria. The mean number numbers of observations and the five species most common above the mean and the five most common below the mean. 
 
**Wilson's Warbler - mean observed species**
   
**Five above the mean from largest to smallest:**
        
    1. Bewick's Wren
    2. Vesper Sparrow
    3. Loggerheaded Shrike
    4. Canyon Wren
    5. Northen Pintail
    
 **Five below the mean from largest to smallest:**
   
    1. Clarks Nutcracker
    2. Savannah Sparrow
    3. Great Horned Owl
    4. Juniper Titmouse
    5. MacGillivary's Warbler
    
There are two notebooks used for data wrangling and analysis. The first one **bird_occurrences_utah_clean.ipynb** describes the process of cleaning the data downloaded from GBIF with Pandas. Importing the raw CSV, dropping unneeded columns (INSERT cell in notebook describing QGIS process of summarizing of data) and exporting to to geojson.

The second notebook **bird_occurrences_utah_explore_stream_buffers_intersect.ipynb** describes a relatively simple analysis where in GeoPandas major streams as classified by the state of Utah are buffered to 300 feet (recommended minimum for avian riparian habitat), dissolved to a single polygon and then used to clip the bird observations. These observations are written to a geojson for use in the resultant interactive map.
