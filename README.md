# Moon Phases & Tides: A Spatial Analysis on Hawaiʻi Island

## Project Summary
This project compares how lunar phases affect high tide height on Hawaiʻi Island and Oʻahu. Using NOAA tide observations for 2023 joined with a moon phase calendar, average high tide heights were calculated for each lunar phase and mapped using GIS methods in R. By visualizing spatial differences between islands, the project highlights how local coastal geography shapes the ocean rhythm described in kilo and Hawaiian lunar knowledge.

## Research Question
How does the effect of lunar phases on high tide height differ between Hawaiʻi Island and Oʻahu?

## Data Description
Tide Observations (NOAA, 2023)
- Hilo Tide Station (NOAA ID: ####)
- Honolulu Tide Station (NOAA ID: ####)
- Hourly tide height values for January–December 2023

Spatial Data
- Hawaiʻi Island and Oʻahu oastline layers
- Source: Hawaiʻi State GIS layers
- Format: shapefile (.shp) / sf object in R

Note on NOAA Refrence Stations:
NOAA identifies Honolulu as the primary reference tide station for Hawaiʻi, with time offsets applied to other locations. In this project, observed tide data for Hilo and Honolulu were used directly to avoid synthetic offset calculations.

## Methods Overview
This workflow was completed in R, using tidyverse, lubridate, sf, and ggplot2.
- Import tide datasets for Hilo & Honolulu
- Clean and format datetime
- Import moon phase calendar
- Join tides with moon phases
- Extract daily high tides
- Calculate average high tide by phase per location
- Convert tide station coordinates to sf
- Join stations to island shapefiles
- Visualize results on a map and bar chart
Code is organized into separate scripts to ensure reproducibility.

