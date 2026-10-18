---
name: severe-weather-warnings
description: Follow UK National Severe Weather Warning Service (NSWWS) warnings through the Atom feed and get each warning as GeoJSON.
api: Met Office NSWWS Warnings API
spec: openapi/met-office-nswws-warnings-openapi.yml
operations:
  - objectsFeed
  - objectsIssued
  - objectsUpdated
generated: '2026-10-18'
method: generated
---
# Severe weather warnings (NSWWS)

Base URL: `https://data.hub.api.metoffice.gov.uk/nswws/v1.1`. Send the `apikey` header on every call.

1. Poll `objectsFeed` (`GET /objects/feed`) to read the Atom feed of warning activity.
2. For each feed entry, take the warning `uuid`. Then call `objectsIssued` (`GET /objects/issued/{uuid}`) to get the latest warnings as a GeoJSON feature collection.
3. Call `objectsUpdated` (`GET /objects/updated/{uuid}`) to get a warning event that has been updated.

Rules: these are read-only GETs. Poll the feed instead of calling the object endpoints in a tight loop.
