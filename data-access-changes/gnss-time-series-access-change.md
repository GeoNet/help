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
- key is `days` to specify the number of days of data requested, and value is `30`.

### Tilde Data Query

Refer to the [Tilde API](https://tilde.geonet.org.nz/v4/api-docs/endpoint/data) for more details.

The equivalent query is

`https://tilde.geonet.org.nz/v4/data/gnss/WGTN/displacement/-/1d/east/latest/30d`.

The Tilde API uses positional values, meaning the order of the values is critical and there are no explicit keys. The values must be in the following order:

- `gnss` to specify the data `Domain`, which is an overall description of the type of observations that have been recorded.
- `WGTN` to specify the `Station`, which is the data collection location
- `displaement` to specify the `Name`, a general name for the observation.
- `-` to specify the `Sensor Code`, there is no need to distinguish different measurement points, and all stations have a `nil` sensor code.
- `1d` to specify the `Method` which describe the time resolution of the data
- `east` to specify `Aspect`, which specifies a component or characteristic of the observation, such as directional components like `east`, `north`, `up` for displacement.
- `latest/30d` to specify the date range of data requested, in this case, the latest 30 days.

### Changes

As well as the API differences, the move to Tilde has been accompanined by a number of changes to how the data are described. This is intended to provide more consistency, understanding, and readability in constructing data queries.

> Please be advised that with the transition from the FITS service to Tilde, a significant change has been implemented regarding displacement units for GNSS time series data.
>
> Displacement units are now reported in **meters (m)** within the Tilde service. Previously, in the FITS service, displacement units were reported in **millimeters (mm)**.
>
> Please adjust your data processing and analysis workflows accordingly


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