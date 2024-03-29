# Location codes change

This document provides details of a number of corrections applied to miniseed data and associated metadata between June and October 2021. 
Those have been applied to correctly label the location code of strong motion (SM) instruments part of the GeoNet national network for instrument changes that occurred between 2011 and 2020. The change was applied to both data and metadata from 27 seismic stations. 

You might be impacted by this change if you:
- have a local copy of our data and/or metadata that is not up to date;
- are using a derived data product that may present a mismatch with the metadata (e.g. seismic pick label on a strong motion derived dataset)

This type of archive change will still be carried out in the future as the need arises although to much smaller extent.

_NB: This type of change in the archive only affects stream names: file headers only are modified_


## Background
A 2 character _location code_ is used to uniquely identify different data streams at a single station. These identifiers are commonly used to logically separate multiple instruments or sensor sets at a single station.

The International convention for miniseed format naming is available at [this link from the IRIS website](https://ds.iris.edu/ds/nodes/dmc/data/formats/seed/).  
The GeoNet seismic stations Location codes naming convention is documented in [the GeoNet website](https://www.geonet.org.nz/data/supplementary/channels) with further details provided on the [GeoNet metadata repository](https://github.com/GeoNet/delta/blob/main/docs/SEISMIC_SITE_NAMING_CONVENTIONS.md).

Based on these nomenclature conventions:
- All GeoNet strong motion sensors have a location code `2?`
- When a GeoNet station sensor is moved more than 1 m (but less than 200m), its location code will change accordingly (e.g. from `20` to `21`)

For GeoNet seismic sensors, this convention was finalized and documented in September 2019.

### Change description
After the convention was confirmed, we conducted an audit on all equipment changes across the GeoNet National Strong motion sensor network. 
We found that a number of SM sensors were moved to a new location at the time without having their location code changed accordingly.

Between June and October 2021 we have retroactively corrected our data archive and our metadata records, so that this change is properly represented.
For 27 SM stations, location codes that were previously recorded as `20` are now being changed to `21`.

Due to the complexity of this work, there has been sometimes and  for a limited period of time a mismatch between the metadata (that were correctly reporting 21) and the data in the archive. This has now been fixed.


### Affected data

Data and metadata that are affected by this change are:
- strong motion metadata (distributed via delta, FDSN)
- strong motion miniseed data (distributed via FDSN)
- strong motion processed data (distributed via the Strong Motion Tool and archive)
- seismic derived data: picks ID and magnitude ID (distributed via FDSN) might have metadata not correctly associated

If you use strong motion miniseed data and metadata, you might be impacted by this change. The impact we expect can be of two forms: 1) mismatch between your local copy of GeoNet data and metadata in comparison with our updated archive and metadata; or 2) mismatch in the metadata used in derived GeoNet seismic data products.  

In case you have a local copy, the following Impacts are expected:
- if you used and downloaded data between 2019 and 2021, you might not be able to retrieve the exact same dataset from the Geonet FDSN data service
 as it has been queried at that time;
- if you have a local copy of our data, some strong motion stream naming may now differ with our GeoNet archive;
- if you have a pre-October 2021 upload of Geonet station metadata into a database or a software querying dataset from 2011 to 2020.

In case you are querying GeoNet derived seismic data products (for example, earthquake products), a number of derived seismic data products were processed before June-October 2021, and have not been updated or reprocessed after the location code was corrected in the miniseed raw data and associated metadata. Those products might still refer to the old location code (namely `20`). For example, some events xml files (quakeML) or earthquake bulletins  might still have the former strong motion station streams naming with location code 20, although these streams do have a location code 21 from October 2021. 


## Details of the change
Here, we endeavour to provide enough details so that you can have a quick overview of the changes, and decide if those are affecting you. 
If you need further details or help please [contact us](https://www.geonet.org.nz/contact) or open an issue in this repository.

The table below provides a list of station and location codes that are affected, and for which time period data and/or metadata were corrected.
For data in the past, we tried to apply the change to data and metadata at the same time to minimise impact on the user while still allowing access to the waveforms. 

Listed below, only the stations for which a significant time range were changed. Change related to temporary configuration issues (few days) are not reported here.

All data and metadata listed below have had their location code changed from `20` to `21`. 
The strong motion channels that are affected are HN(200Hz), BN(50Hz) and occasional LN(1Hz).  

The table shows: 
- _Station_ identifier
- _Channels_ affected
- time range for which data have been corrected (_start_ and _end_, `year.doy`), UTC time 
- time _when_ change was applied, NZ time
- a _Note_ if other changes were also applied for the same time period

Station | Channels | Start | End | When | Note
--|--|--|--|--|--
DSZ | HN BN | 2016/314 | 2019/318 | 11 June 2021 | 
HAZ | HN BN | 2018/011 | 2019/305 | 15 Oct 2021 |
JCZ| HN BN | 2018/331 | 2020/015 | 18 Oct 2021 |
LBZ| HN BN | 2014/275 | 2020/014| 19 Oct 2021 |
LTZ | HN BN | 2013/296 | 2019/304 | 14 Oct 2021 |  
MLZ | HN BN | 2014/084 | 2019/304 | 31 Aug 2021 |[components name change](component-names.md) 
MQZ | HN BN | 2016/055 | 2019/305 | 18 Oct 2021 |
MRZ | HN BN | 2011/103 | 2019/304 | 15 Oct 2021 |
MWZ | HN BN | 2011/231 | 2019/304 | 2 Sep 2021 |  
MXZ | HN BN | 2011/230 | 2019/305 | 15 Oct 2021 |
MXZ | HN BN | 2011/230 | 2019/305 | 15 Oct 2021 |
NNZ| HN BN | 2012/005 | 2019/304 | 15 Oct 2021 | 
ODZ| HN BN | 2017/179 | 2019/305 | 18 Oct 2021 |
OPZ | HN BN | 2017/177 | 2019/304 | 23 June 2021 | 
OUZ| HN BN | 2017/053| 2019/305 | 17 Oct 2021 |
OXZ| HN BN | 2014/303 | 2020/015| 20 Oct 2021 |
PUZ | HN BN | 2013/218 | 2019/325 | 18 Oct 2021 |
QRZ | HN BN | 2015/315 | 2019/325 | 19 Oct 2021 |
THZ| HN BN | 2014/093 | 2020/014| 19 Oct 2021 |
TLZ| HN BN | 2016/043 | 2020/015| 18 Oct 2021 |
TOZ| HN BN | 2016/014 | 2019/325 | 18 Oct 2021 |
TSZ | HN BN | 2013/183 | 2019/325 | 18 Oct 2021 |
TUZ| HN BN | 2015/300 | 2020/014| 19 Oct 2021 |
VRZ| HN BN | 2014/078 | 2020/014| 20 Oct 2021 |[components name change](component-names.md)
WCZ| HN BN | 2017/053 | 2020/015| 20 Oct 2021 |
WHZ| HN BN | 2014/2156 | 2020/014| 21 Oct 2021 |
WVZ| HN BN | 2011/286 | 2020/015| 20 Oct 2021 |


