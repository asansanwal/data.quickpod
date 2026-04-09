# API Documentation

QuickPod exposes both public read-oriented APIs and authenticated update APIs.

## Swagger references

* Read-only and public API: [https://api.quickpod.org/swagger/index.html](https://api.quickpod.org/swagger/index.html)
* Authenticated update API: [https://api.quickpod.org/update/swagger/index.html](https://api.quickpod.org/update/swagger/index.html)

## API categories

### Public discovery APIs

These routes back public console experiences such as:

* [GPU Search](https://console.quickpod.io/)
* [CPU Search](https://console.quickpod.io/cpu-pod-search)
* [Templates](https://console.quickpod.io/templates)
* [GPU Catalog](https://console.quickpod.io/gpu-types)
* [Host Stores](https://console.quickpod.io/host-stores)

Typical public API use cases include reading public templates, reading community templates, browsing rentable offers, reading GPU catalog data, and browsing host stores.

### Authenticated update APIs

Authenticated routes cover user and host workflows such as:

* pods
* templates
* clusters
* cluster services
* serverless endpoints
* storage volumes and sync targets
* account profile and billing
* notifications
* secure API keys
* secrets

## Secure API keys

QuickPod supports scoped secure API keys for automation. These are intended for integrations and scripts where you do not want to reuse an interactive session token.

Examples of supported scope patterns in the product include read and write scopes for pods, machines, templates, storage, account data, contracts, and host store management.

## Serverless invoke paths

QuickPod serverless endpoints are product-facing APIs built around invoke paths such as:

* `/update/serverless/<slug>`

These are configured from the authenticated serverless console and backed by cluster services.

## Guidance

Use the public API for discovery and browsing. Use the authenticated update API for actions that create, modify, or destroy user resources.

