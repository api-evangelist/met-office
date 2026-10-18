---
name: site-specific-forecast
description: Get a Met Office Weather DataHub site-specific (point) forecast for a latitude/longitude at hourly, three-hourly or daily resolution.
api: Met Office Site Specific Forecast API
spec: openapi/met-office-site-specific-openapi.yml
operations:
  - getForecastForPointUsingGET_1
generated: '2026-10-18'
method: generated
---
# Site-specific point forecast

Base URL: `https://data.hub.api.metoffice.gov.uk/sitespecific/v0`. Authenticate every request with your Weather DataHub subscription key in the `apikey` header.

1. Pick the resolution. The contract reuses the operationId `getForecastForPointUsingGET_1` on all three paths: `GET /point/hourly`, `GET /point/three-hourly`, `GET /point/daily`. Our overlay suggests unique ids for them: `getHourlyPointForecast`, `getThreeHourlyPointForecast` and `getDailyPointForecast`.
2. Send `latitude` and `longitude`. You can also send `includeLocationName`, `excludeParameterMetadata` and `dataSource`.
3. The service returns forecast data for the nearest matching site.

Rules: these are read-only GETs, so retrying them is safe. Each call uses up your subscription's call allowance, so cache responses until the next forecast update.
