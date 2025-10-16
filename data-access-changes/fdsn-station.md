# FDSN Station webservice

## Migration to StationXML 1.2 (October 2025)
GeoNet's FDSN archive (`service.geonet.org.nz`) and near real-time (`service-nrt.geonet.org.nz`) webservices are migrated to the latest version of the [FDSN StationXML](https://www.fdsn.org/xml/station/) schema, version 1.2.

The FDSNWS impacted endpoint is:
- `station` (station metadata)

This change updates the `station` webservice from StationXML version 1.0 to 1.2. For a detailed list of schema changes, please refer to the FDSN's [StationXML official changelog](https://docs.fdsn.org/projects/stationxml/en/latest/overview.html#changes-from-version-1-1-to-1-2-2022-2-25).

Key changes in the StationXML 1.2:
- Dates and times should be W3C/ISO 8601 and should always include a timezone of ‘Z’ to indicate UTC;
- Use SI symbols for unit name, like m/s, along with singular lowercase “count” for digital counts;
- Add <WaterLevel> within <Station> and <Channel>
- For low pass FIR filters, use gain at zero frequency (sum of coefficients)
- Gain-only analog Stages should use PolesZeros with no poles or zeros
- Gain-only digital Stages should use FIR with a single numerator of value 1

## What you need to do
We recommend users to review the official FDSN documentation and assess any potential impact on their systems or workflows.

Any existing code that works with 1.1 should work with 1.2 without modification.




