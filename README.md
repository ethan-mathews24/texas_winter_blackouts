# Identifying the Impacts of the 2021 Winter Storm in Texas


![](images/texasblackout.png)


<p align ="center">
<a href ="https://www.nytimes.com/2011/02/03/us/03storm.html">Texas Blackout</a>
</p>



## Purpose of this Repository 

In February 2021, three severe winter storms swept across the United States, causing a major power crisis in Texas that left millions without electricity during freezing temperatures. As climate change increases the frequency and intensity of extreme weather events, understanding where and how these impacts are felt is increasingly important. This project estimates the number of homes in the Houston metropolitan area that lost power by comparing night light intensity from NASA’s VIIRS (VNP46A1) satellite data before and after the storms. Areas that experienced a significant drop in light were identified as blackout zones. These blackout areas were then spatially joined with OpenStreetMap building data to estimate how many homes were affected.



## Package Dependencies 

* `tidyverse`

* `sf`

* `here`

* `tmap`

* `terra`

* `stars`

* `kableExtra`



## File Structure 

```
EDS223-HWK4
├── data
│   ├── ACS_2019_5YR_TRACT_48_TEXAS.gdb
│   ├── gis_osm_buildings_a_free_1.gpkg
│   ├── gis_osm_roads_free_1.gpkg
│   └── VNP46A1
│       ├── VNP46A1.A2021038.h08v05.001.2021039064328.tif
│       ├── VNP46A1.A2021038.h08v06.001.2021039064329.tif
│       ├── VNP46A1.A2021047.h08v05.001.2021048091106.tif
│       └── VNP46A1.A2021047.h08v06.001.2021048091105.tif
├── images
│   └── texasblackout.png
├── README_files
├── README.html
├── README.md
|── texas_winter_storm.pdf
└── texas_winter_storm.qmd
```



## Repository Contents

The `data` folder contains the data used for this analysis.

The `images` folder contains images that were used for the README and results section.



## Results 

IMAGE GOES HERE



## Data Information/Access

### Night Lights
This analysis uses NASA’s Worldview to explore the data around the day of the storm. There are several days with too much cloud cover to be useful, but 2021-02-07 and 2021-02-16 provide two clear, contrasting images to visualize the extent of the power outage in Texas.

VIIRS data is distributed through NASA’s [Level-1 and Atmospheric Archive & Distribution System Distributed Active Archive Center (LAADS DAAC)](https://ladsweb.modaps.eosdis.nasa.gov/).

To prevent this analysis from being a large data wrangling challenge, we have downloaded and prepped the following files for you to work with, stored in the `VNP46A1` folder.

Data files:

- `VNP46A1.A2021038.h08v05.001.2021039064328.tif`: tile h08v05, collected on 2021-02-07
- `VNP46A1.A2021038.h08v06.001.2021039064329.tif`: tile h08v06, collected on 2021-02-07
- `VNP46A1.A2021047.h08v05.001.2021048091106.tif`: tile h08v05, collected on 2021-02-16
- `VNP46A1.A2021047.h08v06.001.2021048091105.tif`: tile h08v06, collected on 2021-02-16


### Roads
Highways account for a large portion of the night lights observable from space (see Google’s [Earth at Night](https://earth.google.com/web/data=MkEKPwo9CiExMzY2MmI4dER6am1uT1I3RFFnUUxaSlJPbDl5SFF2X3YSFgoUMDAwNjEzMUVFNjJCOTgwOUJCQkQgAUICCABKCAiJ1OmVAhAB)). To minimize falsely identifying areas with reduced traffic as areas without power, we ignored areas near highways.

[OpenStreetMap (OSM)](https://planet.openstreetmap.org/) is a collaborative project which creates publicly available geographic data of the world. Ingesting this data into a database where it can be subsetted and processed is a large undertaking. Fortunately, third party companies redistribute OSM data. We used [Geofabrik’s download sites](https://download.geofabrik.de/) to retrieve a shapefile of all highways in Texas and prepared a Geopackage (`.gpkg` file) containing just the subset of roads that intersect the Houston metropolitan area.

- `gis_osm_roads_free_1.gpkg`


### Houses
We can also obtain building data from OpenStreetMap. We again downloaded from Geofabrick and prepared a GeoPackage containing only houses in the Houston metropolitan area.

- `gis_osm_buildings_a_free_1.gpkg`



## Authors and Contributors

Author: [Ethan Mathews](https://github.com/ethan-mathews24)

Contributor: [Annie Adams](https://github.com/annieradams)



## Data Citations

Geofabrik. (n.d.). US South [OpenStreetMap data extract]. Retrieved November 12, 2026, from https://download.geofabrik.de/north-america/us-south.html
