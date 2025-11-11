# data.geonet.org.nz

> [!IMPORTANT]
> This is a planned change, not implemented yet. We recommend users to read carefully and implement the recommended change as soon as possible to ensure a smooth transition once service will be upgraded.

## data.geonet.org.nz transition
The GeoNet data service at https://data.geonet.org.nz is undergoing a significant upgrade.
This change will affect how clients access and interact with the API. 
Users will need to make sure their application will continue to work during the service migration.

### What is changing
The new version of data.geonet.org.nz will introduced the following features:

#### HTTPs Redirects
> [!WARNING]
> users are recommended to check their application and implement this change as soon as possible if required. This change shall be implemented BEFORE the data.geonet.org.nz service is migrated.

Clients downloading data must update their code to follow HTTPs redirects. 
Most clients will follow redirects by default. `curl` clients will need to add a `-L` or `--location` flag in their command.
We recommend to apply this change as soon as possible, it will work with the current and new data API service.



#### New URL pattern
The new service introduces a new URL structure, to allow future implementations of a data API.

The new structure introduce `/v1/data/`, for example:
```
https://data.geonet.org.nz/_pathtofile_
```
will become
```
https://data.geonet.org.nz/v1/data/_pathtofile_
```


The following HTTPs status codes are introduced:
- status code 301: moved permanently
- status code 302: follow redirect

#### Backward compatible API
The current API (https://data.geonet.org.nz/_pathtofile_) will remain available for a limited time after the switchover. It will support redirects (`-L` flag) but will be deprecated in 2026.


#### Rate limiting
We will implement rate limiting measures in the new service. These are introduced to ensure consistent service availability, prevent service degradation caused by individual users, and enable the GeoNet programme to control costs of delivering the data.geonet.org.nz service.

The main change is the implementation of a new Error Handling response for those clients exceeding a rate limit. This limit is calculated considering concurrent requests per minute per IP address.

Clients exceeding the rate limiting will receive an HTTP `429` response error (too many requests). 

To avoid triggering those rate limits, we recommend to modify your code so that:

- it can detect 429 HTTP response errors;
- if such error is detected, a short delay between bulk queries is introduced;
- if such error is detected, a retry logic with exponential backoff is introduced.


#### API documentation
An entry page and API documentation will be added.
