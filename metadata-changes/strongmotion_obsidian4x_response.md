# Strong Motion datalogger (Obsidian 4x) response correction

This document provides details of a correction applied to metadata of strong motion stations equipped with an Obsidian 4x datalogger. \
The metadata correction has an impact on downstream strong motion products of those stations (10 sites in total). Products will reflect this change from the date the correction was implemented (February 2021), and we will endeavour to regenerate derived products to account for this.\
We advise all our users to update their former metadata and results to account for this correction.\
This metadata change will likely affect derived products such as Strong motion parameters, magnitudes or localizations.

## Details of the correction applied
The response file used for Obsidian dataloggers was using an overall Gain 4 times lower than expected.\
Former Gain: 4.201680e+05\
Corrected Gain: 1680672\
Unit: Counts/m/s/s\

The correction to our metadata was applied on 17 Feb 2022 (see also https://github.com/GeoNet/delta/pull/1226)

We expect that datasets that have been affect by this are the deconvolved strong motion and strong motion products generated between 2015 and beginning of 2022.

## List of affected sites and time windows
station | streams | start | end | note
--|--|--|--|--
CTZ | HN/BN | 2021.329 (25 Nov) | ---\* | National site strong motion 
DCZ | HN/BN | 2015.295 (10 Oct) | 2021.221 (09 Aug)| National site strong motion  
FOZ | HN/BN | 2017.075 (16 Mar) | ---\* | National site strong motion 
GLWS | HN/BN | 2019.283 (09 Oct) | 2020.205 (07 Jul) | Strong motion station  
KNZ | HN/BN | 2017.151 (30 May) | 2021.153 (02 Jun) | National site strong motion
MSZ | HN/BN | 2017.144 (23 May) | ---\* | National site strong motion
PYZ | HN/BN | 2017.019 (19 jan) | ---\* | National site strong motion 
RIZ | HN/BN | 2016.261 (17 Sep) | ---\* | National site strong motion
SYZ | HN/BN | 2017.142 (22 May) | ---\* | National site strong motion
WAKS | HN/BN | 2019.253 (10 Sep) | 2021.145 (25 May) | Strong motion station 

Note: _* instrumentation remained active as per 21 Feb 2022. This is subject to future equipement change on the field and shall be updated_ 
