# MSc_Project

Detailed information on methodology can be found in the [report](). 

## Data

Data used in the project:

- [Swedish_NFI_plotdata](swe_nfi_plotdata.xlsx) - Master file, downloaded from: [Swedish University of Agricultural Sciences (SLU)](https://www.slu.se/en/Collaborative-Centres-and-Projects/the-swedish-national-forest-inventory/listor/sample-plot-data/).

- [VG_Plot_Data](VG_Plot_Data.csv) - Cleaned table of plot data for Västra Götaland (VG) with mean height (MeanHeight) and coordinates (Easting, Northing) from the master file, and columns added for total aboveground biomass (Dw_All_Mg), dominant tree type (Class), and a unique identifier (UniqueID).

- [VG_Plots_Shapefile](VG_Plots.shp) - Point shapefile of plot locations in VG.

- [VG_Plots_Buffer](VG_Plots_50m_Buffer.shp) - Shapefile of 50m buffer zones around plot locations to clip rasters to in GEE to minimise storage space and processing time when preparing the training data. Will need to be removed when preparing the final images of the entire region.

- [Plot_Extract_Data+Estimated_MH](Plot_Extract_Data+Estimated_MH.csv) - Table of raster data  extracted for each plot footprint (scripts to prepare rasters and extract data found below). Used to train the Random Forest (RF) model. Include estimated mean height variable for each plot.

- [Global Canopy Height](https://langnico.github.io/globalcanopyheight/) - Produced by Lang et al. Data extracted through GEE.

- LiDAR data available at [Geotorget](https://geotorget.lantmateriet.se/geodataprodukter). Processed data available as EE assets through the extraction script below.


## Code

Scripts for Google Earth Engine (GEE) and python that were used. GEE for data collection, pre-processing, and extraction. Python for training and applying the RF model

This is the order that they were used:

1. [Topo_Data_Prep](https://code.earthengine.google.com/7acdb906d98cd9a32054a4e1df61091e) - GEE script to prepare a raster of topographic data and export it to an EE asset.

2. [S2_Image_Prep](https://code.earthengine.google.com/bb425c4cdeb47f4c4a6bc7b0da602d54?noload=1) - GEE script to prepare a raster of S2 data and export it to an EE asset.

3. [S1_Image_Prep](https://code.earthengine.google.com/36e5c5ca990211a2b53b49531ba31705) - GEE script to prepare a raster of S1 data and export it to an EE asset.

4. [Extraction](https://code.earthengine.google.com/bf49b3ba8421931d774e68169d1115fa?noload=1) - GEE script to stack rasters and extract values at each plot

5. [RF_training](RF_Training+Optimisation.ipynb) - Python script to optimise predictor set and hyperparamters for the RF algorithm. Set up to predict AGB, but can be used to predict MH with small changes to the script.

6.  [Mean_Height_Estimation](https://code.earthengine.google.com/00e81916a63521a63046308bbbc7b3e8) - GEE script to apply the optimised rf for mean height prediction over 10 seeds and then average and export as an EE image for extraction as a predictor (Estimated_MH). This method is faster than doing it in python and uploading.

7. [RF_Application](AGB_Estimation.ipynb) - Python script to apply the optimised RF to the raster of the entire region. Can be used for AGB and MH mapping.

8. [SD_Map+Stats](SD_Map+Stats.ipynb) - Python script to calculate and map standard deviation to represent uncertainty.


## Other

LAStools used to process LiDAR data. Available at https://lastools.github.io/.
