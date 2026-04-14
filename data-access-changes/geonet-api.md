# GeoNet API (api.geonet.org.nz)

## GeoNet API Network Sensor changes (March 2026)

The GeoNet API endpoints that were providing information about the GeoNet sensor network have been reviewed and modified for improved usability. Theses changes mean that some end points will be deprecated, though not immediately.

Key changes:
- new `network/station?sensorType=[n]` endpoint created with the following improvements: 
  - additional sensor types can now be queried (e.g. cameras, environmental sensors, scandoas, geomagnetic sensors)
  - sensor types categories and associated numbering changed with similar sensor technologies are grouped together.
- extended  `network/sensors` endpoint including all sensor types.
- sensor details shall now be queried via `network/sensors?sensorType=[n]&station=[code]`
- deprecated entpoints:
  - `network/sensor?sensorType=[n]`
  - `network/gnss`
  - `network/fdsn`


### New `network/station` endpoint

Sensor types listing moved from `network/sensor?sensorType=[n]` to `network/station?sensorType=[n]`. The new endpoint has been reviewed to include additional types (and data domains). 
Please note that sensor type numbering and category are changed. 
The endpoint to query sensor type is https://api.geonet.org.nz/network/sensor/type.

Numbering and categories of new API version are:
```
1: Air pressure sensor
2: Broadband seismometer
3: Coastal sea level gauge
4: DART bottom pressure recorder
5: DOAS spectrometer
6: Environmental sensor
7: Geomagnetic sensor
8: GNSS/GPS
9: Lake level gauge
10: Manual collection
11: Short period seismometer
12: Strong motion sensor
13: Camera
```

> [!WARNING]  
> Deprecated numbering and categories of previous API version are:
> ```
> 1: Accelerometer
> 2: Barometer
> 3: Broadband Seismometer
> 4: GNSS Antenna
> 5: Hydrophone
> 6: Microphone
> 7: Pressure Sensor
> 8: Short Period Borehole Seismometer
> 9: Short Period Seismometer
> 10: Strong Motion Sensor
> ```


### Sensor details

To find the details of a sensor all types are now using the `network/sensors?sensorType[n]&station=[code]` endpoint.
Users will need to specify the sensorType and station code. The structure of the JSON response has also changed. 

Two examples are provided below. 

To retrieve JSON features with the detailed information for the GNSS station at Dunedin
[network/sensors?sensorType=8&station=DUND](https://api.geonet.org.nz/network/sensors?sensorType=8&station=DUND)

> [!WARNING]  
> The endpoint `/network/gnss/mark?code=DUND` is now deprecated

To retrieve JSON features with the detailed information at Quarts Range use:
- for the Short Period Seismometers [network/sensors?sensorType=11&station=QRZ](https://api.geonet.org.nz/network/sensors?sensorType=11&station=QRZ)
-for Broadband Seismometers [network/sensors?sensorType=2&station=QRZ](https://api.geonet.org.nz/network/sensors?sensorType=2&station=QRZ)
- for Strong motion sensors [network/sensors?sensorType=12&station=QRZ)](https://api.geonet.org.nz/network/sensors?sensorType=12&station=QRZ)

> [!WARNING]  
> The endpoint endpoint `network/fdsn/station?network=NZ&station=QRZ` is now deprecated


### Sensor search

To find sensors with a specific type use the new endpoint `network/station?sensorType=[n]` endpoint.
Users can also select a time range using `startDate` and/or `endDate`.

To find all GNSS stations in operation during 2025 use:
[network/station?sensorType=8&startDate=2025-01-01&endDate=2025-12-31](https://api.geonet.org.nz/network/station?sensorType=8&startDate=2025-01-01&endDate=2025-12-31)

To find all Siesmometers and strong motion sensors in operation since 2025 use:
[network/station?sensorType=2,11,12&startDate=2025-01-01](https://api.geonet.org.nz/network/station?sensorType=2,11,12&startDate=2025-01-01)

> [!WARNING]  
> The following endpoints are deprecated
> - `network/sensor?sensorType=4&startDate=2025-01-01&endDate=2025-12-31`
> - `network/sensor?sensorType=2,8,9&startDate=2025-01-01`
