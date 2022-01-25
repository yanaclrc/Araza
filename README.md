# PlotToMap
Plot-to-map comparison of aboveground biomass workflow - an automated processing chain of AGB plot and map comparison in the context of map validation of AGB map products. The workflow mainly includes preprocessing of forest inventory data and estimating plot-level uncertainties (measurement and allometric model errors, sampling/within-pixel errors, and temporal mismatch with the map year). Preprocessed plot data are also format-ready for calibration/AGB mapping. 

So far, the processing chain can accomodate different kinds of AGB reference data inputs:
1. Plot data (points)
2. Unformatted plot data (default survey format)
3. Polygon data with four corner coordinates (Sustainable Landscape Brazil project (Longo et al., 2016))
4. Tree-level data (Ramesh et al., 2010)
5. Plot data with nested and irregular sub-plots (special case)  
6. Local LiDAR-based AGB maps (One tile from the Sustainable Landscape Brazil project (Longo et al., 2016), wherein raw LIDAR data were processed by Nicolas Labriere)

The most common input is likely #2 and #4

The plot data input will undergo the following preprocessing chain: 
1. Formatting (except for #1)
2. Estimation of SD from Measurement error using BIOMASS package (for #4-5) or using a pre-trained RF model (for #1-3)
3. Estimation of SD from sampling error 
4. Esimation of SD from temporal mismatch error
5. Total of all SD

Map validation is next wherein users should have access of tree cover data (2010) and the AGB map. These inputs are not needed if your purpose is to create calibration-ready plot data.

Plot2Map can also be run in the Multi-Mission Algorithm Platform (MAAP): https://mas.maap-project.org/lauraiduncanson/bio_harmonization

References:
Araza, A. et al. A comprehensive framework for assessing the accuracy and uncertainty of global above-ground biomass maps. Remote Sensing of Environment. In press. 

Dinerstein, E. et al. An Ecoregion-Based Approach to Protecting Half the Terrestrial Realm. Bioscience vol. 67 534–545 (2017)

Longo, M., Keller, M., dos‐Santos, M. N., Leitold, V., Pinagé, E. R., Baccini, A., ... & Morton, D. C. (2016). Aboveground biomass variability across intact and degraded forests in the Brazilian Amazon. Global Biogeochemical Cycles, 30(11), 1639-1660.

Ramesh, B., Venugopal, P.D., P´elissier, R., Patil, S.V., Swaminath, M., Couteron, P., 2010. Mesoscale patterns in the floristic composition of forests in the central western
ghats of karnataka, india. Biotropica 42, 435–443.
