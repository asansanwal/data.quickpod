# Pods

Authenticated route: `/pods`

Public entry points that lead into pod creation:

* [GPU Search](https://console.quickpod.io/)
* [CPU Search](https://console.quickpod.io/cpu-pod-search)
* [Templates](https://console.quickpod.io/templates)

## What the Pods page does

The Pods page is the authenticated control center for workloads after they are launched.

## Current pod management capabilities

The current console surface includes:

* GPU and CPU pod views
* cached pod list updates
* running spend summary
* stopped-storage spend summary
* connect and logs workflows
* start, stop, restart, and destroy actions
* state-aware readiness and lifecycle visibility

## Cost visibility

The current pod page distinguishes between:

* running spend per hour for active pods
* storage spend per hour for stopped pods that still exist

This distinction matters because stopping a pod does not remove storage cost.

## Typical workflow

1. Launch from search.
2. Open Pods after creation.
3. Wait for the workload to become ready.
4. Connect, monitor, or inspect logs.
5. Stop when temporarily finished, or destroy when the workload and disk are no longer needed.

## Related docs

* [Search & Launch](search-and-launch.md)
* [Templates](templates.md)
* [Storage & Cloud Sync](storage-and-cloud-sync.md)