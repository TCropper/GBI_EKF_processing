# GBI_EKF_processing
Contribution to Hanna et al. 2022 GBI Paper

TC contribution to Extended North Atlantic Oscillation and Greenland Blocking indices 1800-2020 from new meteorological reanalysis

The shell script extract_from_EKF400a.sh comprises the CDO and NCO routines to splice together the EKF and ERA5 sea level pressure and geopotentisal height datasets, outputting global netcdf files and specific csv files for the regions/stations of interest.

The paths are hardcoded so would need changing to replicate, and assumes the downloading of the entire EKFV2 ensemble and ERA5 monthly SLP and GPH data (with the files named as near the top of the shell script, ERA5 can be downloaded from C3S).

The R script gbi_eof.R performs the EOF analysis to generate the NAO timeseries. 

Both designed to run in naive parallel, e.g. 

parallel -j 4 Rscript gbi_eof.R ::: {1..30}

where 1-30 are the EKF ensemble members, although serially for both scripts shouldn't take too long (hours)
