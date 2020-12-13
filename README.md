## Map of bird observation/occurrences along riparian corridors in the state of Utah in 2019
**Data for the map is from three sources**

    1. Bird Occurrences - GBIF | Global Biodiversity Information Facility: https://www.gbif.org/ 
    2. State Boundaries - Natural Earth / geojson.xyz
    3. NHD Streams - https://gis.utah.gov/data/water/lakes-rivers-dams/

The data was explored, wrangled and test mapped in Pandas and GeoPandas. ##UPDATE THIS SECTION ON HOW TO USE THE NOTEBOOK

The map itself displays bird occurrences/observations in 2019. Each classified (colored) point represents a sigle observation of 1 of 11 sampled species. The species were selected based on the follwing criteria. The mean number numbers of observations in the unclipped dataset and the five species most common above the mean and the five most common below the mean. They are as follows:

    1. Wilson's Warbler - mean observed species
# Five above the mean from largest to smallest:
        
    1. Bewick's Wren
    2. Vesper Sparrow
    3. Loggerheaded Shrike
    4. Canyon Wren
    5. Northen Pintail
    
 # Five below the mean from largest to smallest
   
    1. Clarks Nutcracker
    2. Savannah Sparrow
    3. Great Horned Owl
    4. Juniper Titmouse
    5. MacGillivary's Warbler
    
