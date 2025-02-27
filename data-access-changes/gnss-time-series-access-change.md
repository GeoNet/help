# GNSS Time Series Access Changes

## FITS to Tilde

GeoNet's GNSS time series data access has been migrated from FITS to the Tilde platform. Consequently, previously used FITS URLs for data retrieval are now invalid. This document outlines the process for converting FITS URLs to the corresponding Tilde URLs. It includes practical examples and is intended for users who utilize automated data retrieval scripts or have existing FITS URL bookmarks. This guide specifically addresses GNSS time series data (Tilde Domain: `gnss`)

### FITS Data (Observation) Query

Refer to the [FITS API](https://fits.geonet.org.nz/api-docs/endpoint/observation) for more details.

A basic data (called observation in FITS) query might be

`https://fits.geonet.org.nz/observation?siteID=WGTN&typeID=e&days=30`.

The FITS API uses key and value pairs that can be in any order:
- key is `siteID` to specify the data collection location, and value is `WGTN`
- key is `typeID` to specify the type of data, and value could be  `e`, `n` or `u`
- key is `days` (optional) to specify the number of days of data requested, and value is `30`.

#### Retrieving All Available Data

The FITS service allows to retrieve all available data for a specific station without defining a time range.
Using the following query:

`https://fits.geonet.org.nz/observation?siteID=WGTN&typeID=e`

**Important**: This "retrieve all data" functionality is not available in the Tilde service. You must specify a time window when using the Tilde API.

### Tilde Data Query

Refer to the [Tilde API](https://tilde.geonet.org.nz/v4/api-docs/endpoint/data) for more details.

The equivalent query is

`https://tilde.geonet.org.nz/v4/data/gnss/WGTN/displacement/-/1d/east/latest/30d`.

The Tilde API uses positional values, meaning the order of the values is critical and there are no explicit keys. The values must be in the following order:

- `gnss` to specify the data `Domain`, which is an overall description of the type of observations that have been recorded.
- `WGTN` to specify the `Station`, which is the data collection location
- `displacement` to specify the `Name`, a general name for the observation.
- `-` to specify the `Sensor Code`, there is no need to distinguish different measurement points, and all stations have a `nil` sensor code.
- `1d` to specify the `Method` which describe the time resolution of the data
- `east` to specify `Aspect`, which specifies a component or characteristic of the observation, such as directional components like `east`, `north`, `up` for displacement.
- `latest/30d` to specify the date range of data requested, in this case, the latest 30 days.

#### Retrieving Data for a Specific Time Range

To get data within a specific time period using the Tilde API, the start and end dates must be explicitly defined.
This is done by including the date range in the URL. Example query:

`https://tilde.geonet.org.nz/v4/data/gnss/WGTN/displacement/-/1d/east/2000-01-01/2025-02-25`

In this example, `2000-01-01/2025-02-25` specifies the time window, with `2000-01-01` as the start date and `2025-02-25` as the end date.

#### Finding the Available Data Time Range

To determine the earliest and latest available data dates for a particular dataset, use the `dataSummary` endpoint.
This endpoint returns the `earliestRecord` and `latestRecord` values. Example query::

`https://tilde.geonet.org.nz/v4/dataSummary/gnss?station=WGTN&name=displacement&method=1d&aspect=east`

### Changes

As well as the API differences, the move to Tilde has been accompanined by a number of changes to how the data are described. This is intended to provide more consistency, understanding, and readability in constructing data queries.

#### Query Output Format Change
>Please take note of a significant change in the query output format with the transition from the FITS service to Tilde. FITS queries returned data in CSV format while Tilde queries now return data in JSON format.
>This change requires users to adjust their data processing scripts and applications to accommodate the new JSON output. 
>
>We understand this may require adjustments to existing workflows, and we are committed to providing resources to ease this transition.
>For detailed guidance on working with JSON data from Tilde, please refer to our comprehensive data tutorials available here: https://github.com/GeoNet/data-tutorials/tree/main/Tilde. These tutorials cover various aspects of querying and processing Tilde data, including parsing the JSON output.
>
>We encourage you to review these tutorials and update your code accordingly

#### Displacement Units Update in Tilde Service
> Please be advised that with the transition from the FITS service to Tilde, a significant change has been implemented regarding displacement units for GNSS time series data.
>
> Displacement units are now reported in **meters (m)** within the Tilde service. Previously, in the FITS service, displacement units were reported in **millimeters (mm)**.
>
> Please adjust your data processing and analysis workflows accordingly

#### FITS-Tilde parameters mappings
For the earlier example:
- FITS `siteID` and Tilde `Station` are both `WGTN` and they will be the same.
- FITS `typeID` is `e`, while the equivalent Tilde `Aspect` is `east`.

FITS does not have Tilde's `Domain`, `Name`, `Sensor Code` or `Method`. In the query example:
- `Domain` is `gnss`, indicating derived GNSS time series.
- `Name` is `displacement`, to specify exactly type of derived GNSS time series. 
- `Sensor Code` is not aplicable to the `gnss` data domain.
- `Method` is `1d` to specify GNSS time series sampling rate.


The accompanying table contains mappings for all possible FITS data query parameters and the parameters of the corresponding Tilde data query to retrieve GNSS time series data.

| Query output                |  FITS  |        |   |  Tilde |         |              |            |        |        |
|-----------------------|:------:|:------:|:-:|:------:|:-------:|:------------:|:----------:|:------:|:------:|
|                       | siteID | typeID |   | Domain | Station |     Name     | SensorCode | Method | Aspect |
| East displacements of WGTN station   |  WGTN  |    e   |   |  gnss  |   WGTN  | displacement |      -     |   1d   |  east  |
| North displacement of WGTN station    |  WGTN  |    n   |   |  gnss  |   WGTN  | displacement |      -     |   1d   |  north |
| Vertical displacement of WGTN station |  WGTN  |    u   |   |  gnss  |   WGTN  | displacement |      -     |   1d   |   up   |