# Storage & Cloud Sync

Authenticated route: `/storage`

Public route for the console page itself: [https://console.quickpod.io/storage](https://console.quickpod.io/storage)

## What storage covers

QuickPod storage is no longer just the pod disk size slider during launch. The current product includes persistent volumes and cloud sync workflows.

## Current storage areas

### Volumes

Create and manage persistent volumes that can survive independently from an individual pod lifecycle.

### Cloud Sync

Cloud Sync lets you move data between a QuickPod volume and supported cloud storage providers.

Current provider coverage in the console includes:

* Amazon S3
* Backblaze B2
* Dropbox
* Google Drive

## Current cloud sync capabilities

The cloud sync surface supports:

* push and pull direction control
* provider-specific remote settings
* reusable credentials through secrets
* manual sync jobs
* scheduled sync jobs
* schedule timezone and cadence settings
* job history and sync target management

## When to use storage features

Use a volume when you want persistence independent of a single pod.

Use cloud sync when you need to move data between QuickPod and a storage provider you already use.

## Related routes

* Authenticated storage management: `/storage`
* Authenticated secrets management: `/secrets`
* Public console page: [https://console.quickpod.io/storage](https://console.quickpod.io/storage)

## Practical guidance

If the workload is disposable, pod-local storage may be enough.

If the workload needs repeatable datasets, backups, or shared persistence across launches, use volumes and cloud sync instead of leaving stopped pods around only for their disks.