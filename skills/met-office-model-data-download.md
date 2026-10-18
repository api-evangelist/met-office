---
name: model-data-download
description: List your Weather DataHub atmospheric-model orders, find the latest files for an order, and download the file data.
api: Met Office Atmospheric Model API
spec: openapi/met-office-atmospheric-models-openapi.yml
operations:
  - getOrders
  - getOrderLatest
  - getOrderLatestFileDetails
  - getOrderLatestFileData
  - getAllRuns
  - getModelRuns
generated: '2026-10-18'
method: generated
---
# Atmospheric model data download

Base URL: `https://data.hub.api.metoffice.gov.uk/atmospheric-models/1.0.0`. Send the `apikey` header on every call. The Map Images API (`map-images/1.0.0`) uses the same order flow and the same operationIds, except `getModelRuns`.

1. `getOrders` (`GET /orders`) lists the orders that your subscription can see. Orders are set up in the DataHub portal, not through this API.
2. You can check the available model runs with `getAllRuns` (`GET /runs`) or `getModelRuns` (`GET /runs/{modelId}`).
3. `getOrderLatest` (`GET /orders/{orderId}/latest`) lists the latest files for an order. You can narrow the list with `runfilter`.
4. `getOrderLatestFileDetails` (`GET /orders/{orderId}/latest/{fileId}`) returns the details of one file.
5. `getOrderLatestFileData` (`GET /orders/{orderId}/latest/{fileId}/data`) downloads the data. Set `Accept` to the format you want, as the contract describes.

Rules: all of these calls are read-only, so retrying is safe. Files are large, so download each file only once per run.
