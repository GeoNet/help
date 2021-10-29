# Location codes change

This document provides details of **Data/Metadata Legacy corrections** we have applied to correctly label the **location code** of **strong motion instruments** part of the GeoNet national network for periods of time between **2011 and 2020**.
The change was applied to **data and metadata** from **27 seismic stations**  (in between June and October 2021) 

You might be impacted by this change if you:
- have a local copy of our data and/or metadata that is not up to date Prior to June/Oct 2021 ;
- are using our data and metadata services while we applied the change Prior up to Oct 2021;
- are using a derived data product that may present a mismatch with the metadata (e.g. seismic pick label on a strong motion)

## Location code definition
Location ID: **A 2 character code used to uniquely identify different data streams at a single station.** These IDs are commonly used to logically separate multiple instruments or sensor sets at a single station.

## Background
- The Miniseedformat naming international conventions are available at (https://ds.iris.edu/ds/nodes/dmc/data/formats/seed/)  
- The GeoNet seismic stations Location codes naming conventions are documented on "https://www.geonet.org.nz/data/supplementary/channels".

    [More details about GeoNet location codes](https://github.com/GeoNet/delta/blob/main/docs/SEISMIC_SITE_NAMING_CONVENTIONS.md)

For GeoNet seismic sensors, a convention was finalized and documented in September 2019.

Based on these nomenclature conventions:
- **All GeoNet strong motion sensors have a location code `2?`**
- **When a GeoNet station sensor is moved more than 1 m (but less than 200m), its location code will change accordingly (e.g. from `20` to `21`)**

### Change description
After the convention was confirmed, we conducted an audit on all equipment changes across the GeoNet National Strong motion sensor network. 
We found that a number of SM sensors were moved to a new location at the time without having their location code changed accordingly.

We are now (2021) retroactively correcting our data archive and our metadata records, so that this change is properly represented.
For those SM stations, location codes that were previously recorded as `20` are now being changed to `21`.

Due to the complexity of this work, there has been sometimes and  for a limited period of time a mismatch between the metadata (that were correctly reporting 21) and the data in the archive. 
This has now been fixed.

### Affected data

Data and metadata that are affected by this change are:
- strong motion metadata (distributed via delta, FDSN)
- strong motion miniseed data (distributed via FDSN)
- strong motion processed data (distributed via the Strong Motion Tool and archive)
- seismic derived data: picks ID and magnitude ID (distributed via FDSN) might have metadata not correctly associated

If you use strong motion miniseed data and metadata, you might be impacted by this change. The impact we expect can be of two forms:
- if you used and downloaded data between 2019 and 2021, you might not be able to retrieve the exact same dataset from the Geonet FDSN data service
 as it has been queried at that time
- if you have a local copy of our data, some strong motion stream naming will differ with our GeoNet archive
- if you have a pre-October 2021 upload of Geonet station metadata into a database or a software querying dataset from 2011 to 2020
- If you are querying GeoNet derived earthquake products: Some are not updated/reprocessed accordingly and will refer to old location code (namely `20`).
For example, some events xml files (quakeML) or earthquake bulletins  might still have the forner strong motion station streams naming with location code 20, 
although these streams do have a location code 21 from October 2021. 


## Details of the change
Here, we endeavour to provide enough details so that you can have a quick overview of the changes, and decide if those are affecting you. 
If you need further details or help please [contact us](https://www.geonet.org.nz/contact) or open an issue in this repository.

The table below provides a list of station and location codes that are affected, and for which time period data and/or metadata were corrected.
For data in the past, we tried to apply the change to data and metadata at the same time to minimise impact on the user while still allowing access to the waveforms. 

Listed below, only the stations for which a significant time range were changed. 
Change related to temporary configuration issues (few days) as opposed to stream naming policy change are not reported here: No impacts or no significant ones.

All data and metadata listed below have had their location code changed from `20` to `21` 
Strong motion channels affected are **HN(200Hz), BN(50Hz) and occasional LN(1Hz)** 

The table shows: 
- _Station_ identifier
- _Channels_ affected
- time range for which data have been corrected (_start_ and _end_, `year.doy`) 
- time _when_ change was applied
- a _Note_ if other changes were also applied for the same time period

Station | Channels | Start | End | When | Note
--|--|--|--|--|--
DSZ | HN BN |	2016/314 | 2019/318 | _11th June 2021 (162)_ | 
OPZ | HN BN |	2017/177 | 2019/304 | _23th June 2021 (174)_ | 
MLZ | HN BN |2014/084 | 2019/304 | _31st Aug 2021 (212)_ |[components name change](component-names.md) 
MWZ | HN BN |2011/231 | 2019/304 | _02nd Sep 2021 (245)_ |  
LTZ | HN BN | 2013/296 | 2019/304 | _14th Oct 2021 (257)_ |  
NNZ| HN BN | 2012/005 | 2019/304 | _15th Oct 2021 (258)_ | 
MRZ | HN BN | 2011/103 | 2019/304 | _15th Oct 2021 (257)_ |
MXZ | HN BN | 2011/230 | 2019/305 | _15th Oct 2021 (257)_ |
HAZ | HN BN | 2018/011 | 2019/305 | _15th Oct 2021 (257)_ |
MXZ | HN BN | 2011/230 | 2019/305 | _15th Oct 2021 (257)_ |
MQZ | HN BN | 2016/055 | 2019/305 | _18th Oct 2021 (260)_ |
OUZ| HN BN | 2017/053| 2019/305 | _17th Oct 2021 (259)_ |
ODZ| HN BN | 2017/179 | 2019/305 | _18th Oct 2021 (260)_ |
PUZ | HN BN | 2013/218 | 2019/325 | _18th Oct 2021 (260)_ |
QRZ | HN BN | 2015/315 | 2019/325 | _19th Oct 2021 (261)_ |
TOZ| HN BN | 2016/014 | 2019/325 | _18th Oct 2021 (260)_ |
TSZ | HN BN | 2013/183 | 2019/325 | _18th Oct 2021 (260)_ |
JCZ| HN BN | 2018/331 | 2020/015 | _18th Oct 2021 (260)_ |
TLZ| HN BN | 2016/043 | 2020/015| _18th Oct 2021 (260)_ |
THZ| HN BN | 2014/093 | 2020/014| _19th Oct 2021 (261)_ |
LBZ| HN BN | 2014/275 | 2020/014| _19th Oct 2021 (261)_ |
TUZ| HN BN | 2015/300 | 2020/014| _19th Oct 2021 (261)_ |
VRZ| HN BN | 2014/078 | 2020/014| _20th Oct 2021 (262)_ |[components name change](component-names.md)
OXZ| HN BN | 2014/303 | 2020/015| _20th Oct 2021 (262)_ |
WCZ| HN BN | 2017/053 | 2020/015| _20th Oct 2021 (262)_ |
WVZ| HN BN | 2011/286 | 2020/015| _20th Oct 2021 (262)_ |
WHZ| HN BN | 2014/2156 | 2020/014| _21th Oct 2021 (263)_ |

