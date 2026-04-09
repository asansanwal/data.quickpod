# Clusters

Public route: [https://console.quickpod.io/clusters](https://console.quickpod.io/clusters)

## What clusters are

QuickPod clusters let you run multiple replicas of a workload under one logical deployment instead of managing each pod separately.

## Current cluster concepts

The current cluster surface includes:

* cluster creation from templates
* replica management
* start and stop controls
* rolling redeploy behavior
* scale workflows
* replica health visibility
* cluster storage modes
* cluster services and connect behavior

## Storage modes

Clusters can be configured with no cluster volume, shared storage, or sharded storage depending on how the workload should persist data.

## Why use clusters

Clusters are useful when you want a repeatable deployment model for:

* multi-replica inference or API backends
* services you want to expose through a stable service layer
* workloads that need shared or predictable storage behavior across replicas

## Related public and authenticated routes

* Public cluster landing page: [https://console.quickpod.io/clusters](https://console.quickpod.io/clusters)
* Cluster detail after login: `/clusters/:id`
* Serverless publishing on top of cluster services: `/serverless`

## Notes

QuickPod's cluster features are implemented in QuickPod's own control plane and routing model. They should be understood in QuickPod terms rather than generic Kubernetes terminology.