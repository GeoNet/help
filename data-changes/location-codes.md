# Location codes change

This document provides details of **Data/Metadata Legacy corrections** we have applied to correctly label the **location code** of **strong motion instruments** part of the GeoNet national network for periods of time between **2011 and 2020**.
The change was applied to **data and metadata** from **27 seismic stations**  (in between June and October 2021) 

You might be impacted by this change if you:
- have a local copy of our data and/or metadata that is not up to date Prior to June/Oct 2021 ;
- are using our data and metadata services while we apply the change Prior up to Oct 2021;
- are using a derived data product that has a mismatch in the metadata (e.g. seismic pick label on a strong motion)


## Background
Location codes naming conventions used for GeoNet seismic stations are documented [on our _delta_ metadata repository](https://github.com/GeoNet/delta/tree/main/docs).
Based on this nomenclature convention:
- all strong motion sensors have a location code `2?`;
- when a sensor is moved more than 1 m (but less than 200m), its location code will change accordingly (e.g. from `20` to `21`).

This convention aligns with [naming requirements for Seismohraph Stations](http://www.isc.ac.uk/registries/registration/) established by the International Seismological Centre (ISC).

For GeoNet seismic sensors, the convention was established in September 2019.

### Change description
After the convention was confirmed, we conducted an audit on all equipment changes across the GeoNet National Strong motion sensor network. We found that a number of SM sensors were moved to a new location, without having their location code changed accordingly.

We are now retroactively correcting our data archive and our metadata records, so that this change is properly represented.

For those SM stations, location codes that were previously recorded as `20` are now being changed to `21`.

Due to the complexity of this work, there has been for a period of time a mismatch between the metadata (that were correctly reporting 21) and the data in the archive. This has now been fixed.

### Affected data

Data and metadata that are affected by this change are:
- strong motion metadata (distributed via delta, FDSN)
- strong motion miniseed data (distributed via FDSN)
- strong motion processed data (distributed via the Strong Motion Tool and archive)
- seismic data picks ID and magnitude ID (distributed via FDSN) might have metadata not correctly associated

If you use strong motion miniseed data and metadata, you might be impacted by this change. The impact we expect can be of two forms:
- if you have used and downloaded data between 2019 and 2021, you might have not been able to retrieve the complete dataset from FDSN
- if you have a local copy of our data, things might not match anymore with our GeoNet archive
- derived products we distribute and were not able to be reprocessed might still refer to old location code. For example, quakeML might still show that a station had location code 20, but then miniseed data will have that station with a location code 21


## Details of the change
Here, we endeavour to provide enough details so that you can have a quick overview of the changes, and decide if those are affecting you. 
If you need further details or help please [contact us](https://www.geonet.org.nz/contact) or open an issue in this repository.

The table below provides a list of station and location codes that are affected, and for which time period data and/or metadata were corrected.
For data in the past, we tried to apply the change to data and metadata at the same time to minimise impact on the user while still allowing access to the waveforms. 

Listed below, only the stations for which a significant time range were changed. If the change was only affecting a few days, we are not reporting it here.

All data and metadata listed below have had their location code changed from `20` to `21`

The table shows: 
- _station_ identifier
- time range for which data have been corrected (_start_ and _end_, `year.doy`) 
- time _when_ change was applied
- a _note_ if other changes were also applied for the same time period

station | start | end | when | note
--|--|--|--|--
DSZ | 2016.314 | 2019.318 | Jun 2021 |
HAZ | 2018.011 | 2019.305 | Oct 2021 |
JCZ | 2018.331 | 2020.015 | TODO |
LBZ | 2014.275 | 2020.014 | TODO |
LTZ | 2013.296 | 2019.304 | Oct 2021 |
MLZ | 2014.084 | 2019.304 | Oct 2021 | [components name](component-names.md) 
MQZ | 2016.055 | 2019.305 | Oct 2021 | 
MRZ | 2011.103 | 2019.304 | Oct 2021 |
MWDS | 2016.054 | 2019.176 | Jun 2021 |
MWZ | 2011.231 | 2019.304 | Sep 2021 |
MXZ | 2011.230 | 2019.305 | Oct 2021 |
NNZ | 2012.005 | 2019.304 | TODO |
ODZ | 2017.179 | 2019.305 | Oct 2021 |
OPZ | 2017.177 | 2019.304 | Jun 2021 |
OUZ | 2017.053 | 2019.305 | Oct 2021 |
OXZ | 2014.303 | 2020.015 | TODO |
PUZ | 2013.218 | 2019.325 | Oct 2021 |
QRZ | 2015.315 | 2019.325 | TODO |
THZ | 2014.093 | 2020.014 | TODO |
TLZ | 2016.043 | 2020.015 | Jun 2021 |
TMHS | 2017.201 | 2019.015 | May 2021 |
TOZ | 2016.014 | 2019.325 | TODO |
TSZ | 2013.183 | 2019.325 | TODO |
TUZ | 2015.300 | 2020.014 | TODO |
VRZ | 2014.078 | 2020.014 | TODO | [components name](component-names.md)
WCZ | 2017.053 | 2020.015 | TODO |
WHZ | 2014.156 | 2020.014 | TODO |
WKZ | 2017.179 | 2019.304 | Jul 2021 |
WVZ | 2014.156 | 2020.014 | TODO |

