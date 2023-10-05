# FITS to Tilde Changes

With the move from FITS as the access point for GeoNet's low rate data to Tilde, all of the URLs that previously
allowed users to retrieve data won't work, and a different URL will be required.

The purpose of this document is to explain and give examples of how a FITS URL can be converted to Tilde. This is
of particular relevance to users who use computer code to retrieve data, or who may have bookmarked a number of
FITS data queries. It includes only manually collected data (having the Tilde `Domain` of `manualcollect`). This 
is currently restricted to a sub-set of data collected for volcano monitoring purposes.

## FITS Data (Observation) Query

Refer to the [FITS API](https://fits.geonet.org.nz/api-docs/endpoint/observation) for more details.

A basic data (called observation in FITS) query might be

`https://fits.geonet.org.nz/observation?siteID=RU000&typeID=CO2-flux-a&methodID=cont&days=30`.

The FITS API uses key and value pairs that can be in any order:
- key is `siteID` to specify the data collection location, and value is `RU000`
- key is `typeID` to specify the type of data, and value is `CO2-flux-a`
- key is `methodID` to specify the method of data collecton, and value is `cont`.
- key is `days` to specify the number of days of data requested, and value is `30`.

## Tilde Data Query

Refer to the [Tilde API](https://tilde.geonet.org.nz/v3/api-docs/endpoint/data) for more details.

The equivalent query is

`https://tilde.geonet.org.nz/v3/data/manualcollect/RU000/plume-CO2-gasflux/MC01/contouring/-/latest/30d`.

The Tilde API uses values without any key, and the values must be in a specific order:
- `manualcollect` to specify the data `Domain`, which is the broad data collection method or data discipline
- `RU000` to specify the `Station`, which is the data collection location
- `plume-CO2-gasflux` to specify the `Name` of the data
- `MC01` to specify the `Sensor Code`, which is given to different sensors at a location, or slightly different measurement or sampling points where data are collected manually
- `contouring` to specify the `Method` of data collecton
- `-` to specify `Aspect`, which is a particular part or feature of a station or location. It is not used in this example so is set to `-`.
- `latest/30d` to specify the date range of data requested, in this case, the latest 30 days.

## Changes

As well as the API differences, the move to Tilde has been accompanined by a number of changes to how the data are described. This is intended to provide more consistency, understanding, and readability in constructing data queries.
For the earlier example:
- FITS `siteID` and Tilde `Station` are both `RU000`. In most cases they will be the same
- FITS `typeID` is `CO2-flux-a`, while the equivalent Tilde `Name` is `plume-CO2-gasflux`
- FITS `methodID` is `cont`, while the equivalent Tilde `Method` is `contouring`

FITS does not have Tilde's `Domain`, `Sensor Code` or `Aspect`. In the query example:
- `Domain` is `manualcollect`, indicating manually collected data
- `Sensor Code` is `MC01`. All stations have `MC01` as a `Sensor Code`. Some have additional codes if there are 
nearby sample or data collection points that are logically grouped under the same `Station`
- `Aspect` in this example is `-`, which means not used. `Aspect` is most commonly used when describing data collected
by a single sensor at multiple nearby points, e.g. at different depths. It is not commmonly used with `manualcollect`
data.

The accompanying PDF file contains a table with a recored for all possible FITS data query parameters and the
parameters of the corresponding Tilde data query. Table rows are ordered alphabetically by Tilde `Station` code.
The Place Name column is that displayed by the [Tilde Data Discovery GUI[(https://tilde.geonet.org.nz/ui/data-exploration#/).
The table does not contain all manually collected data in Tilde. If a data set was never in FITS, it is not listed in this
table. Furthermore, the table does not list data sets from other data domains that may have been available
through FITS.

Not list every possible constituent from laboratory analysis is listed for FITS `typeID` and Tilde `Name`,
which are equivalent descriptors, as the list is too long. If you see the word `constituent` in FITS `typeID` or Tilde `Name`,
then it is a placeholder for all of the possible constituents available from laboratory analyses.
For a FITS `methodID` of `lab` and its Tilde `Method` equivalent `water-analysis-lab`, `constituent` can mean
`Al`, `As`, `Br`, `Ca`, `Cl`, `Cs`, `d18O`, `d2H`, `Fe`, `F`, `H2S`, `HCO3`, `K`, `Li`, `Mg`, `Na`, `NH3`,
`NO3-N`, `PO4-P`, `Rb`, `SiO2`, `SO4`. Not all constituents are analysed for manually collected data from every locality.
