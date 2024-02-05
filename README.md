# Landsat_SST_algorithm

`NLSSTpipeline` produces atmospheric corrected sea surface temperatures (SST) from Landsat thermal infrared
imagery. The atmospheric correction is produced using an NLSST algorithm. We calculate the NLSST algorithm
coefficients using ECMWF ERA5 atmospheric column water vapors at 37 atmospheric levels input into
the MODTRAN radiative transfer model to estimate the relationship between Top of Atmosphere (TOA)
thermal brightness temperatures and sea surface temperatures. We use coincident MODIS water vapor
measurements to correct each Landsat scene using the NLSST algorithm. A cross-calibration is included
for the SSTs using MODIS. To create the cross-calibration we created uncalibrated Landsat SSTs near the
Cosgrove and Dotson ice shelves and used them to matchup with MODIS and produce the calbration in the
LandsatCalibration notebook. 

`LandsatCalibration` calculates the bias and trend for calibration between MODIS and Landsat SSTs.
It creates matchups between MODIS and Landsat for region near Cosgrove and Dotson ice shelves, West Antarctica and uses
an Orthoganal Distance Regresson (ODR) to produce a calibration equation for Landsat, which is then used
to calibrate all SST pixels used for analyses. The current calibration (20230627) is significant to the 90% confidence level (p=0.08). 

`ERADownload` is the code required to download all ERA-5 atmospheric profiles and sea surface temperature
reanalysis data for the training of the MODTRAN atmospheric correction model. `MODTRAN4_prep` prepares
the ERA-5 data for intake for the MODTRAN software run by the MODTRAN C script.

Data includes matchup data (`MODISvLandsat`) that has already been created in `LandsatCalibration`.
Uncalibrated SSTs produced by `NLSSTpipeline` for input into `LandsatCalibration` were too big to include
so the user must run `NLSSTpipeline` first to be able to run `LandsatCalibration`. Data required to generate the
atmospheric correction (`modtran_atmprofiles`) and the output generated by the notebook (`TCWV`) are found
in `Data/AtmCorrection`.

This algorithm was constructed to be used in the virtual cloud and was built using the [CryoCloud](https://cryointhecloud.com) 
cryosphere community JupyterHub ([https://doi.org/10.5281/zenodo.7576601](https://doi.org/10.5281/zenodo.7576602)).

This work is covered under an MIT license.  

Project contact info: \
Tasha Snow, PhD \
Colorado School of Mines \
tsnow@mines.edu
