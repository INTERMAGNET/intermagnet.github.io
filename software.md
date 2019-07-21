---
title: Software
---

<div class="alert alert-info" role="alert">
INTERMAGNET does not endorse or recommend any of the non-INTERMAGNET software. These applications are here to help the community find tools that might be useful to them.
</div>

#  Data processing

## [MagPY](https://github.com/geomagpy/magpy)

MagPy (or GeomagPy) is a Python package for analysing and displaying geomagnetic data. MagPy provides tools for geomagnetic data analysis with special focus on typical data processing routines in observatories. MagPy provides methods for data format conversion, plotting and mathematical procedures with specifically geomagnetic analysis routines such as basevalue and baseline calculation and database handling. Among the supported data formats are ImagCDF, IAGA-02, WDC, IMF, IAF, BLV, and many more. Full installation also provides a graphical user interface, xmagpy.

## [ObsMat](https://gitext.gfz-potsdam.de/mors/OBS_MAT)

ObsMat is a collection of MATLAB routines to analyze, calibrate, display and check geomagnetic data. Internally, data are stored in a custom cdf file format that includes all information to produce definitive data. An interactive tool for flagging and displaying geomagnetic data, called varlab, is part of the package.

## [MagPySV](https://github.com/gracecox/MagPySV)

Python toolbox for geomagnetic data processing particularly related to SV work.

## [Kasm](http://magneto.igf.edu.pl/soft/kasm/)

Program Kasm is designed for calculation of geomagnetic activity indices K according to the Adaptative Smoothed method.

# Visualization

## [Imcdview](ftp://ftp.nmh.ac.uk/INTERMAGNET/software/CDViewer/)

Imcdview is an application for working with the CDs and DVDs of 1-minute definitive data that INTERMAGNET has published annually since 1991. The programme is compiled and will run on Microsoft Windows, SOLARIS, Linux and OS X (source code is not included). The program allows you to view minute, hourly and daily mean data and to scroll rapidly through data sets, and also to view quality control information such as comparison of instruments at an observatory, comparison of data between nearby observatories and plots of the 'baseline' at an observatory - an important indicator of the quality of measurements. Metdata such as observatory location and contact details for institutes is also available.

Imcdview works with the INTERMAGNET Archive Format (IAF) and requires data to be in the structure defined for the INTERMAGNET CD/DVD. One module in the programme allows import of data from other formats (such as IAGA-2002) into the IAF format. Another module provides options to export the data in a number of geomagnetic data formats. Caution should be used when working with these import and export facilities - data will always be limited to the precision of the IAF format, which is particularly low for angles (declination).

## [Autoplot](http://autoplot.org/)

Autoplot is a general purpose plotting package which can be used to view data in INTERMAGNET's CDF format (ImagCDF) as well as a number of other formats. It is able to handle large volumes of time series data efficiently and provides spectral as well as time series plots.

Autoplot was developed under the NASA Virtual Observatories for Heliophysics program in a collaborative effort among several institutions, including support or code contributions from ViRBO, VMO, RBSP-ECT, and the Radio and Plasma Wave Group at The University of Iowa.

# I/O and format conversion

## [INTERMAGNET GitHub](https://github.com/INTERMAGNET)

A collection of source code including routines in Python, Mathematica, Matlab, IDL and Java for reading and writing the INTERMAGNET CDF format ImagCDF. This repository is open for other source code that would be useful to the community and we encourage contributions.

## [Gm_convert](ftp://ftp.nmh.ac.uk/INTERMAGNET/software/gm_convert/)

This software allows you to convert between a number of geomagnetic formats. The program can read the following formats: WDC; INTERMAGNET Minute Mean Format; IAGA-2002; INTERMAGENT Archive Format; INTERAMGNET-CDF; INTERMAGNET-DKA. It converts to either INTERMAGNET Archive Format, IAGA-2002 or INTERAMGNET-CDF. The program can convert from large numbers of input files in multiple formats. It is designed so that, once the necessary information has been collected from the user, the conversion will take place without requiring further input, meaning that long conversion tasks can run unattended.

# Checking

## [DataCheck1S](ftp://ftp.nmh.ac.uk/INTERMAGNET/software/DataCheck1s/)

DataCheck1s is primarily intended for INTERMAGNET members who are tasked with quality checking INTERMAGNET 1-second data. The programme compares 1-second data in IAGA-2002 format to 1-minute data from the same observatory / time range in IAF format. It also converts data from IAGA-2002 to the new INTERMAGNET CDF format (ImagCDF) and provides some simple plotting abilities.

## [check1min](http://magneto.igf.edu.pl/soft/check1min/)

Software to check INTERMAGNET 1 minute definitive data, as described in the INTERMAGNET technical manual (ver 5).

# Data acquisition

## [GeomagLogger](https://gitext.gfz-potsdam.de/mors/GeomagLogger/)

A C++ software package for logging data at geomagnetic observatories.



