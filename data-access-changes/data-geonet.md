# data.geonet.org.nz

> [!IMPORTANT]
> This change will be implemented on **17 March 2026**. We recommend users to read carefully and implement the recommended change as soon as possible to ensure a smooth transition once service is upgraded.

## data.geonet.org.nz transition
The GeoNet data service at https://data.geonet.org.nz is undergoing a significant upgrade.
This change will affect how clients access and interact with the API. 
Users need to make sure their application will continue to work during the service migration.

### What is changing
The new version of data.geonet.org.nz introduces the following features:

### New landing page
Those using https://data.geonet.org.nz with their browser, will notice a new look of the landing page. The first page will show the Application Programmatic Interface documentation, a list of available endpoints (and links to related API-documentation) and a banner used for notices of upcoming/recent changes. The old landing page is now available under one of the endpoints ( https://data.geonet.org.nz/v1/data ). 
No other noticeable changes have been implemented (besides the service being more responsive and browsing faster!).


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

A client can get a rate limiting error if it sends too many simultanous requests at the same time (for example, if it has too many parallel downloads, or too many consecutive attempts during a short period of time).

Clients exceeding the rate limiting will receive an HTTP `429` response error (too many requests). 

To avoid triggering those rate limits, we recommend to modify your code so that:

- it can detect 429 HTTP response errors;
- if such error is detected, a short delay between bulk queries is introduced;
- if such error is detected, a retry logic with exponential backoff is introduced.


#### API documentation
An entry page and API documentation is added.


### Change timeline overview

This graph shows an indicative timeline of GeoNet Data API changes and actions users are recommended to take.

![data-geonet](/data-access-changes/data-geonet.svg)


### Frequently asked questions

The list below point to issues encountered by our users while preparing for the migration

* [wget not correctly following redirect](https://github.com/GeoNet/help/issues/150)
