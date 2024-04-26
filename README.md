# MSc_Project

## Data

[NFI_Data]() - Table of plot data for Västra Götaland with biomass (Dw_All_Mg), mean height (MeanHeight), dominant tree type (Class), coordinates (Easting, Northing), and a unique identifier (UniqueID)

LiDAR data available at https://geotorget.lantmateriet.se/geodataprodukter


## Code

Scripts for GEE and python that I used in my MSc project. GEE for data collection, pre-processing, and extraction. Python for training and applying the RF model

This is the order that they were used:

1. [Topo_Data_Prep](https://code.earthengine.google.com/7acdb906d98cd9a32054a4e1df61091e) - Script to prepare a raster of topographic data and export it to an EE asset.

2. [S2_Image_Prep](https://code.earthengine.google.com/bb425c4cdeb47f4c4a6bc7b0da602d54?noload=1) - Script to prepare a raster of S2 data and export it to an EE asset.

3. [S1_Image_Prep](https://code.earthengine.google.com/36e5c5ca990211a2b53b49531ba31705) - Script to prepare a raster of S1 data and export it to an EE asset.

4. [Extraction] - Script to stack rasters and extract values at each plot

5. [RF_training]

6. [RF_Application]


## Other

LAStools available at https://lastools.github.io/
