# Search & Launch

QuickPod's public search pages are the main entry point for renting compute.

Direct links:

* [GPU Search](https://console.quickpod.io/)
* [CPU Search](https://console.quickpod.io/cpu-pod-search)
* [GPU Catalog](https://console.quickpod.io/gpu-types)

## What the search pages do

The search console lists currently rentable offers from QuickPod hosts. Each offer represents a rentable slice of compute capacity with its own price, hardware details, duration rules, and port range.

## Current filter categories

The current search experience includes filters and sorting for:

* GPU or CPU search mode
* hardware count
* hardware type
* sort order
* max duration
* max hourly cost
* minimum VRAM where relevant
* region selection
* occupied offers visibility
* privileged-only visibility

These filters are persisted in the browser so the console can restore your last-used search preferences.

## Template-aware launch flow

Search and launch is closely tied to templates.

Before creating a pod, select a matching template for the workload you want to run. The selected template influences image path, launch mode, exposed routes, and user experience after the pod starts.

Use [Templates](https://console.quickpod.io/templates) to browse available templates before launching.

## Typical workflow

1. Open GPU Search or CPU Search.
2. Filter to the hardware profile, cost, and location you want.
3. Pick a template that matches your workload.
4. Set storage size and any runtime-specific options.
5. Create the pod.
6. Open the authenticated Pods page to monitor readiness and connect.

## Related public pages

* [Templates](https://console.quickpod.io/templates)
* [GPU Catalog](https://console.quickpod.io/gpu-types)
* [Host Stores](https://console.quickpod.io/host-stores)

## Notes

If you are comparing a GPU family before renting, start from the public GPU catalog. If you already know the hardware family, the search pages are the fastest way to filter to live rentable offers.