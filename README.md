## Map of bird observation/occurrences along riparian corridors in the state of Utah in 2019
**Data for the map is from three sources**

    1. Bird Occurrences - GBIF | Global Biodiversity Information Facility: https://www.gbif.org/ 
    2. State Boundaries - Natural Earth / geojson.xyz
    3. NHD Streams - https://gis.utah.gov/data/water/lakes-rivers-dams/

The data was explored, wrangled and test mapped in Pandas and GeoPandas. ##UPDATE THIS SECTION ON HOW TO USE THE NOTEBOOK

The map itself displays bird occurrences/observations in 2019. Each classified (colored) point represents a sigle observation of 1 of 11 sampled species. The species were selected based on the following criteria. The mean number numbers of observations and the five species most common above the mean and the five most common below the mean. 


 
**Wilson's Warbler - mean observed species**
   
**Five above the mean from largest to smallest:**
        
    1. Bewick's Wren
    2. Vesper Sparrow
    3. Loggerheaded Shrike
    4. Canyon Wren
    5. Northen Pintail
    
 **Five below the mean from largest to smallest**
   
    1. Clarks Nutcracker
    2. Savannah Sparrow
    3. Great Horned Owl
    4. Juniper Titmouse
    5. MacGillivary's Warbler
    
There are two notebooks used for data wrangling and analysis. The first one **bird_occurrences_utah_clean.ipynb** describes the process of cleaning the data downloaded from GBIF with Pandas. Importing the raw CSV, dropping unneeded columns (INSERT cell in notebook describing QGIS process of summarizing of data) and exporting to to geojson.

The second notebook describes a relatively simple analysis where in GeoPandas major streams as classified by the state of Utah are buffered to 300 feet (recommended minimum for avian riparian habitat), dissolved to a single polygon and then used to clip the bird observations. These observations are written to a geojson for use in the resultant interactive map.
