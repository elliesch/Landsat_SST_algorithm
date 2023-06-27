# Landsat_SST_algorithm

NLSSTpipeline produces atmospheric corrected sea surface temperatures (SST) from Landsat SST. The \
atmospheric correction is produced using an NLSST algorithm. We calculate the NLSST algorithm \
coefficients using ECMWF ERA5 atmospheric column water vapors at ___ atmospheric levels input into \
the MODTRAN radiative transfer model to estimate the relationship between Top of Atmosphere (TOA) \
thermal brightness temperatures and sea surface temperatures. We use coincident MODIS water vapor \
measurements to correct each Landsat scene using the NLSST algorithm. A calibration is included \
for the SSTs using MODIS. To create the calibration we ran the notebook without a calibration \
and used these uncalibrated Landsat SSTs to matchup with MODIS and produce the calbration in the \
LandsatCalibration notebook. 

LandsatCalibration calculates the bias and trend for calibration between MODIS and Landsat SSTs. \
It creates matchups between MODIS and Landsat for a region near Cosgrove, West Antarctica and uses \
a RANSAC regression to produce a calibration equation for Landsat, which is then added in the \
NLSST pipeline. The current calibration (20230627) is significant to the 90% confidence level (p=0.08). 

Data includes sample uncalibrated SSTs produced by NLSST pipeline for input into LandsatCalibration. \
Also includes matchup data (MODISvLandsat) that has already been created in LandsatCalibration.
