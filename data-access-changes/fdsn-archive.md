# FDSN Archive webservice Access Changes

## Change on frontend service (September 2025)
All endpoints of the GeoNet FDSN archive service (`service.geonet.org.nz` or the "GEONET" shortcut if using obspy) are migrated to a new frontend in September 2025. 

The FDSNWS impacted endpoints are:
- `dataselect` (waveform data)
- `event` (earthquake catalogue data)
- `station` (station metadata)

This migration will change the FDSN archive service by implementing rate limiting measures. These are introduced to ensure consistent service availability, prevent service degradation caused by individual users, and enable the GeoNet programme to control costs of delivering the FDSN service.

The main change is the implementation of a new Error Handling response for those clients exceeding a rate limit. This limit is calculated considering concurrent requests per minute per IP address.

Clients exceeding these thresholds will receive an `HTTP 429` (_Too Many Requests_) response error. 

To avoid triggering those rate limits, we recommend to modify your code so that:
1. it can detect `429` HTTP response errors;
2. if such error is detected, a short delay between bulk queries is introduced;
3. if such error is detected, a retry logic with exponential backoff is introduced.


