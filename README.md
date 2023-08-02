# Landsat_SST_algorithm

`NLSSTpipeline` produces atmospheric corrected sea surface temperatures (SST) from Landsat SST. The \
atmospheric correction is produced using an NLSST algorithm. We calculate the NLSST algorithm \
coefficients using ECMWF ERA5 atmospheric column water vapors at ___ atmospheric levels input into \
the MODTRAN radiative transfer model to estimate the relationship between Top of Atmosphere (TOA) \
thermal brightness temperatures and sea surface temperatures. We use coincident MODIS water vapor \
measurements to correct each Landsat scene using the NLSST algorithm. A calibration is included \
for the SSTs using MODIS. To create the calibration we ran the notebook without a calibration \
and used these uncalibrated Landsat SSTs to matchup with MODIS and produce the calbration in the \
LandsatCalibration notebook. 

`LandsatCalibration` calculates the bias and trend for calibration between MODIS and Landsat SSTs. \
It creates matchups between MODIS and Landsat for a region near Cosgrove, West Antarctica and uses \
a RANSAC regression to produce a calibration equation for Landsat, which is then added in the \
NLSST pipeline. The current calibration (20230627) is significant to the 90% confidence level (p=0.08). 

Data includes matchup data (`MODISvLandsat`) that has already been created in `LandsatCalibration`. \
Uncalibrated SSTs produced by `NLSSTpipeline` for input into `LandsatCalibration` were too big to include \
so must run `NLSSTpipeline` first to be able to run `LandsatCalibration`. Data required to generate the \
atmospheric correction (`modtran_atmprofiles`) and the output generated by the notebook (`TCWV`) are found \
in `Data/AtmCorrection`.

This work is covered under an MIT license.

Project contact info:
Tasha Snow, PhD
Colorado School of Mines
tsnow@mines.edu
