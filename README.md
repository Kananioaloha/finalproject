# Moon Phases & Tides: A Spatial Analysis on Hawaiʻi Island

## Project Summary
This project explores how lunar cycles shape tides at Hilo Bayfront on Hawaiʻi Island. Using NOAA tide observations for 2023 from the Hilo tide station (1617760), the dashboard visualizes daily maximum tides across the year, zooms into August 2023 to highlight supermoon-driven “big up, big down” tides, and compares predicted versus observed tides for January 2023. A synthetic 2024 dataset is also used to show an idealized relationship between lunar illumination and mean low tide. Together, these views help connect kilo of Hilo tides to lunar phases, coastal access, fishing, diving, and daily life in Hawaiʻi.

## Research Question
How does the effect of lunar phases on high tide height differ between Hawaiʻi Island and Oʻahu?
How do lunar phases and lunar illumination influence daily tide patterns at Hilo Bay, Hawaiʻi (NOAA Station 1617760)?



## Data Description
# Tide Observations (NOAA, 2023)
Hilo Tide Station – NOAA ID 1617760
Location: Hilo Bayfront, Hawaiʻi Island
Time span: January–December 2023
Resolution: 6-minute tide height values (ft, MLLW), including predicted and observed tides
## Files used in the dashboard
- data_clean/hilo_tides_2023_clean_1.csv
   - Cleaned 2023 Hilo tide data (parsed datetime, selected columns)
- data_clean/hilo_tides_2023_daily_summary_1.csv
   - Daily summary for 2023 (max, min, mean tide height per day)
- data_raw/hilo_tides_2023_01_raw_copy.csv
   - Raw predicted vs observed tide heights for January 2023
- data_raw/hilo_tides_2023_08_raw_copy.csv
   - Raw tide data for August 2023 (used for focusing on supermoon tides)
## Moon Phase & Lunar Illumination Data
# Moon phase calendar (2023)
- Visual calendars included as images:
   - media/hinaicopy.png
   - media/mahoecopy.png
- Used to visually align full and new moon dates with August 2023 tide peaks.
# Lunar illumination (2000–2024)
- Computed in R with the suncalc package (getMoonIllumination()).
- Daily fraction of the moon illuminated (%).
- Initially calculated for 2000–2024, then summarized and visualized with a focus on 2024.
## Synthetic Tide Data (2024 Visualization Only)
- Generated in R (not downloaded from NOAA).
- Daily mean low tide values for 2024 created using:
  - A ~14-day spring–neap cycle
  - A yearly seasonal oscillation
  - Small random “environmental noise”
- Lunar illumination for 2024 is added to the same dataframe and rescaled to show:
  - Tide (primary y-axis)
  - Illumination (%) (secondary y-axis)
- Purpose: to provide a clear, “textbook-style” example of how lunar illumination and tide cycles are linked. This dataset is for visualization only and does not represent real measured tide heights.
## Spatial Context
- The dashboard uses leaflet to map the Hilo tide station:
  - Coordinates: 19.7297° N, 155.06° W
  - Basemap from OpenStreetMap tiles
- A single leaflet marker shows the location of NOAA Station 1617760 at Hilo Bayfront.
## Note on NOAA Reference Stations
NOAA identifies Honolulu as the primary reference tide station for Hawaiʻi, with time offsets applied to many secondary locations. In this dashboard, we use observed and predicted data provided directly for Hilo Station 1617760, rather than applying Honolulu-based offsets. This keeps the analysis grounded in the real conditions experienced specifically at Hilo Bayfront.

## Methods Overview
This workflow was completed in R, using tidyverse, lubridate, plotly, leaflet, ggplot2, and suncalc.
- Import cleaned tide data for Hilo (2023) and daily summary data.
- Plot daily maximum tide height for all of 2023 and convert it to an interactive plot with ggplotly() so viewers can hover and zoom.
- Filter the daily summary to August 2023 and plot daily maximum tides to highlight the supermoon + full/new moon period, using the moon phase calendar images as visual reference.
- Map the Hilo tide station using leaflet() with a marker on the basemap to provide spatial context.
- Import January 2023 raw tide data and create a two-line comparison plot of predicted vs observed tide heights, styled for clarity and converted to an interactive ggplotly() graph.
- Use suncalc::getMoonIllumination() to compute daily lunar illumination (2000–2024), then visualize the long-term pattern and focus on 2024 as a single-year example.
- Generate a synthetic 2024 daily mean low tide series (spring–neap + seasonal + noise), join it with lunar illumination, and build a dual-axis plot showing tide and illumination together.
- Use consistent themes, labels, and titles so each plot clearly communicates how lunar cycles and tides connect at Hilo Bayfront.

Code is organized into clearly labeled chunks inside a single Quarto dashboard file to keep the workflow reproducible and easy to follow from data import to final visualizations.

