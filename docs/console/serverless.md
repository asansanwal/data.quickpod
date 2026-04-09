# Serverless

Public route: [https://console.quickpod.io/serverless](https://console.quickpod.io/serverless)

## What serverless means in QuickPod

QuickPod serverless publishes a cluster service behind a managed invoke path so users can call it like an API.

## Current serverless endpoint fields

The current serverless experience includes:

* endpoint name
* slug
* hot service binding
* optional warm service binding
* auth mode
* auth token when token-based access is used
* request timeout
* base price per call
* price per 100ms
* active or inactive state
* request logs
* generated invoke URL and curl example

## Typical workflow

1. Create a cluster.
2. Define a cluster service that targets the workload port.
3. Open the Serverless area.
4. Create a serverless endpoint that points to the cluster service.
5. Share or integrate against the invoke URL.

## Why serverless is useful

Serverless is useful when you want a stable HTTP entry point for an inference backend, tool endpoint, or service workload without sharing raw pod coordinates.

## Related routes

* Public serverless landing page: [https://console.quickpod.io/serverless](https://console.quickpod.io/serverless)
* Serverless create route after login: `/serverless/create`
* Cluster management: `/clusters`

## API note

QuickPod serverless invoke paths are public product APIs, not just internal console implementation details. They deserve separate API documentation if you are building external integrations.